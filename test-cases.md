# Use Case: View and filter the list of courses

### Test Conditions
1.  a) All courses are displayed
    b) Only a filtered selection is displayed
    c) No course is displayed
2.  a) Courses are ordered by default
    b) A custom ordering is used
3. Click on the "View Courses" button
4. Special message displayed

## Test Case 1

__ID:__                   1  
__Title:__                User views a list of all courses  
__Priority:__             High  
__Preconditions:__        A set of courses (and their attributes) is registered in the system. The user is logged in.  
__Post conditions:__      A list of all registered courses is shown, sorted in a default way (alphabetically).  
__Role:__                 A registered User.  
__Test data__:            A set of courses.  
__Test conditions__:      1a, 2a, 3  

| Test Steps |                                          |                                                       |        |         |
|------------|------------------------------------------|-------------------------------------------------------| ------ | ------- |
| #          | Action                                   | Expected result                                       | Result | Comment |
| 1.         | User clicks "View Courses" button        | A list of all courses is shown.                       |        |         |
| 2.         | User does not apply any filter condition | The list is sorted in a default way (alphabetically). |        |         |

## Test Case 2

__ID:__                   2     
__Title:__                User view a set of courses based on custom filter  
__Priority:__             Medium  
__Preconditions:__        A set of courses (and their attributes) is registered in the system. The user is logged in.  
__Post conditions:__      All courses matching the entered filter are shown (and no other ones). The courses are ordered based on a custom condition.  
__Role:__                 A registered User.  
__Test data__:            A set of courses. A filter condition. An ordering criterium.  
__Test conditions__:      1b, 2b, 3  

| Test Steps |                                   |                                                                             |        |         |
|------------|-----------------------------------|-----------------------------------------------------------------------------| ------ | ------- |
| #          | Action                            | Expected result                                                             | Result | Comment |
| 1.         | User clicks "View Courses" button | A list of all courses is shown, sorted in a default way.                    |        |         |
| 2.         | User applies a filter condition   | The list of courses is refreshed (filtered) based on the entered condition. |        |         |
| 3.         | User sets an ordering             | The list of courses is reordered based on the desired ordering.             |        |         |

## Test Case 3

__ID:__                   3  
__Title:__                User views an empty set of courses  
__Priority:__             Medium     
__Preconditions:__        A set of courses (and their attributes) is registered in the system. The user is logged in.  
__Post conditions:__      A special message is shown. No subjects are listed.  
__Role:__                 A registered User.  
__Test data__:            A set of courses. An unsatisfiable filter condition (non-existent subject code).  
__Test conditions__:      1c, 3, 4

| Test Steps |                                         |                                                                          |        |         |
|------------|-----------------------------------------|--------------------------------------------------------------------------| ------ | ------- |
| #          | Action                                  | Expected result                                                          | Result | Comment |
| 1.         | User clicks "View Courses" button       | A list of all courses is shown, sorted in a default way.                 |        |         |
| 2.         | User enters a non-existent subject code | A special message is shown. No subjects are listed.                      |        |         |

# Use Case: View courses according to degree plan

### Test Conditions
1. Click on the "View courses according to the degree plan" button
2. All courses according to the degree plan are displayed
3. Special message displayed if no degree plan is chosen
4. No courses are displayed becouse the student has not chosen a degree plan yet yet and there are not common courses for all degree plans
5. Common courses for all degree plans are displayed when the student has not chosen a degree plan yet

## Test Case 1

__ID:__                   1  
__Title:__                The student views courses according to their degree plan  
__Priority:__             High  
__Preconditions:__        The student has a degree plan registered in the system. The user is logged in.  
__Post conditions:__      A list of all courses according to the degree plan is dispalyed.  
__Role:__                 Student.  
__Test data__:            A set of courses for a specific degree plan.  
__Test conditions__:      1, 2

| Test Steps |                                             |                                                       |        |         |
|------------|---------------------------------------------|-------------------------------------------------------| ------ | ------- |
| #          | Action                                      | Expected result                                       | Result | Comment |
| 1.         | The student clicks "View courses according to the degree plan" button | A list of all courses according to the degree plan is displayed. |        |         |

## Test Case 2

__ID:__                   2  
__Title:__                The student views an empty list of courses becouse no degree plan is chosen  
__Priority:__             Medium  
__Preconditions:__        The student does not have a degree plan registered in the system. The user is logged in.  
__Post conditions:__      A special message is shown. No courses are listed.  
__Role:__                 Student  
__Test data__:            No degree plan.  
__Test conditions__:      1, 3, 5

| Test Steps |                                             |                                                       |        |         |
|------------|---------------------------------------------|-------------------------------------------------------| ------ | ------- |
| #          | Action                                      | Expected result                                       | Result | Comment |
| 1.         | The student clicks "View courses according to the degree plan" button | A special message is shown indicating no degree plan is chosen. |        |         |
| 2.         | System displays no courses                 | The course list is empty.                             |        |         |

## Test Case 3

__ID:__                   3  
__Title:__                The student views common courses becouse no degree plan is chosen  
__Priority:__             Medium  
__Preconditions:__        The student does not have a degree plan registered in the system. The user is logged in. Common courses exist.  
__Post conditions:__      A list of common courses for all degree plans is shown.  
__Role:__                 Student.  
__Test data__:            A set of common courses. No degree plan.  
__Test conditions__:      1, 3, 4

| Test Steps |                                             |                                                       |        |         |
|------------|---------------------------------------------|-------------------------------------------------------| ------ | ------- |
| #          | Action                                      | Expected result                                       | Result | Comment |
| 1.         | The student clicks "View courses according to the degree plan" button | A special message is shown indicating no degree plan is chosen. |        |         |
| 2.         | System displays common courses              | A list of common courses for all degree plans is displayed. |        |         |
