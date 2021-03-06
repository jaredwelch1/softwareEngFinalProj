Testing

##Procedure

Testing will need to occur at every stage of new features, and along with those features, tests should be made to test those things before they are added to the software. These tests will remain recorded to be retested when newer changes are added. 


###Database Tests
We need to:

- Test that we are able to insert new data into all tables.
  
    - Failure scenarious for test:
    
        - Insertion into User table does not have the required fields (ID, email, first_name, permission_level, last_name) 
        
        - Insertion into Manifest Table does not have all required fields (version, manifest_id, category, last_edit, data, ownerID, title, upload_date)
        
        - Failure if any of supplied data does not match a valid data type for that field (i.e., string for an integer data field)

- Test that we can select data from all tables

     - Failure cases for this test:
         
          - A valid selection on a test row that will exist for each table with expected test values does not return the expected test values. (i.e., we have a row for id 1 that we created with test data and when we query that test row we do not get the data we should)
             
- Ensure that foreign keys work properly. (Should be unable to assign a value that does not exist in the linked table.)

    - Failure case:
        
        - Successful creation of a row in a table that does not have a forgein key that matches an existing value; If we can create such a row then our foreign keys are not linked as intended so the test failes

- Test that files don't change upon being uploaded and then downloaded.

    - Failure case:
    
        - Flow for test: upload a file, then download the same file. If the two files do not match **exactly** test fails.
        
- Ensure that any sql scripts we need to run on the site works on the server first. (i.e. run any insert, update, delete, etc. statements directly in the database.)

    - Failure case:
    
      - If a query to an existing table does not return expected test data for that test, this test fails. Test queries will need to exist for each unit test that covers this functionality, with test data respective to the test query. If a test query returns invalid data, data that does not match exactly, or some other unexpected behavior other than successful returned data, the test fails.
      
###User Interface
We need to:

- Test buttons and links to make sure that they direct to the proper page
  
  - Workflow:
      
      - Must create a list of buttons and their expected function, then starting from the beginning of the list, all buttons must be tested for their functionaltiy. 

  - Failure case:
  
      - Button clicked does not lead to intended place; 

- Compare filled forms to actual database entry to make sure all fields populated correctly.

    - Failure:
    
       - Form filled out and successful upload occurs, but database does not properly reflect the data supplied by the user

- Ensure that admin functions and features can only be seen by admins.

    - Workflow:
    
        - List of admin privileges to reference, using a normal user account, test that those features are unavailable.

    - Failure:
    
        - A user that does not have admin privileges is allowed access to admin functionality.
        
        

###Data Entry

Our forms should:

- Be able to handle invalid data entry. (i.e. invalid data types, exceeds the length we can process, etc.)

  - Workflow:
  
      - User attempts to submit a form that is either not filled out completely OR filled out with improper data.
      
   - Failure:
   
      - Form is submitted without error message and without preventing an invalid submission
      
##Regression Testing Plan

In order to ensure that all new functionality does not invalidate previously working pieces of our software, we must implement regression testing. This refers to testing of old features in an organized way to ensure nothing has been broken by new additions.

The plan for our regression testing is as follows

- Following all new features being finished and integrated into the application, a series of both unit tests and manual workflow tests (such as clicking all buttons for example) will be conducted. All tests that are created during the work for that sprint, uplon successful completion of that function, will then be added to the already existing regression tests. By creating a specific suite of tests, and both adding and maintening those tests as we progress, we can esnure that previously tested functionality will be tested again at ever iteration of the application.

- Workflow: 

* Test login

* test search works and displays results

* test clicking a displayed manifest result leads user to that manifest page

* Test download and upload of manifest

* Test user account infor

##Integration Testing

Our plan for integration testing is to organize our tests by 3 main categories:

- User Interface

- Database and Data Access

- Controller testing (those features which send request from the front end to attempt to access back end data)

Those categories will allow us to organize our tests and testing procedure in a way that allows to to test the application in terms of its overall funcionality at a high level.

Within each larger group, we will divide up testing based upon sprints that the tests and features were written. An example would be as follows:

- User Interface:

    - Sprint 1 features
    
    - Sprint 2 features
    
    - Sprint 3 features
    
Further specifying testing groups within our larger classification will allow us to not only keep features and testing in an organized workflow, but also help us isolate where the feature was originally working chronologically to help us fix issues as they arise more effectively, by giving us a specific place to look for the original working version.

##User acceptance Testing

As part of our testing workflow, we have tests in place to ensure things are working as expected. However, when the product is finished by us, we will still need to verfiy the users of the software are satisfied with the work. The end user for our purpose will be those who will be using the Manifest sharing site. We will have them test the software and verify that it works for their needs

* We will list use cases and document how to access that funcionality. Then the end user will test the software live, attempting to use it to be all the use ca

* The system should be thoroughly tested, from creating a new user, logging in, creating a manifest, uploading files for that manifest, then searching for that manifest, then editing, then downloading. All of those should be possible for every new user, and verified working with the live testing. 

* Take feedback from the end user. If they are not satisfied, make the improvements required. If they are satisifed, but would like quality of life fixes for the next project version release, they will be noted for future development. 

##Unit Testing

We have a document, [linked here](https://github.com/jaredwelch1/softwareEngFinalProj/blob/master/testing/readme.md), that outlines our procedure and plans for unit tests. We will use unit tests to test our application on the smallest level on functionality. We will try to create unit tests for basic features, such as valid log in cases, valid queries, and other low level, single step functionaltiy such as those will be covered as best as we can by unit testing. Refer to the document for more specific details. 

##Edge Cases

Edge cases refer to those situations which only occur rarely, which may be hard to think of through the traditional manner of testing. Edge cases should test the boundaries of our application, trying to find as many weaknesses in the software which are due to mishandling some behavior that is traditionally not common in the work flow. In other words, edge case testing is important as it is designed to test the software outside of the obvious testing. Regression testing and integeration testing will not be exhaustive, and it is up to us to think of and test edge cases in our software.

Our plan for approaching test cases is to try our best to test the high end and low end of our functions and methods. If the extreme cases work, we can be reasonably confident that it will also cover those cases within the bounds of the upper and lower ends. A good similie is boundary conditions. We will try to found the furthest acceptable boundary, and test those boundaries, in order to try to cover all the edge case behavior as effectively as possible. 

##Verification/Validation

- Validation refers to ensuring that our requirements are met by the features of our software. This is accomplished through User Acceptance Testing. Ulimately, the end User is who we must go to for Validation of the software. Their feedback will determine whether we meet the end user's requirements.

- Verification refers to ensuring that our software does what it is designed to do. While validation tests that we meet our requirements, verification tests that our software does what we intend it to do, separate from what the requirements asked. This is covered by regression testing, integration testing, and unit testing. 

##Testing Workflow 

###Unit Testing

Unit tests, designed to test the low level one dimensional functions of software, did not seem to be very applicable to our application. While we understand the purpose and usefulness of unit testing, our testing plan does not include unit tests. 

###Integration Tests

Most of our tests are integration tests, performed by using the software for its intended purpose, through its own UI elements, to ensure those elements work and each functional requirement is satisfied. For clarity, some testing groups are organized based on the functionality they are testing, relative to the requirements document we put together. This ensures our testing covers verification and validation. We must further test validity with performing a demo for the perspective client requesting the software. 

- Login Testing

    * Test valid username/valid password
    
        - should result in successful login
        
    * Test valid username/invalid passwordt
    
        - should result in error message to user
        
    * Test invalid username, valid password
    
        - should result in error message to user
        
    * Test invalid username/invalid password
    
        - should result in error message to user
        
- Logout testing

    * Test logging out actually logs user out and ends session
    
        - logout, then attempt to go through pages. All should redirect to login, and not allow user to see content
        
- Account creation testing 

    * Test valid completion of account creation form and valid submission
    
        - should result in new account created, tested by logging in with it after account creation. 
        
    * Test invalid form completion, attempt submit, verify it fails and database doesn't get any new information
    
        - should result in error message to user, should also verify that database is unchanged 
        
- Account Session Management

    * Test that no pages other than login are accessible when not logged in as a user
    
    * Test that once logged in, you can access all the pages that a user should be able to access 
    
        - This will be tested using the web page map we have, to ensure all pages are tested
        
    * Verify account information page reflects the current user 
    
- Manifest searching tests

    * For the following tests, we will need to ensure proper test data is in our database to ensure the tests are correctly set up
    
    TEST DATA:
    
    - Manifest(s) searchable by keyword 'test'
    
    - Manifests searchable by keyword 'test' with a date earlier or later than the previous manifest mentioned
    
    
    TEST CASES:
    
    - Search for 'test' manifests.
    
        * Enter 'test' into search field and press search. Expected outcome: all manifests with 'test' as a keyword will populate
        the table, showing their preview information in a tabular and organized output 
        
    - Order search results
    
        * After performing search on 'test', attempt to organize the table by the date, using the sorting tabs. Expected outcome:
        Search results organize properly based on their descending/ascending dates (depending on requested ordering)
       
   - Redirect to respective manifest view page 
   
       * After performing a search on 'test', click on a given manifest and ensure it redirects to its **own** manifest view, with all the same details as the preview showed. 
   
- Manifest Upload tests

    - navigate to upload screen, click upload manifest and files, try to upload a file.
    
        * Success message should display for a valid upload. Expected outcome from valid upload: Can find the uploaded files and download them, to verify same file was uploaded as can be downloaded after an upload.
        
    - Provide manifest file
    
        * Expected outcome: Valid manifest provided, upload succeeds, manifest information is absorbed from file for upload to database
        
        * Failure: test that uploading an invalid manifest file results in a failure to upload the manifest itself
        
    - Create manifest file
    
        * Expected success (assuming form filled out completeley) when clicking generate manifest: Manifest file is created and assosciated with the respective dataset files. 
        
        * Also, test here that not filling out form correctly does not allow for file creation. Try to submit invalid form.
        Expected outcome: Failure to generate a valid manifest file error message to user
        
     - Upload dataset files
     
         * Attempt to upload dataset/SNC files. 
             
             1. Valid files: Expect successful upload
             
             2. Invalid file type: Expect error message to user
             
             3. If valid files uploaded, and a manifest created, then test that after successful addition of a new manifest that the files uploaded match the ones kept by the server 
             
- Manifest download tests

    - Test ability to download manifest files and dataset files
    
        * Click download for manifest file and dataset file. Expected behavior: when download requested, file successfully downloads to local machine. 
        
###User Interface Testing:

This section is dedicated to all UI functionality not tested by integration testing. These tests are one dimensional, simple tests, to determine whether the functions of the UI such as page navigation work as intended.

It is broken down by page.

####Login:

- Login button

test pressing this attempts to login with form information

- User Registration

test redirects to user registration page

- Forgot password

test redirects to password recovery page

####Browse Manifests/Search manifests page

- Manifest display

test that clicking a manifest row redirects to manifest page

- Search

test that pressing search initiates a search

####Header

The header is used in several pages, but the code is the same, so it can be tested once.

- Profile Tab

Test clicking the user profile tab displays the menu items 1. Profile 2. Admin Panel (for admin account only) 3. Log out

- Profile
     
test redirects to user account page
    
- Admin panel
    
test redirects to account creation page
    
- log out
    
test redirects to log in page AND no longer able to access user only pages
    
####Manifest Creation/Upload

- Create 

Test clicking create will take supplied form data and create manifest file

- Upload

Open file browser to select a file for upload when user presses

- Upload Dataset Files

Open file browser to select a local file

####Sidebar 

- dashboard

test redirects to homepage

- Manifest editor

test redirects to page for editing a manifest

- manifest search

test redirects to search page


###Regression Testing Plan

These features were working and should be checked when updates are made:

1. Login should work for valid username and password, and fail otherwise

2. User should be able to create an account

3. User should be able to view all pages once logged in 

4. Those users not logged in should not be able to see any pages other than create account

5. Search should work

6. View manifest should display the manifests in the database currently 

7. All buttons on sidebar and header should work properly 

8. Upload a new manifest with files, check the upload succeeds

9. Download the newly uploaded manifest, should get back the files correctly

