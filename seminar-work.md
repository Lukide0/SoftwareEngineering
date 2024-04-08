# Student information system - Subjects

System for managing subjects.

## Functional Requirements

This section specifies the functional requirements.

### User requirements

- As a teacher, I want to be able to send a request to create a subject so that new subjects can be created.
- As a teacher, I want to be able to set subject info because nobody else can it set.
- As a teacher I want to be able to activate a subject because it allows the subject to be available for enrollment, enabling students to register for the course.
- As a teacher, I want to be able to set co/pre-requisites because it ensures that students have the necessary foundation or concurrent knowledge required to succeed in the subject.
- As a teacher, I want to be able to set the teachers for a subject because it allows me to designate qualified instructors who can effectively deliver the subject material and provide guidance to students.
- As a teacher, I want to be able to submit a request to modify important information about the subject (instructor, credits, prerequisites, co-requisites, etc.) so that any necessary updates or changes can be accurately reflected in the system.
- As a teacher I want to be able to edit non-essential information about the subject (annotations, requirements for credit, literature, syllabus, etc.) without submitting a request, ensuring flexibility and efficiency in managing the subject details.

- As a SDO, I want to be able to activate/deactivate a subject because it enables me to control the availability of subjects within the curriculum, aligning with academic policies and ensuring efficient resource allocation.
- As a SDO, I want to be able to accept a subject creation request t because it allows me to review and approve proposals for new subjects, ensuring alignment with educational objectives and curricular standards.
- As a SDO, I want to be able to add a subject to a study programme because it enables me to incorporate approved subjects into the curriculum of specific study programs, ensuring that students have access to a structured and coherent course of study.
- As a SDO, I want to be able to edit subjects directly to correct mistakes and make edits efficiently, without relying on teachers to file requests for changes.

- As a student, I want to be able to view subject info because it provides me with essential details about subjects, such as course content, prerequisites, and instructors, helping me make informed decisions about my academic path and course selections.

### System requirements

#### Actors

##### Teacher

Faculty members responsible for initiating subject-related actions such as creating, modifying, and activating subjects, as well as assigning instructors and setting prerequisites.

##### SDO (Student department)

Administrative personnel tasked with managing subjects at a higher level, including activating/deactivating subjects, accepting subject creation requests, adding subjects to study programs, and editing subjects.

##### Student

Individuals who are enrolled in a study programme.

#### Use cases

##### Subject management

```plantuml
@startuml
left to right direction
actor Teacher as "Teacher"
actor SDO as "SDO"
actor Student as "Student"

rectangle "Subject Management" {
  usecase "Send request to create subject" as UC1
  usecase "Edit essential subject info" as UC2
  usecase "Activate subject" as UC3
  usecase "Set co/pre-requisites" as UC4
  usecase "Set teachers for subject" as UC5
  usecase "Send request to modify subject info" as UC6
  usecase "Edit non-essential subject info" as UC7
  usecase "Update subject info" as UC8
  usecase "Activate/deactivate subject" as UC9
  usecase "Accept subject creation request" as UC10
  usecase "Add subject to study programme" as UC11
  usecase "Edit subject" as UC12
  usecase "View subject info" as UC13
  usecase "Accept subject info modification request" as UC14


  SDO --> UC9
  SDO --> UC10
  SDO --> UC11
  SDO --> UC12
  SDO --> UC14

  Teacher --> UC1
  Teacher --> UC2
  Teacher --> UC3
  Teacher --> UC4
  Teacher --> UC5
  Teacher --> UC7

  Student --> UC13

  UC4 ..> UC6 : <<include>>
  UC2 ..> UC6 : <<include>>
  UC3 ..> UC6 : <<include>>
  UC5 ..> UC6 : <<include>>
  UC14 ..> UC8 : <<include>>
  UC12 ..> UC8 : <<include>>
  UC7 ..> UC8 : <<include>>
}
@enduml
```

The use case diagram depicts the subject management system, involving three main actors: Teachers, Student Department Officers (SDO), and Students.
The Teacher actor interacts with various use cases such as sending requests to create subjects, setting subject info, activating subjects, submitting requests to modify subject info, and editing non-essential subject info.
The SDO actor is responsible for tasks like activating/deactivating subjects, accepting subject creation requests, adding subjects to study programs, and editing subjects.
Students interact with the system to view subject info.

###### Send request to create subject
This use case describes a process, by which the teacher can send a request to the study department office for creation of a new subject.

**Actors**
- Teacher
- SDO

**Precondition**
The teachers has logged in into their SIS account and have opened the form for creating a new subject.

**Normal**
1. The teacher fills out the subject creation form by setting all of the required fields in the subject creation form (also by setting some optional fields).
2. The teacher submits the subject creation form.
3. SIS verifies if the field values of the submitted form are valid (possible number of credits, examination type, supported languages, etc.)
4. SIS stores the form and sends the SDO a notification in regards to the new subject creation form
5. SIS notifies the teacher of a successful submission

**What can go wrong**

**System state on completion**
- A new valid subject creation request is recorded and available for an SDO officer to accept
- An invalid subject creation request is rejected and the teacher is notified of that fact.

```plantuml
@startuml
|#lightblue|Teacher|
start
:The teacher fills out the subject creation form;
:The teacher submits the subject creation form;
|#lightgray|SIS|
    if (Verify data) then (valid data)
        :The system stores the subject creation form;
        :The system notifies the SDO of a new subject creation form;
        :The system notifies the teacher of success;
        stop
    else (invalid data)
        :The system notifies the teacher of a failure;
        stop;
    endif
@enduml
```

##### Use Case: Edit non-essential subject info
###### Starting situation (Initial assumption)
- The teacher must be able to log in to the system 
- The teacher has to be authorized to edit non-essential subject information.
- The subject must already exist in the system.
###### Normal
1. The teacher logs into their account.
2. The teacher navigates to subject they wish to edit non-essential subject info.
3. The system displays current subject information.
4. The teacher navigates to the edit essential info
5. The teacher modifies the fields they wish to change, such as the subject's description ...
6.  The teacher submits the changes.
7.  The system checks if updated information about subject is valid.
8.  The system updates the subject information in the database.
9.  The system notifies the teacher that the update was successful.
###### What can go wrong
- If the teacher enters invalid information, the system displays an error message and the teacher will decide if they want to try again to edit the subject information or to end editing without changing anything.
###### System state on completion
- Subject information is updated, the teacher is notified about the successful completion.
- Non-valid subject information is rejected and the teacher is notified about the error and decide what they want to do the next.

```plantuml
@startuml
|Teacher|
start
:The teacher logs into her/his account;
:The teacher navigates to subject to edit;
:The system displays current subject info;
:The teacher navigates to the edit non-essential info;
repeat
    :The teacher modifies non-essential subject info;
    :The teacher submits changes;
    |System|
    if (Verify data) then (valid data)
        :The system updates subject info in a database;
        :The system notifies the teacher of success;
        stop
    else (invalid data)
        :The system displays error message;
    endif
|Teacher|
repeat while (Try again to edit subject info?) is (yes)
->no;
:No changes;
stop
@enduml
```
##### Use Case: Edit essential subject info
###### Starting situation (Initial assumption)
- The teacher must be able to log in to the system 
- The teacher has to be authorized to edit essential subject information.
- The subject must already exist in the system.
###### Normal
1. The teacher logs into their account.
2. The teacher navigates to subject they wish to edit essential subject info.
3. The system displays current subject information.
4. The teacher navigates to the edit non-essential info
5. The teacher modifies the fields they wish to change, such as the subject's name, code, credits, timetable, teachers ...
6.  The teacher submits the changes.
7. The SDO approves the changes.
8.  The system checks if updated information about subject is valid.
9.  The system updates the subject information in the database.
10.  The system notifies the SDO and the teacher that the update was successful.
###### What can go wrong
- If the SDO does not approve change that the teacher did, the error message is sent to the teacher and the teacher will decide if they want to try again to edit the subject information or to end editing without changing anything.
- If edited subject info is invalid, the system displays an error message and the SDO will decide if they want to fix error or to send error message to the teacher.
###### System state on completion
- Subject information is updated, the SDO and the teacher is notified about the successful completion.
- Non-approved subject information is rejected and the teacher is notified about the error and decide what they want to do the next.
- Non-valid information is rejected and the SDO will decide what to do the next. The SDO can send error message to the teacher and let them decide what do to like with non-approved information or the SDO can try to fix error.

##### Use Case: Edit subject
###### Starting situation (Initial assumption)
- The SDO must be able to log in to the system 
- The SDO has to be authorized to edit subject information.
- The subject must already exist in the system.
###### Normal
1. The SDO logs into the system and accesses the subject management section.
2. The SDO selects the subject to edit.
3. The SDO modifies essential or non-essential fields they wish to change.
4.  The SDO submits the changes.
5.  The system checks if updated information about subject is valid.
6.  The system updates the subject information in the database.
7.  The system notifies the SDO that the update was successful.
###### What can go wrong
- If the SDO enters invalid information, the system displays an error message and the SDO will decide if they want to try again to edit the subject information or to end editing without changing anything.
###### System state on completion
- Subject information is updated, the SDO is notified about the successful completion.
- Non-valid subject information is rejected and the SDO is notified about the error and decide what they want to do the next.

##### Use Case: Set co/pre-requisites
###### Starting situation (Initial assumption)
- The teacher must be able to log in to the system 
- The teacher has to be authorized to set co/pre-requisites for the specific subject.
- The subject must already exist in the system.
###### Normal
1. The teacher logs into their account.
2. The teacher navigates to the subject for which they want to set co/prerequisites.
3. The system displays the current co/prerequisites for the chosen subject.
4. The teacher adds/modifies the subject's co/prerequisites from a list of available subjects.
5.  The teacher submits the changes.
6.  The system checks if selected subjects are valid co/prerequisites.
8.  The system updates the subject's co/prerequisites.
9.  The system notifies the teacher that the co/prerequisites have been successfully set.
###### What can go wrong
- If the teacher selects a subject that cannot logically be set as a co/prerequisite, the system displays an error message and the teacher will decide if they want to choose a different subject as a co/prerequisite.
###### System state on completion
- The subject's co/prerequisites are set in the system and the teacher is notified about the successful completion.
- Students are informed of the updated requirements.
- Non-valid subject's co/prerequisite is rejected and the teacher is notified about the error.


###### Send request to modify subject info
This use case describes a process, by which the teacher can send a request to the study department office for modification of essential subject info.

**Actors**
- Teacher
- SDO


**Precondition**
The teachers has logged in into their SIS account and have opened the form for modifying essential subject info.

**Normal**


**What can go wrong**
- The modification form contains some invalid values and the system notifies the teacher of a failed form submission.

**System state on completion**
- A new valid subject modification request is recorded and available for an SDO officer to accept, while notifying both the teacher and the SDO of the fact.
- An invalid subject modification request is rejected and the teacher is notified of that fact.

***
###### Activate/deactivate a subject
This use case describes a process, by which the SDO can activate/deactivate a subject.

**Actors**
- SDO


**Precondition**
The SDO has logged in to their SIS account and has opened the form for activating/deactivating a subject.


**Normal**
1. The SDO selects a subject by its shortcode and is provided with the option of activating/deactivating the subject.
2. The SDO clicks on the activate/deactivate subject button.
3. The application displays a verification window, to warn the SDO if they truly want to go proceed with the operation.
4. The SDO confirms the operation.
5. SIS verifies that the operation can be done, does it and notifies the SDO of it. 


**What can go wrong**
- The subject activation/deactivation cannot be done(for example due to the subject being taught at the moment) and the SDO is notified of that.

**System state on completion**
- The subject is activated/deactivated and the SDO is notified of that.
- The subject activation/deactivation wasn't able to proceed and the SDO is notified of that.


## Information model

```plantuml
@startuml
class Visitor

class Person {
name
email
phone
}

class Student
class Teacher {
faculty
department
}
class SDO

class Subject {
name
shortcode
description
credits
hours
examination type

}
class StudyProgramme

Person <|-- Student
Person <|-- Teacher
Person <|-- SDO


Subject "0..n" <-- Subject : has prerequisites
Subject "0..n" <-- Subject : has corequisites
Subject "0..n" -- "0..n" StudyProgramme : " has subject"
Teacher -- Subject : guarantees
Teacher -- Subject : teaches
@enduml
```

### Visitor
Non-logged in visitor to the website.

### Person
A natural person with personal information like name, email, phone etc.

### Student
A person studying at the university.

### Teacher
A person teaching at the university.

### SDO
A person working as a study department officer at the university.

### Subject
An area of knowledge or study being taught at the university.