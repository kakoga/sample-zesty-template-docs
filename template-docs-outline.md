What are the assumptions that we are making about the user?
  User has moderate level of understanding for GitHub and a general understanding about how Zesty works

Is this a user that knows how to use Github? Is this a guide for the complete novice?
What is the scope of this guide? Just templating? Be able to work off a base template and confidently make changes and additions to both the content schema and the design of the site.

#What are Zesty.io templates?

A. Purpose
    1. Creating your own repeatable website with custom designs connected to CMS interface within a few minutes.
    2. Making templates for personal use and/or public
B. Languages
    1. What languages are they written in?
      a. Xml
      b. Html
      c. Css,less, scss
      d. Parsley
      e. javascript
C. Process
    1. What is the process of writing a template?
    2. How to test to ensure that your template is error-free?
D. What you need to get started
    1. Eg github acct. / coding experience helpful.

#Overview of template
A. File structure
    1. Show example of the file structure with labels and text describing what they are
    2. Show how the file structure relates to the GUI
    3. Explain what kind of media goes in each folder

#The anatomy of Plate.xml ** MOST IMPORTANT
A. Define what plate.xml is
B. Show the standard structure of a template (I think standardizing this will be best even if no standard is required)
    1. Define terms here?? Such as ‘parent’ ‘parent-item’ ‘path_part’ Need a main glossary section in the page
C. Diagram showing different pieces of the Plate.xml and text explaining what they are
    1. Head
    2. Clippings
    3. Datasets
      a. Explain that unparented datasets need to be at top of template
    4. Templatesets and Pagesets
    5. Fields
    6. Items
    7. Explain how Parenting works?? Here or in relationship to GUI
D. Show how template terms relate to GUI
    1. Eg relationship between ‘name’ and ‘name_friendly’ between the fields in the GUI and what is in the template

#Anatomy of Plate-variable.xml ** SECOND MOST IMPORTANT
    1. Define what plate-variable.xml is
    2. Standard structure
      a. Define terms here??
    3. Diagram pieces of plate-var

#How to code it
    1. Recommend how to get started
    2. yes/no fields
    3. Dropdown lists
    4. plate - deep dive
    5. plate-variables deep dive
