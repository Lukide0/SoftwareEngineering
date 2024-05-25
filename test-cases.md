# Test Cases

## Use Case: View and filter the list of courses

### Test Conditions

1.  All courses are displayed
2.  Only a filtered selection is displayed
3.  No course is displayed
4.  Courses are ordered by default
5.  A custom ordering is used
6.  Click on the "View Courses" button
7.  Special message displayed

### Test Case 1

|                      |                                                                                             |
| -------------------- | ------------------------------------------------------------------------------------------- |
| **ID:**              | 1                                                                                           |
| **Title:**           | User views a list of all courses                                                            |
| **Priority:**        | High                                                                                        |
| **Preconditions:**   | A set of courses (and their attributes) is registered in the system. The user is logged in. |
| **Post conditions:** | A list of all registered courses is shown, sorted in a default way (alphabetically).        |
| **Role:**            | A registered User.                                                                          |
| **Test data**        | A set of courses.                                                                           |
| **Test conditions**  | 1, 4, 6                                                                                     |

| Test Steps |                                          |                                                       |        |         |
| ---------- | ---------------------------------------- | ----------------------------------------------------- | ------ | ------- |
| #          | Action                                   | Expected result                                       | Result | Comment |
| 1.         | User clicks "View Courses" button        | A list of all courses is shown.                       |        |         |
| 2.         | User does not apply any filter condition | The list is sorted in a default way (alphabetically). |        |         |

### Test Case 2

|                      |                                                                                                                             |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **ID:**              | 2                                                                                                                           |
| **Title:**           | User view a set of courses based on custom filter                                                                           |
| **Priority:**        | Medium                                                                                                                      |
| **Preconditions:**   | A set of courses (and their attributes) is registered in the system. The user is logged in.                                 |
| **Post conditions:** | All courses matching the entered filter are shown (and no other ones). The courses are ordered based on a custom condition. |
| **Role:**            | A registered User.                                                                                                          |
| **Test data**        | A set of courses. A filter condition. An ordering criterium.                                                                |
| **Test conditions**  | 2, 5, 6                                                                                                                     |

| Test Steps |                                   |                                                                             |        |         |
| ---------- | --------------------------------- | --------------------------------------------------------------------------- | ------ | ------- |
| #          | Action                            | Expected result                                                             | Result | Comment |
| 1.         | User clicks "View Courses" button | A list of all courses is shown, sorted in a default way.                    |        |         |
| 2.         | User applies a filter condition   | The list of courses is refreshed (filtered) based on the entered condition. |        |         |
| 3.         | User sets an ordering             | The list of courses is reordered based on the desired ordering.             |        |         |

### Test Case 3

|                      |                                                                                             |
| -------------------- | ------------------------------------------------------------------------------------------- |
| **ID:**              | 3                                                                                           |
| **Title:**           | User views an empty set of courses                                                          |
| **Priority:**        | Medium                                                                                      |
| **Preconditions:**   | A set of courses (and their attributes) is registered in the system. The user is logged in. |
| **Post conditions:** | A special message is shown. No subjects are listed.                                         |
| **Role:**            | A registered User.                                                                          |
| **Test data:**       | A set of courses. An unsatisfiable filter condition (non-existent subject code).            |
| **Test conditions:** | 3, 6, 7                                                                                     |

| Test Steps |                                         |                                                          |        |         |
| ---------- | --------------------------------------- | -------------------------------------------------------- | ------ | ------- |
| #          | Action                                  | Expected result                                          | Result | Comment |
| 1.         | User clicks "View Courses" button       | A list of all courses is shown, sorted in a default way. |        |         |
| 2.         | User enters a non-existent subject code | A special message is shown. No subjects are listed.      |        |         |

## Use Case: Put a course in cart

### Test Conditions

1. The cource is available.
2. The cource is already in the cart.
3. The cource is not available.
4. The "Put course in cart" button is enabled.
5. The "Put course in cart" button is disabled.
6. Added course is displayed in cart.
7. Error message is shown

### Test Case 1

|                              |                                                                                                                                                       |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ID:**                      | 4                                                                                                                                                     |
| **Title:**                   | Student successfully adds an available course to cart                                                                                                 |
| **Priority:**                | High                                                                                                                                                  |
| **Preconditions:**           | The student is logged in, the course is available, the course is not already in the cart, and the student is on the Course Detail page of the course. |
| **Post conditions:**         | The course is added to the student's cart, and the "Put course in cart" button is disabled.                                                           |
| **Role:**                    | Student                                                                                                                                               |
| **Test data:**               |
| **Covered test conditions:** | 1,4,5,6                                                                                                                                               |

| Test Steps |                                            |                                                                      |        |         |
| ---------- | ------------------------------------------ | -------------------------------------------------------------------- | ------ | ------- |
| #          | Action                                     | Expected result                                                      | Result | Comment |
| 1.         | Student clicks "Put course in cart" button | The course is added to the student's cart and the button is disabled |        |         |
| 2.         | Student goes to view cart                  | All course in cart are shown with the new added course               |        |         |

### Test Case 2

|                              |                                                                                                                         |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **ID:**                      | 5                                                                                                                       |
| **Title:**                   | Student attempts to add a course that is alrady in threir cart                                                          |
| **Priority:**                | High                                                                                                                    |
| **Preconditions:**           | The student is logged in, the course is already in the cart and the student is on the Course Detail page of the course. |
| **Post conditions:**         | The error message is shown                                                                                              |
| **Role:**                    | Student                                                                                                                 |
| **Test data:**               |
| **Covered test conditions:** | 2,5,6,7                                                                                                                 |

| Test Steps |                                            |                                                                         |        |         |
| ---------- | ------------------------------------------ | ----------------------------------------------------------------------- | ------ | ------- |
| #          | Action                                     | Expected result                                                         | Result | Comment |
| 1.         | Student clicks "Put course in cart" button | The error message is shown                                              |        |         |
| 2.         | Student goes to view cart                  | All course in cart are shown even the course which student tries to add |        |         |

### Test Case 3

|                              |                                                                                                                    |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **ID:**                      | 6                                                                                                                  |
| **Title:**                   | Student attempts to add a course that is not available                                                             |
| **Priority:**                | High                                                                                                               |
| **Preconditions:**           | The student is logged in, the course is not available, and the student is on the Course Detail page of the course. |
| **Post conditions:**         | The error message is shown                                                                                         |
| **Role:**                    | Student                                                                                                            |
| **Test data:**               |
| **Covered test conditions:** | 3,5,6,7                                                                                                            |

| Test Steps |                                            |                                                                            |        |         |
| ---------- | ------------------------------------------ | -------------------------------------------------------------------------- | ------ | ------- |
| #          | Action                                     | Expected result                                                            | Result | Comment |
| 1.         | Student clicks "Put course in cart" button | The error message is shown                                                 |        |         |
| 2.         | Student goes to view cart                  | All course in cart are shown without the course which student tries to add |        |         |
