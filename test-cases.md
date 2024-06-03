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

**ID:** 1  
**Title:** User views a list of all courses  
**Priority:** High  
**Preconditions:** A set of courses (and their attributes) is registered in the system. The user is logged in.
**Post conditions:** A list of all registered courses is shown, sorted in a default way (alphabetically).  
**Role:** A registered User.  
**Test data** A set of courses.  
**Test conditions** 1, 4, 6

#### Test Steps

| #   | Action                                   | Expected result                                       | Result | Comment |
| --- | ---------------------------------------- | ----------------------------------------------------- | ------ | ------- |
| 1.  | User clicks "View Courses" button        | A list of all courses is shown.                       |        |         |
| 2.  | User does not apply any filter condition | The list is sorted in a default way (alphabetically). |        |         |

### Test Case 2

**ID:** 2  
**Title:** User view a set of courses based on custom filter  
**Priority:** Medium  
**Preconditions:** A set of courses (and their attributes) is registered in the system. The user is logged in.  
**Post conditions:** All courses matching the entered filter are shown (and no other ones). The courses are ordered based on a custom condition.
**Role:** A registered User.  
**Test data** A set of courses. A filter condition. An ordering criterium.  
**Test conditions** 2, 5, 6

#### Test Steps

| #   | Action                            | Expected result                                                             | Result | Comment |
| --- | --------------------------------- | --------------------------------------------------------------------------- | ------ | ------- |
| 1.  | User clicks "View Courses" button | A list of all courses is shown, sorted in a default way.                    |        |         |
| 2.  | User applies a filter condition   | The list of courses is refreshed (filtered) based on the entered condition. |        |         |
| 3.  | User sets an ordering             | The list of courses is reordered based on the desired ordering.             |        |         |

### Test Case 3

**ID:** 3  
**Title:** User views an empty set of courses  
**Priority:** Medium  
**Preconditions:** A set of courses (and their attributes) is registered in the system. The user is logged in.
**Post conditions:** A special message is shown. No subjects are listed.  
**Role:** A registered User.  
**Test data:** A set of courses. An unsatisfiable filter condition (non-existent subject code).  
**Test conditions:** 3, 6, 7

#### Test Steps

| #   | Action                                  | Expected result                                          | Result | Comment |
| --- | --------------------------------------- | -------------------------------------------------------- | ------ | ------- |
| 1.  | User clicks "View Courses" button       | A list of all courses is shown, sorted in a default way. |        |         |
| 2.  | User enters a non-existent subject code | A special message is shown. No subjects are listed.      |        |         |

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

**ID:** 4  
**Title:** Student successfully adds an available course to cart  
**Priority:** High  
**Preconditions:** The student is logged in, the course is available, the course is not already in the cart, and the student is on the Course Detail page of the course.
**Post conditions:** The course is added to the student's cart, and the "Put course in cart" button is disabled.  
**Role:** Student  
**Test data:**  
**Covered test conditions:** 1,4,5,6

#### Test Steps

| #   | Action                                     | Expected result                                                      | Result | Comment |
| --- | ------------------------------------------ | -------------------------------------------------------------------- | ------ | ------- |
| 1.  | Student clicks "Put course in cart" button | The course is added to the student's cart and the button is disabled |        |         |
| 2.  | Student goes to view cart                  | All course in cart are shown with the new added course               |        |         |

### Test Case 2

**ID:** 5  
**Title:** Student attempts to add a course that is alrady in threir cart  
**Priority:** High  
**Preconditions:** The student is logged in, the course is already in the cart and the student is on the Course Detail page of the course.
**Post conditions:** The error message is shown  
**Role:** Student  
**Test data:**  
**Covered test conditions:** 2,5,6,7

#### Test Steps

| #   | Action                                     | Expected result                                                         | Result | Comment |
| --- | ------------------------------------------ | ----------------------------------------------------------------------- | ------ | ------- |
| 1.  | Student clicks "Put course in cart" button | The error message is shown                                              |        |         |
| 2.  | Student goes to view cart                  | All course in cart are shown even the course which student tries to add |        |         |

### Test Case 3

**ID:** 6  
**Title:** Student attempts to add a course that is not available  
**Priority:** High  
**Preconditions:** The student is logged in, the course is not available, and the student is on the Course Detail page of the course.
**Post conditions:** The error message is shown  
**Role:** Student  
**Test data:**  
**Covered test conditions:** 3,5,6,7

#### Test Steps

| #   | Action                                     | Expected result                                                            | Result | Comment |
| --- | ------------------------------------------ | -------------------------------------------------------------------------- | ------ | ------- |
| 1.  | Student clicks "Put course in cart" button | The error message is shown                                                 |        |         |
| 2.  | Student goes to view cart                  | All course in cart are shown without the course which student tries to add |        |         |

## Use Case: View courses according to degree plan

### Test Conditions

1. Click on the "View courses according to the degree plan" button
2. All courses according to the degree plan are displayed
3. Special message displayed if no degree plan is chosen
4. No courses are displayed becouse the student has not chosen a degree plan yet yet and there are not common courses for all degree plans
5. Common courses for all degree plans are displayed when the student has not chosen a degree plan yet

### Test Case 1

**ID:** 1  
**Title:** The student views courses according to their degree plan  
**Priority:** High  
**Preconditions:** The student has a degree plan registered in the system. The user is logged in.  
**Post conditions:** A list of all courses according to the degree plan is dispalyed.  
**Role:** Student.  
**Test data**: A set of courses for a specific degree plan.  
**Test conditions**: 1, 2

#### Test Steps

| #   | Action                                                                | Expected result                                                  | Result | Comment |
| --- | --------------------------------------------------------------------- | ---------------------------------------------------------------- | ------ | ------- |
| 1.  | The student clicks "View courses according to the degree plan" button | A list of all courses according to the degree plan is displayed. |        |         |

### Test Case 2

**ID:** 2  
**Title:** The student views an empty list of courses becouse no degree plan is chosen  
**Priority:** Medium  
**Preconditions:** The student does not have a degree plan registered in the system. The user is logged in.  
**Post conditions:** A special message is shown. No courses are listed.  
**Role:** Student  
**Test data**: No degree plan.  
**Test conditions**: 1, 3, 5

#### Test Steps

| #   | Action                                                                | Expected result                                                 | Result | Comment |
| --- | --------------------------------------------------------------------- | --------------------------------------------------------------- | ------ | ------- |
| 1.  | The student clicks "View courses according to the degree plan" button | A special message is shown indicating no degree plan is chosen. |        |         |
| 2.  | System displays no courses                                            | The course list is empty.                                       |        |         |

### Test Case 3

**ID:** 3  
**Title:** The student views common courses becouse no degree plan is chosen  
**Priority:** Medium  
**Preconditions:** The student does not have a degree plan registered in the system. The user is logged in. Common courses exist.  
**Post conditions:** A list of common courses for all degree plans is shown.  
**Role:** Student.  
**Test data**: A set of common courses. No degree plan.  
**Test conditions**: 1, 3, 4

#### Test Steps

| #   | Action                                                                | Expected result                                                 | Result | Comment |
| --- | --------------------------------------------------------------------- | --------------------------------------------------------------- | ------ | ------- |
| 1.  | The student clicks "View courses according to the degree plan" button | A special message is shown indicating no degree plan is chosen. |        |         |
| 2.  | System displays common courses                                        | A list of common courses for all degree plans is displayed.     |        |         |

## Use Case: Un-enroll from a course

### Test Conditions

1. Click on the "Un-enroll from this course" button
2. A warning containing information about the course is displayed and two buttons: Un-enroll and Cancel Un-enrollment.
3. Click on the "Un-enroll" button
4. Input the student password and the un-enrollment goes through

### Test Case 1

**ID:** 1  
**Title:** The student successfully unenrolls from an enrolled course
**Priority:** High  
**Preconditions:** The student is enrolled in the course and is able to un-enroll. The student is logged in.  
**Post conditions:** The student is un-enrolled from the course, making him no longer enlisted in given course.  
**Role:** Student.  
**Test data**: A set of enrolled courses.  
**Test conditions**: 1, 2, 3, 4

#### Test Steps

| #   | Action                                                 | Expected result                                                                    | Result | Comment |
| --- | ------------------------------------------------------ | ---------------------------------------------------------------------------------- | ------ | ------- |
| 1.  | The student clicks "Un-enroll from this course" button | A warning is displayed along with two buttons: Un-enroll and Cancel Un-enrollment. |        |         |
| 2.  | The student clicks "Un-enroll"                         | The student is prompted with a password input                                      |        |         |
| 3.  | The student inputs their password and press enter      | The student is successfully un-enrolled from the course                            |        |         |

### Test Case 2

**ID:** 2
**Title:** The student can't un-enroll due to date being past the date of un-enrollment
**Priority:** Medium  
**Preconditions:** The student is enrolled in the course and it's paste the date of un-enrollment. The student is logged in.  
**Post conditions:** The student is displayed an error message indicating that it's past the date of un-enrollment.  
**Role:** Student.  
**Test data**: A set of enrolled courses.  
**Test conditions**: 1

#### Test Steps

| #   | Action                                                 | Expected result                                                                                                              | Result | Comment |
| --- | ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- | ------ | ------- |
| 1.  | The student clicks "Un-enroll from this course" button | An error message is displayed saying that it's paste the date of un-enrollment, providing a link to contact study department |        |         |

### Test Case 3

**ID:** 3
**Title:** The student can't un-enroll due to incorrect password
**Priority:** Medium  
**Preconditions:** The student is enrolled in the course and can un-enroll. The student is logged in.  
**Post conditions:** The student gets logged out.  
**Role:** Student.  
**Test data**: A set of enrolled courses.  
**Test conditions**: 1, 2, 3, 4

#### Test Steps

| #   | Action                                                          | Expected result                                                                    | Result | Comment |
| --- | --------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ------ | ------- |
| 1.  | The student clicks "Un-enroll from this course" button          | A warning is displayed along with two buttons: Un-enroll and Cancel Un-enrollment. |        |         |
| 2.  | The student clicks "Un-enroll"                                  | The student is prompted with a password input                                      |        |         |
| 3.  | The student inputs incorrect password and presses enter 4 times | The student is logged out of their account.                                        |        |         |
