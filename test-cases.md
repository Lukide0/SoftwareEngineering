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
