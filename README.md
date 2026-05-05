# User Interface Specification: User Management Screen

## 1. Overview
This document outlines the user interface specifications and behavioral requirements for the "User Management" screen. This interface allows administrators to view, filter, create, and edit user accounts within the system.

## 2. Initial Page State
When a user navigates to the User Management screen, the following initial state should be established:
* **Data Grid (Left Panel):** Populated with the existing list of users fetched from the backend. 
* **Filter State:** The `Hide Disabled User` checkbox is **checked** by default. Consequently, the grid should initially filter out any users where the `Enabled` status is false.
* **Detail Form (Right Panel):** Should be in a read-only state or hidden until a specific user row is selected from the grid, OR it should default to the "New User" creation state with all fields empty if that is the preferred default flow.
* **Action Buttons:** The `Save User` button should remain disabled until valid modifications are made in the Detail Form.

## 3. UI Layout & Component Details

The screen is divided into a top action toolbar and a main content area split into two columns (Data Grid on the left, Form on the right).

### 3.1. Top Action Toolbar
* **`[ + New User ]` Button:** 
  * **Type:** Primary Action Button (Blue).
  * **Location:** Top left.
  * **Action:** Clears the Detail Form on the right, sets the form title to "New User", and readies the inputs for a new entry.
* **`Hide Disabled User` Checkbox:**
  * **Type:** Checkbox input with label.
  * **Location:** Next to the New User button.
  * **Action:** Triggers a client-side or server-side filter on the Data Grid to show/hide rows where `Enabled == false`.
* **`[ Save User ]` Button:**
  * **Type:** Primary Action Button (Blue).
  * **Location:** Top right.
  * **Action:** Submits the form data from the Right Panel to the API (handles both POST for new users and PUT/PATCH for existing users).

### 3.2. Data Grid (Left Panel)
* **Component Type:** Interactive Data Table / Grid.
* **Columns:**
  * `ID`: Numeric identifier.
  * `User Name`: String.
  * `Email`: String (e.g., admin@piworks.net).
  * `Enabled`: Boolean indicator (displays as "true" or "false", or localized strings).
* **Grid Features:**
  * **Sorting:** Clicking on any column header toggles ascending/descending sorting for that column (indicated by up/down arrows).
  * **Filtering:** Clicking the filter icon (funnel) on a column header opens an inline search/filter input for specific column queries.
  * **Selection:** Clicking a row highlights it (e.g., in a light blue color) and triggers an event to populate the Right Panel with that user's data.

### 3.3. User Detail Form (Right Panel)
* **Component Type:** Data Entry Form.
* **Title:** Dynamic. Displays "New User" when creating, or "Edit User" (or similar) when a row is selected.
* **Input Fields:**
  * **`Username`:** Text Input (Alphanumeric).
  * **`Display Name`:** Text Input.
  * **`Phone`:** Text Input (Should support standard phone number formatting/validation).
  * **`Email`:** Text Input (Must validate against standard email regex, e.g., *@*.com).
  * **`User Roles`:** Multi-select Dropdown.
    * Contains a placeholder: *"Select user roles..."*
    * Options visible in dropdown: `Guest`, `Admin`, `SuperAdmin`.
    * Supports selecting multiple roles.
  * **`Enabled`:** Checkbox. Determines active/inactive status.

## 4. Component Behaviors & Interactions
1. **Row Selection to Edit:** When a user clicks a row in the Left Panel (e.g., ID 2, Test User), the Right Panel form immediately populates with that user's specific details. The form title updates contextually.
2. **Form Validation:** The `Save User` button should only trigger the save function if required fields (Username, Email, User Roles) are filled and valid. Invalid fields should display a red border and an inline error message upon attempted save.
3. **Role Selection:** When opening the `User Roles` dropdown, multiple items can be clicked. Selected roles should display as chips/tags within the input box.
4. **State Persistence:** Sorting and filtering states on the Data Grid should be maintained even after saving a user, to prevent jarring UX resets.
