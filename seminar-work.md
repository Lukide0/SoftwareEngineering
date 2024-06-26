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

##### SDO (Study department officer)

Administrative personnel tasked with managing subjects at a higher level, including activating/deactivating subjects, accepting subject creation requests, adding subjects to study programs, and editing subjects.

##### Student

Individuals who are enrolled in a study programme.
***
#### Use cases

##### Use case diagram
![use case diagram](img/use-case-diagram.png)

The use case diagram depicts the subject management system, involving three main actors: Teachers, Student Department Officers (SDO), and Students.  
The Teacher actor interacts with various use cases such as sending requests to create subjects, setting subject info, activating subjects, submitting requests to modify subject info, and editing non-essential subject info.  
The SDO actor is responsible for tasks like activating/deactivating subjects, accepting subject creation requests, adding subjects to study programs, and editing subjects.  
Students interact with the system to view subject info.

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

***

#### Use Case: Send request to create subject

This use case describes a process, by which a teacher can send a request to the study department office for creation of a new subject.

##### Actors

- Teacher


##### Precondition

The teacher has logged in into their SIS account and have opened the form for creating a new subject.


##### Normal flow

1. The teacher fills out the subject creation form by setting all of the required fields in the subject creation form (also by setting some optional fields).
2. The teacher submits the subject creation form.
3. SIS verifies if the field values of the submitted form are valid (possible number of credits, examination type, supported languages, etc.)
4. SIS stores the form and sends the SDO a notification in regards to the new subject creation form
5. SIS notifies the teacher of a successful submission


###### Alternative flows
- The form contains invalid information and is rejected with teacher being notified of that. 


###### System state on completion
- A new valid subject creation request is recorded and available for an SDO officer to accept
- An invalid subject creation request is rejected and the teacher is notified of that fact.

![creation image](img/use-case-creation.png)
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

***

#### Send request to modify subject info

This use case describes a process, by which the teacher can send a request to the study department office for modification of subject info.

##### Actors

- Teacher

##### Precondition
The teacher has logged in into their SIS account and have filled out all of the essential subject info that they want to change.

##### Normal flow
1. The teacher submits the subject modification form.
3. SIS verifies if the field values of the submitted form are valid
4. SIS stores the form and sends the SDO a notification in regards to the new subject modification request
5. SIS notifies the teacher of a successful submission

##### What can go wrong
- The modification form contains some invalid values and the system notifies the teacher of a failed form submission.

##### System state on completion
- A new valid subject modification request is recorded and available for an SDO to accept, while notifying both the teacher and the SDO of the fact.
- An invalid subject modification request is rejected and the teacher is notified of that fact.


***

#### Activate/deactivate a subject

This use case describes a process, by which the SDO can activate/deactivate a subject.

##### Actors
- SDO

##### Precondition
The SDO has logged in to their SIS account and has opened the form for activating/deactivating a subject.

##### Normal flow

1. The SDO selects a subject by its shortcode and is provided with the option of activating/deactivating the subject.
2. The SDO selects to activate/deactivate subject.
3. The application displays a verification window, to warn the SDO if they truly want to go proceed with the operation.
4. The SDO confirms the operation.
5. SIS verifies that the operation can be done, does it and notifies the SDO of it.

##### Alternative flows

- The subject activation/deactivation cannot be done(for example due to the subject being taught at the moment) and the SDO is notified of that.

##### System state on completion

- The subject is activated/deactivated and the SDO is notified of that.
- The subject activation/deactivation wasn't able to proceed and the SDO is notified of that.



***


#### Use Case: Edit essential subject info

##### Actors
- Teacher

##### Precondition

- The teacher must be able to log in to the system.
- The teacher has to be authorized to edit essential subject information.
- The subject must already exist in the system.


##### Normal flow

1. The teacher logs into their account.
2. The teacher navigates to subject they wish to edit essential subject info.
3. The system displays current subject information.
4. The teacher navigates to the edit essential info.
5. The teacher modifies the fields they wish to change, such as the subject's name, code, credits, timetable, teachers ...
6. The teacher sends the request to modify subject info.
7. The system checks if the updated information about subject is valid.
10. The system notifies the teacher that the request was successfully sent.


##### Alternative flows

- If edited subject info is invalid, the error message is sent to the teacher and the teacher will decide if they want to try again to edit the subject information or to end editing without changing anything.


##### System state on completion

- The request to midify subject info is sent and the teacher is notified about the successful request.
- Non-valid subject modification is rejected and the teacher is notified about the error and decide what they want to do the next.



***


#### Use Case: Edit non-essential subject info

##### Actors
- Teacher


##### Precondition

- The teacher must be able to log in to the system.
- The teacher has to be authorized to edit non-essential subject information.
- The subject must already exist in the system.


##### Normal flow

1. The teacher logs into their account.
2. The teacher navigates to subject they wish to edit non-essential subject info.
3. The system displays the current subject information.
4. The teacher navigates to the edit non-essential info.
5. The teacher modifies the fields they wish to change, such as the subject's description ...
6. The teacher submits the changes.
7. The system checks if updated information about subject is valid.
8. The system updates the subject information in the database.
9. The system notifies the teacher that the update was successful.


##### Alternative flows

- If the teacher enters invalid information, the system displays an error message and the teacher will decide if they want to try again to edit the subject information or to end editing without changing anything.


##### System state on completion

- Subject information are updated, the teacher is notified about the successful completion.
- Non-valid subject information is rejected and the teacher is notified about the error and decide what they want todo the next.


![edit non essential](img/edit-non-essentials.png)
```plantuml
@startuml
start
:The teacher logs into her/his account;
:The teacher navigates to subject to edit;
:The system displays current subject info;
:The teacher navigates to the edit non-essential info;
repeat
    :The teacher modifies non-essential subject info;
    :The teacher submits changes;
    :The system checks updated info;
    if (Verify data) then (valid data)
        :The system updates subject info in a database;
        :The system notifies the teacher of success;
        stop
    else (invalid data)
        :The system displays error message;
    endif
repeat while (Try again to edit subject info?) is (yes)
->no;
:No changes;
stop
@enduml
```



***



#### Use Case: Edit subject

##### Actors
- SDO

##### Precondition

- The SDO must be able to log in to the system.
- The SDO has to be authorized to edit subject information.
- The subject must already exist in the system.

##### Normal flow

1. The SDO logs into the system and accesses the subject management section.
2. The SDO selects the subject to edit.
3. The SDO modifies essential or non-essential fields they wish to change.
4. The SDO submits the changes.
5. The system checks if updated information about subject is valid.
6. The system updates the subject information in the database.
7. The system notifies the SDO that the update was successful.


##### Alternative flows

- If the SDO enters invalid information, the system displays an error message and the SDO will decide if they want to try again to edit the subject information or to end editing without changing anything.

##### System state on completion

- Subject information is updated, the SDO is notified about the successful completion.
- Non-valid subject information is rejected and the SDO is notified about the error and decide what they want to do the next.



***



#### Use Case: Set co/pre-requisites

##### Actors
- Teacher

##### Precondition

- The teacher must be able to log in to the system.
- The teacher has to be authorized to set co/pre-requisites for the specific subject.
- The subject must already exist in the system.

##### Normal flow

1. The teacher logs into their account.
2. The teacher navigates to the subject for which they want to set co/prerequisites.
3. The system displays the current co/prerequisites for the chosen subject.
4. The teacher adds/modifies the subject's co/prerequisites from a list of available subjects.
5. The teacher sends the request to modify subject`s co/prerequisites.
6. The system checks if selected subjects are valid co/prerequisites.
7. The system notifies the teacher that the request was successfully sent.

##### Alternative flows

- If the teacher selects a subject that cannot logically be set as a co/prerequisite, the system displays an error message and the teacher will decide if they want to choose a different subject as a co/prerequisite.

##### System state on completion

- The subject's co/prerequisites are set in the system and the teacher is notified about the successful submission of the request.
- Non-valid subject's co/prerequisite is rejected and the teacher is notified about the error.


***

#### Use Case: Add subject to study programme

##### Actors
- SDO

##### Precondition

- The SDO must be able to log in to the system.
- The SDO has to be authorized to add subjects to study programmes.
- The subject must already exist in the system.
- The study programme must already exist in the system.

##### Normal flow

1. The SDO logs into the system and accesses the study programme management section.
2. The SDO selects the study programme to which they want to add a subject.
3. The system displays the current list of subjects in the chosen study programme.
4. The SDO adds the subject to the study programme from a list of available subjects.
5. The SDO submits the changes.
6. The system checks if the selected subject is valid and not already part of the study programme.
7. The system updates the study programme with the added subject.
8. The system notifies the SDO that the subject has been successfully added to the study programme.

##### Alternative flows

- If the SDO selects a subject that is already part of the study programme, the system displays an error message, and the SDO will decide if they want to choose a different subject or cancel the operation.

##### System state on completion

- The subject is successfully added to the study programme, and the SDO is notified about the successful completion.
- Non-valid subjects are rejected, and the SDO is notified about the error.

![add to programme](img/add-subject-to-programme.png)
```plantuml
@startuml
|SDO|
start
:SDO logs into the system;
:SDO accesses study programme management;
repeat
    :SDO selects study programme;
    |System|
    :System displays current subjects in the study programme;
    |SDO|
    :SDO adds subject to study programme;
    |System|
    if (Subject is already in the study programme?) then (no)
        :System updates study programme with added subject;
        :System notifies SDO of success;
        stop
    else (yes)
        :System displays error message;
    endif
    |SDO|
    repeat while (Try again to add subject into the study programme) is (yes)
    -> no;
stop
@enduml
```


***

#### Use Case: View Subject Info

##### Actors

Student, Teacher, SDO

##### Precondition
- The user is logged into the system.
- The system contains up-to-date information on subjects.

##### Normal flow

1. **User Login:** The user logs into the system and is authenticated.
2. **Navigate to Subjects Overview:** The user navigates to the "Subjects Overview" section or tab within the system interface.
3. **Display Subject Search Interface:** The system displays the "Subject Search" interface, which includes a search bar and possibly filters for criteria such as name, code, semester, faculty, department, or the names of teachers associated with subjects.
4. **Enter Search Criteria:** The user inputs search criteria into the search bar, which can include the subject name, code, semester, faculty, department, or teacher's name.
5. **Submit Search:** The user submits the search query.
6. **Display Search Results:** The system processes the search query and displays a list of subjects matching the search criteria. If no subjects are found, the system displays a "No subjects found" message.
7. **Select Subject:** The user selects a subject from the list to view more information.
8. **Retrieve and Display Subject Info:** The system retrieves detailed information about the selected subject from the database and displays it. This information includes the subject name, description, credit hours, semester, faculty, department, list of teachers, and schedule.


##### Alternative Flows

- **No Search Results:** If no subjects match the search criteria, the system displays a message indicating that no subjects were found. The user can adjust their search criteria and try again.


##### System state on completion

- The user has accessed detailed information about the chosen subject.

![view info](img/view-subj-info.png)
```plantuml
@startuml
start
:User logs into the system;
partition User {
    :Navigate to the Subjects Overview section;
}
partition System {
    :Display Subjects Dashboard with search functionality;
}
partition User {
    :Search for subjects by name, code, semester, faculty, department, or teacher;
}
partition System {
    if (Subjects found based on criteria) then (yes)
        :Display list of subjects matching search criteria;
    else (no)
        :Display message "No subjects found matching criteria";
    endif
}
partition User {
    :Select a subject from the list;
}
partition System {
    :Retrieve detailed info for selected subject;
    :Display subject info including name, code, semester, faculty, department, assigned teachers, and description;
}
stop
@enduml
```


***



#### Use Case: Set Teachers for Subject

##### Actors

- SDO

##### Precondition

- The SDO must be logged into the system with sufficient privileges.
- The subject and teacher information must be available in the system database.

##### Normal flow

1. The SDO navigates to the subject management page.
2. The SDO selects the subject for which they want to assign teachers.
3. The system presents a list of available teachers.
4. The SDO selects one or more teachers to assign to the subject and confirms the selection.
5. The system updates the subject information with the assigned teacher(s) and displays a confirmation message.

##### Alternative flows

- No Teachers Available: If there are no available teachers to assign, the system displays a message indicating this.

##### System state on completion

- The selected teacher(s) are assigned to the subject, and this information is updated in the system.


***
#### Use Case: Accept subject info modification request

##### Precondition

- A teacher fills in a form with modifications of one subject's information.
- They submit the form as a request to the Study Department.
- The subject must already exist (approved by the SD) and the teacher must guarantee or teach this subject.

##### Normal flow

1. A SDO views the modifications of the information.
2. A SDO approves the modification request.
3. A SDO assigns a subject code to the subject.
4. The modifications are propagated to the system. (See the included Use case: "Update subject info").
5. The teacher (author) is notified of the approvement via e-mail.

##### Alternative flows

- If the SDO declines the modifications, the subject info remains unchanged. The teacher (author) is notified of the denial. The request is archived.

##### System state on completion:

- The subject info is modified (if the request was approved).
- The subject info remains unchanged (if the request was declined).

![accept request](img/accept-modification-request.png)
```plantuml
@startuml

|SDO|
start
:Review the subject creation request;
if (Is approved?) then (yes)
  :Assign a subject code;
|System|
  :Update subject info;
  :Enable teacher to edit info;
  :Enable students to view subject detail;
else (no)
  :Archive the request;
endif
:Notify the author of the result via e-mail;
stop

@enduml
```


***



#### Use Case: Accept subject creation request


##### Actors
- SDO

##### Precondition

- A teacher submits a subject creation request containing all the necessary information to the Study Department.

##### Normal flow

1. The SDO views the request.
2. The SDO checks if the request is valid.
3. The SDO approves the request.
4. The subject is inserted into the system.
5. The author of the request is notified of the result via email.

##### Alternative flows

- The SDO might not approve the request. In that case, the author is notified of the denial and the system remains unchanged.

##### System state on completion

- The system contains the newly created subject.



***

#### Use Case: Update subject info

##### Precondition

- The respective subject is already created.
- A teacher who wants to update the info must teach or guarantee this subject. - Within another Use case, there arises a need to update subject info.

##### Normal flow

1. The system receives the subject data that should be modified.
2. The system updates the information.
3. If there is a need to propagate these changes to another subjects (e.g. setting prerequisites), then their info is also modified.

##### Alternative flows

- If there arises a problem with prerequisite setting (e.g. a cycle is created), the operation should be canceled and the author should be notified via email.

##### System state on completion

- The system contains the updated info.


***

## Information model

![](img/info-model.png)

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

### Subject creation request
A request sent by a teacher to create a new subject

### Subject modification request
A request sent by a teacher to modify an existing subject
