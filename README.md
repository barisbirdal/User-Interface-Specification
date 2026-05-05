# User Interface Specification: User Management Screen

## 1. Overview

The User Management screen is where administrators can view, filter, create and edit user accounts within the system. This document outlines how the User Management screen should work and what it should look like.

## 2. Initial Page State

When you go to the User Management screen you should see the following:

* The list of users on the side of the screen should already be populated with the existing users from the system.

* The "Hide Disabled User" checkbox should be checked by default so you do not see any users who are disabled.

* The form on the side of the screen should either be empty and ready to create a new user or it should show the details of a user you selected from the list.

* The "Save User" button should be disabled until you make some changes to the form.

## 3. UI Layout & Component Details

The screen has a toolbar and a main area that is split into two columns. The left column has a list of users and the right column has a form to edit user details.

### 3.1. Top Action Toolbar

* The "New User" button is blue and located at the top left. When you click it the form on the side of the screen clears and you can start creating a new user.

* The "Hide Disabled User" checkbox is next to the New User button. When you check or uncheck it the list of users on the side of the screen updates to show or hide disabled users.

* The "Save User" button is blue and located at the right. When you click it the form data gets sent to the system to create an user or update an existing one.

### 3.2. Data Grid (Left Panel)

* The list of users is a table.

* The columns show the users ID, username, email and whether they are enabled or not.

* You can sort the list by clicking on any column header.

* You can filter the list by clicking the filter icon on a column header and typing in what you're looking for.

* When you click on a row it highlights and the form on the side of the screen populates with that users details.

### 3.3. User Detail Form (Right Panel)

* The form is where you can edit user details.

* The title of the form changes depending on whether you're creating a new user or editing an existing one.

* The form has fields for the users username, display name, phone number, email, user roles and whether they are enabled or not.

* The user roles field is a menu where you can select multiple roles.

## 4. Component. Interactions

1. When you select a user from the list the form on the side of the screen populates with their details.

2. The "Save User" button only works if you have filled in all the required fields and they are valid. If you try to save and something is wrong the field will turn red. Show an error message.

3. When you select user roles they appear as chips or tags, in the input box.

4. The system remembers how you sorted and filtered the list of users even after you save changes to a user. This way you do not have to redo your sorting and filtering every time you make a change.
