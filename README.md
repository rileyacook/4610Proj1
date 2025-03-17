# 4610Proj1
4610 Group Project 1: Gym Database

Members:
1. Riley Cook https://github.com/rileyacook/4610Proj1.git
2. Sophie Naustdal https://github.com/sophienaustdal/MIST4610GroupProject.git
3. Rachel Chuan https://github.com/rachelchuan/4610Proj1
4. Chidera Nwosu
5. Coleman Vaughn

Scenario Description:

Our company, Dawg Fitness, is a large fitness enterprise with multiple gym locations across the United States, with each gym serving as the core of our operations. While all gyms operate under Dawg Fitness, each location offers tailored services to meet the diverse needs of its members. Our goal is to create a relational database that connects all relevant entities across the business. This database will manage key information such as gym details, member profiles, trainers, equipment inventory, class schedules, membership plans, payment history, and survey feedback. By leveraging this data, we aim to structure queries that provide valuable insights for improving and growing Dawg Fitness' operations.

Data Model Explanation:
Our model's most center-based entity is our Gym entity. The Gym entity represents each of Dawg Fitness's distinct gym locations across the United States. Its attributes include a unique identifier, location, phone number, and email. Since our gym table is our central point, we have multiple relationships stemming from the Gym entity: Equipment, Staff, and Members.

Equipment is directly related to Gyms, as equipment and resources are the main points of operation in gyms. A unique ID number is assigned to each piece of equipment, along with the name, status, and age of each piece. Equipment belongs to only one gym, so the gymID, which identifies the gym where the equipment is located, is present for each piece of equipment. Although equipment can only belong to one gym, a gym can have multiple pieces of equipment representing a one-to-many relationship.

Our Staff entity tracks all non-trainer employees within our organization. To keep up with each individual staff member, we have assigned them a unique ID number. Other important information includes name, date of birth, contact information, position, salary, and the duration of their employment at Dawg Fitness. Each staff member is only able to work for one gym, hence the gymID being present for each row of staff members. Since gyms require many staff members to operate, this results in a one-to-many relationship.

Our Members table has a one-to-many relationship with the Gym table because our gym locations can be home to many members, but each member belongs to only one Dawg Fitness location. We assign a unique identifier to each member and track basic information such as name, personal details, contact information, and address. Although the Members table is not the central entity, it has the most relationships with other tables. There is a relationship with MembershipPlans that identifies which of our multiple membership options a member is under; a member can have one plan, while a plan can have multiple members. GymID is also present within the table to identify which gym our members are associated with. Members have the option to sign up for group classes taught by our trainers. Since members can sign up for multiple classes and classes can have multiple members, the associative entity "ClassRegistration" connects the two. Additionally, each member has their own payment information associated with their account.

Dawg Fitness offers a variety of membership plans to fit the different needs of our members. Each plan requires a unique identifier to differentiate between plans and their details. Each plan is named and assigned a monthly fee, along with a description of the accessibility offered by the plan.

Regarding the Payments entity, each payment requires a unique identifier and tracks the associated fee a member has paid for gym access on that date. The member's payment method used is also recorded in this table along with the date they submitted the payment. MemberID is present within the table to associate each payment with a single member, but members make multiple payments, as there are monthly dues.

Though our trainers operate under the name "Dawg Fitness," they are a separate entity functioning independently. Like staff members, trainers have an ID number to track each individual trainer. Necessary details include name, salary, tenure at Dawg Fitness, area of expertise, and contact information. Trainers are associated with both Members and Classes in a many-to-many relationship. Trainers can have multiple one-on-one sessions with different members, recorded in the PrivateSessions table. Since trainers can teach multiple classes and each class type can have multiple trainers, we use the associative entity "TrainerSchedule."

Our Classes table is straightforward, tracking each class by classID, class name, the room where the class is taught, and the maximum number of members that can enroll. The Classes table is related to multiple tables: TrainerSchedule, ClassRegistration, and Surveys. Each class can have multiple Survey entries, registrations, and TrainerSchedule associations.

To track member satisfaction and their experience with classes, we created the Surveys table. Each survey requires a unique primary key, which is a survey ID number. To track recent trends in our classes, we include a date-submitted attribute. To assess satisfaction, we implement a 1-5 rating system. The classID foreign key is present to attribute ratings and feedback to each class.

ClassRegistration is one of our three associative entities. Many members can take many different classes, thus this many-to-many relationship results in an associative entity. The composite primary key is made up of classID and memberID as primary keys to track which classes and members are associated with one another. ClassID is also a foreign key in that it references the Class table, to store classes taken by members, and memberID is also a foreign key that references the Member table, to store members who take classes. RegistrationID is the final primary key, to represent each unique case of a member signing up for a class. The class name is also present in this table to easily signify which class a member has been registered for. The date of the class is also present as members can take the same class many times over various dates.

TrainerSchedule is the associative entity linking trainers to the classes they teach. Many trainers can teach many classes. Similar to the ClassRegistration table, there are three primary keys, two of which originate from other tables. The trainerID and classID make up the composite primary key to match trainers with the classes that they teach. These two attributes are also foreign keys in which trainerID references the Trainer table to identify which trainer is teaching a class, and classID references the Class table to determine which class is within the trainer's schedule. The third primary key, scheduleID, represents each unique case of a trainer teaching a class. The date of a class they teach is also represented as trainers can teach the same class many times over many dates.

PrivateSessions is designed for members interested in one-on-one training with a trainer. Many members can have many private sessions with trainers. The composite primary key originates from the Members table with memberID and the Trainers table with trainerID, allowing each session to track which member is working with which trainer. Again, these two attributes are foreign keys that reference the Members table and the Trainers table. The PrivateSessionID is a table-specific primary key that represents each unique pairing of a member and the trainer they are to have a one-on-one session with. Lastly, the date of the private session is included, as members can have many different private sessions with the same trainer.

Data Model:
<img width="645" alt="Screenshot 2025-03-16 at 12 44 34 AM" src="https://github.com/user-attachments/assets/376abce4-404e-4845-a157-602aa907a245" />


Data Dictionary:

<img width="777" alt="Screenshot 2025-02-17 at 9 28 42 AM" src="https://github.com/user-attachments/assets/cd4caf58-a534-40ef-86aa-e8d2bcd25803" />

<img width="791" alt="Screenshot 2025-03-16 at 12 53 55 AM" src="https://github.com/user-attachments/assets/f57f1f94-3738-4b29-9b30-43af05c3e75b" />

<img width="789" alt="Screenshot 2025-03-16 at 12 53 32 AM" src="https://github.com/user-attachments/assets/6908f366-2d10-4501-b889-5c91069c67aa" />

<img width="793" alt="Screenshot 2025-03-16 at 9 03 28 PM" src="https://github.com/user-attachments/assets/675f1487-650a-4819-a525-851dae07337d" />

<img width="883" alt="Screenshot 2025-03-17 at 11 27 51 AM" src="https://github.com/user-attachments/assets/8878a3a8-c4ca-47bf-aa34-527fb95e976a" />

<img width="879" alt="Screenshot 2025-03-17 at 11 28 21 AM" src="https://github.com/user-attachments/assets/201d249a-1052-4932-8ba2-54badcd59c0f" />



Ten Queries(6 complex 4 simple):
<img width="788" alt="Screenshot 2025-03-16 at 11 10 26 PM" src="https://github.com/user-attachments/assets/17a943f2-c139-4fce-894c-396bda7019a9" />
1. Query 1 lists each gym's ID, the number of pieces of equipment that are "Under Maintenance" or "Needs Repair", and equipmenth that is at least 2 years old (as of 2025- March - 14). These pieces of equipment are to be labeled as "Urgent Needs". Group each piece of "Urgent Needs" equipment into its respective gym, and order the count of "Urgent Needs" in a descending order.
<img width="727" alt="Screenshot 2025-03-17 at 9 10 21 AM" src="https://github.com/user-attachments/assets/040d8e9c-6cc8-45df-871d-06acc88676f5" />

The equipment in our gyms is the core product we offer to our members, and faulty machines require immediate attention. We specifically focus on equipment that is at least two years old to identify not only malfunctioning pieces but also those that are aging. Due to their age and inability to function properly, these items should be classified as "Urgent Needs" so that our repair team can prioritize them. Organizing these by urgency ensures that we address the most critical issues first and direct attention to the gyms that require immediate repairs.

2. Query 2 lists every trainer's ID and their last and first names. Alongside names and ID, we listed the classes they teach, labeled by the class' ID, class' room number, and class' name. Lastly, we are interested in the average survey score of that trainer and the respective class, labeled as "Average Rating". We are interested in our trainers who specialize in any "Strength" or "Endurance" area of focus. We grouped the results by the trainer's ID, the class ID and class name they are in charge of. The Average Rating of survey scores is ordered in a descending manner.

<img width="737" alt="Screenshot 2025-03-17 at 9 44 49 AM" src="https://github.com/user-attachments/assets/a10dffbd-9e89-4db4-9b4c-a700d9c5f0d4" />

The purpose of Query 2 is to track feedback for our strength trainers and endurance trainers who lead group classes. We aim to capture all relevant information about these trainers, the classes they teach, and their average survey ratings. By monitoring this data—particularly each trainer’s average score—we can assess their performance and determine if any coaching or adjustments are needed to enhance their effectiveness.

Query 3: # Get the surveyID and rating for surveys of large classes (More than 20 people) that have a higher rating than the average rating of all classes offered 

![image](https://github.com/user-attachments/assets/6d645c58-099e-426a-8c7b-2375c6733009)
![image](https://github.com/user-attachments/assets/0f846170-bd11-45de-b6ec-2c9407634975)


Query 3 lists the survey IDs of all large group classes ( More than 20 people in the class) that have an above average rating compared to all the surveys. This is important to us so we can see how people feel about our larger sized group classes in comparison to other classes we offer. This will help us make decisions about which classes aren't being affected by the large size and do not need to be reduced to a smaller capacity.


Query 5: #Retrieve the total number of members per membership plan and sort in descending order: CALL TP_Q5();  
<img width="807" alt="Screenshot 2025-03-17 at 11 32 11 AM" src="https://github.com/user-attachments/assets/7cba7469-c76b-4a49-a9be-178404da4726" />

Query 6: #Find Members Who Have Never Signed Up for a Class or a Private Session: CALL TP_Q6();  
<img width="704" alt="Screenshot 2025-03-17 at 11 40 29 AM" src="https://github.com/user-attachments/assets/c1f994ce-d061-417d-a8e7-0d02e233b5f8" />

Query 7: #Find all equipment in a specific gym: CALL TP_Q7();
<img width="456" alt="Screenshot 2025-03-17 at 11 42 19 AM" src="https://github.com/user-attachments/assets/ff74a3b9-5a39-47f3-8ab8-ae328bc468ec" />


8. Query 8 lists each gym's ID, its location, a count of the members associated with that gym, and the sum of the payment amounts made by each member for that gym. The count of members is aliased as "TotalRevenue" and the sum of payments is aliased as "TotalRevenue". The results are ordered by total revenue in ascending order.
   
<img width="1290" alt="Screenshot 2025-03-16 at 11 02 03 PM" src="https://github.com/user-attachments/assets/6174b0a3-4366-4aed-becb-f022180f85a0" />

Query 8 provides managers with valuable insights into the performance of each gym location. It allows managers to track how many members are active at each gym location and the total revenue generated for each gym. Understanding the revenue generated by each gym helps managers assess the gyms' financial health and see which locations possibly need more resources and marketing. Ordering the results by total revenue in ascending order provides a quick identification of which gyms need the most investments.


9. Query 9 lists the staff members who are managers and make a salary greater than the average salary of managers. The employee's ID number, name, hire date, position, salary, and the gym they work at are displayed.

<img width="1286" alt="Screenshot 2025-03-16 at 11 02 30 PM" src="https://github.com/user-attachments/assets/6c777225-97c9-489e-9821-2e61f162faa8" />

Query 9 provides managers with valuable insights into the performance of managers across the different gym locations. It compiles a list of managers within the company and only those managers who make a salary above that of the average salary of all managers. This identifies the company's highest-earning managers and which gym locations have the highest-paid managers. Including the staff members' hire dates also allows managers to compare years of experience to pay granted. These results could help managers indicate any pay disparities among managers or different gym locations.

