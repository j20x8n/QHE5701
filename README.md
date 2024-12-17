java cQHE5701 – Database Systems 2024 
Coursework Assignment 
 Design and Implementation of a Relational Database Application Using MYSQL 
Title: 
Submission Deadline: Sunday 15th December 2024 (23:59 China Standard Time). 
Any late submission will have penalty as per QMUL regulations.
Nursing House Record System 
Introduction 
You have been contracted to design and develop a database system for a small sized nursing 
facility for senior citizens. 
This family-owned nursing facility where all the records were managed on pen and paper, yet 
it has grown to the point where this method has become unfeasible and are looking to 
professionalise the management of the operation. 
From client’s perspective, any senior resident record should store information about the 
resident’s identity, differentiated by a unique ID (for this, Chinese National ID number is used). 
The record should also include the resident’s name, their permanent address, contact phone 
number, date of birth, gender, any known allergies, and a special field to store health and carerelated
 notes about the resident. 
The system supports four primary roles for managing resident data: caregivers, nurses, 
administrative staff and guardians. 
1. Caregivers can add, modify, or delete their personal care and assistance records for residents. 
They can also view the complete care records for the residents assigned to them. 
2. Nurses have permissions to add health-related treatment records for a resident. They can also 
browse the resident’s visit history in a restricted manner, meaning they cannot view detailed 
care or medical records created by caregivers unless necessary for their responsibilities. 
 
 3. Administrative staff can view the resident’s basic identity information, such as their name, 
contact details, and room assignment. They can also monitor resident activity logs, schedule 
visits, and ensure caregivers and nurses are appropriately assigned to residents based on 
availability and needs. 
4. Guardian is the contact person of the resident in case of emergency. Guardian is responsible 
for paying the charges for the resident’s stay at the nursing house. Guardian’s data needs to be 
stored in the database including their name, address (house, street, city, postal code), contact 
number, wechat contact along with their relation with the resident is to be recorded. In some 
cases, there can be two guardians for same resident, but this is optional. Not all residents have 
two guardians. 
Additionally, a database administrator role is introduced for managing user permissions 
dynamically. This includes defining roles, assigning users to roles, and handling role 
modifications or revocations (e.g., when caregivers, nurses, or staff members are hired or leave 
the facility). 
This design ensures that resident information is securely stored and accessed according to 
specific role-based permissions while maintaining a clear separation of duties among 
caregivers, nurses, staff, and administrative staff. 
General 
You are required to design and implement this database system through data requirements 
analysis, conceptual design using concepts of the Entity-Relationship (ER) model, logical 
design using the concepts of the relational model, and implementation and testing using 
MySQL. 
The specification above details the minimal requirements, you can design above or improve 
the proposed design. For each change you are required to document the rationale for the 
improvement. Include any assumption that you made in the data modelling. 
 
Task 1 – Requirement Analysis: 
(a) Background: 
A short report about your understanding of the provided user requirement for which you are 
designing the database (DB). This includes knowledge about the scenario which you used for 
designing the DB. 
(b) Assumptions: 
Add 3 to 6 assumptions that inform your DB design. These assumptions should be relevant to 
the DB. Mention any assumptions you made for the Data Model. Different assumptions lead 
to different data model. 
 
Example: 
 A student registers for exactly one course is relevant. "a student has a name" are not relevant. 
Other relevant assumptions: 
"A booking involves a customer, a receptionist, and several rooms booked; should be 
modelled as a relationship; but we model booking as an entity and use relationships such as 
customer_makes_booking." 
 
Task 2 – Conceptual Design/ER Model: 
Create a conceptual schema for the above database system using the concepts of the EntityRelationship
 (ER) model. Explain the relationships modelled in your relational schema. 
 
Show the following design steps: 
 
(a) A textual description of the entity-relationship model including keys 
(b) Description of the entities and relationships 
(c) Explanations for cardinality and participation constraints 
 
Example: 
Complete the ER diagram by using the notation shown in the example of the Student, Course 
entities and Enrol relationship given below. (NOTE: This is only for guidance on where to 
start. It is not a required Format). 
 
Entities: 
 Student{StudentNo, fName, lName, address, gender, NIN, compID, DOB, ProgrammeTitle} 
Primary key: StudentNo 
Foreign key: ProgrammeTitle references Programme(pTitle) 
Alternate key: NIN 
Course{CourseNo, CourseTitle, Credits, FacultyID, DeptID} 
Primary key: CourseNo 
Foreign key: DeptID references Department(DeptID) 
Foreign key: FacultyID references Faculty(FacultyID) 
Alternate key: CourseTitle 
 
Relationship: 
Enrol (many-to-many relation between Student and Course) 
Enrol {StudentID, CourseID} 
Primary key (combination of two FK): StudentID + CourseID 
 Task 3 – ER Diagram: 
(a) Partial ER Diagram: 
Draw partial ER diagrams showing each entity and all its attributes. You can use any tool (not 
restricted to use MS-Visio, Draw.io, Lucid Chart or MySQL). 
Example: Entity – Person 
 
(b) Complete ER Diagram: 
Graphical representation of your ER model. Your ER diagram must make use of the building 
blocks of ER diagrams including primary key (simple or composite), alternate key, 
composite attribute, multi-valued attribute, attribute of a relationship, recursive 
relationship, 1:1 relationship, 1:m relationship and m:n relationship, among others. All 
constraints should be considered including cardinality and participation constraints. 
Example: 
ER Diagram of a Hotel Reservation System. 
 
Person 
personID 
email 
ﬁrstname lastname 
phone  
(c) Textual Description of ER: 
Provide a textual description of your ER Model. Your graphical diagram must correspond to 
the textual description. 
 
Example: 
Enrol{StudentID, CourseID, Enr代 写QHE5701、SQL
代做程序编程语言olmentDate} 
– PK (combination of two FK): StudentID + CourseID 
– when mapping the ERM to tables, we noticed that attribute EnrolmentDate makes sense 
 
Task 4 – Mapping ER to Logical Model: 
Provide mapping of the conceptual model to the logical model. Explain the main mapping 
steps. Show the logical model (tables). 
 
Example 1: 
Logical model of a small sized company that sells Droids. 
 
Source: BlueCorpSolution 
 
You can also create the logical model in MySQL. 
Example 2: 
Logical model of a retail company.  
Source: Binus 
 
You can also use the EER diagram created in MySQL instead of the designing a logical model 
separately. The EER diagram provide detailed overview of the underlying data structures, 
presenting a detailed representation of the data model including tables, columns, data types, 
indexes, and storage details. 
Example: 
EER diagram of a University Parking. 
  
Task 5 – Normalisation: 
Explain if and why your schema is in 3NF. Even if your schema is already in 3NF, construct 
an example for 2NF and 3NF to demonstrate where in your design a normalisation step 
occurred (excluding the normalisation of address, post-code -> city). 
 
Task 6 – Implement the Database 
Based on your schema, we ask you to create a minimum of 5 tables using SQL CREATE 
commands. Create the tables and relationships between tables for database application using 
MySQL. All the elements shown above in blue (Task 3) in your relational schema must be 
properly implemented. 
Remember to enforce the Referential Integrity including update rules on each of the 
relationships between tables. We expect to see an instance of Generalisation. 
 
Task 7 – Populate the Tables with Data 
Populate the tables with meaningful data. You should populate your tables with at least 10 rows 
of data per table using SQL INSERT statements. Enter sufficient data that reflect the 
relationships' structural constraints (i.e., participation constraints and cardinality ratio 
specified with ‘min..max’) and test the queries in Task 8. 
 
Task 8 – Query the Database 
Write at least 3 basic, 3 medium and 3 advanced queries using SQL and run them in your 
database and add screenshots of your queries result in the final report. 
(a) Basic queries: 
Write 3 basic but non-trivial SQL queries using WHERE, JOIN or OPERATORS (AND, OR, 
BETWEEN etc). SELECT * FROM table will not be accepted. 
Example: 
Customers who booked a room whose price is greater than 200. 
 
(b) Medium queries: 
Write 3 (only 2 if you're working in a group of 2 members) medium queries using GROUP BY, 
HAVING, and complex JOINS (self-joins, outer joins). 
Example: 
Customers who booked a comfort room and a luxury room, all rooms with the customers who 
booked them including the rooms no customer has booked.  
(c) Advanced queries: 
Write 3 (2 if you're working in a group of 2 members) advanced queries (NESTED Queries, 
SET-based conditions or AGGREGATIONS). 
Example: 
Show customers who booked more rooms than the average customer (i.e. the average number 
of rooms), all customers who booked mostly luxury rooms (e.g. more than 90% of the bookings 
were for luxury rooms). 
 
Task 9 - Database Application 
Develop and implement an application that will allow the database users to access and retrieve 
data from the database. The application should have a 'user friendly' graphical interface. The 
application should allow the users to perform the following: 
a) Run Use Cases for the System. 
b) View data in Tables in datasheet view. 
 
Task 10 – Considerations on Privacy and Security 
The design presented above has no specific data privacy and security requirements. You are 
requested to produce a one-page critique of the issues that can potentially become incidents. 
You should include: 
- An Identification of Sensitive data 
- Data protection measures that you would add to the design. 
- GDPR compliance. Reflect on data minimization, purpose limitation, storage 
limitation, and data subject rights (e.g., right to access, rectify, or erase personal data). 
Provide recommendations on how the system can adhere to these principles and ensure 
the lawful processing of personal data. 
 
Task 11 – Critical Evaluation 
Submit a critical assessment of your work, as well as the value of this coursework in 
understanding and using (or otherwise) the techniques and methods you learned to design and 
implement a relational database. A brief statement of ‘individual contributions’ must be 
included in here from each member of the group. This section should not be longer than A4 
page. 
 
Task 12 – Viva: 
You are required to demonstrate your database application through a MS Teams meeting of 10 
minutes. Each of the group will be sent an invite to MS Teams Meeting which will be scheduled from Monday (16th December 2024) to Tuesday (17th December 2024). These sessions will be 
recorded as per QMUL regulations. Schedule will be shared in Week – 16. 
 
Final Coursework Submission: 
• Include a title page with your full name, module name, QMUL ID Number, BUPT ID 
Number, Class Number, and qmul email. 
• Use a clear and organized layout. 
• Clearly label each task (e.g., Task 1 (a), Task 1 (b), Task 2 etc.) 
• Your coursework report (pdf) should consist of all tasks (the SQL code and result as 
screenshots). This report should explain the semantics of your relational schema. 
• You must submit your SQL scripts in ONE .sql file. The SQL script MUST work 
without ANY issues on MySQL. If the script does not run, you will get at most 40% of 
the total marks. 
• Create a folder and place all your database files (coursework report (.pdf), your SQL 
scripts in a single file (.sql), database application files, and any additional file you 
created for your ER Diagram within the folder. 
• Compress this folder and rename it with your QMUL ID numbers of all group members: 
221155XXX_ 221155XXX_ 221155XXX.zip 
• Upload the compressed file on the Coursework Submission in Assessment Tab on 
QMPlus module page. 
 
Using ChatGPT or any generative AI tool is not recommended for this coursework. 
However, if you choose to use such any GenAI tool, please ensure you properly cite it in 
your report to avoid penalties related to plagiarism or academic misconduct. 
 
Marking Scheme: 
 Requirement Analysis [5 Marks] 
Conceptual Design/ER Model [5 Marks] 
ER Diagram [10 Marks] 
Mapping ER to Logical Model [10 Marks] 
Normalization [5 Marks] 
Implement the Database [10 Marks] 
Populate tables with data [5 Marks] 
Queries  Basic
 
Critical Evaluation
Good Luck!
 
         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
