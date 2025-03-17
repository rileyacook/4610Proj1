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
Our model's most center-based entity is our Gym entity. The Gym entity represents a unique identifier, location, phone number, and email. Since our gym table is our central point, we have multiple relationships stemming from the Gym entity: Equipment, Staff, and Members.

Equipment is directly related to Gyms, as equipment and resources are the main points of operation in gyms. A unique ID number is assigned to each piece of equipment, along with the name, status, and age of each piece. Equipment belongs to only one gym, so the gymID, which identifies the gym where the equipment is located, is present for each piece of equipment. Although equipment can only belong to one gym, a gym can have multiple pieces of equipment.

Our Staff entity tracks all non-trainer employees within our organization. To keep up with each individual staff member, we have assigned them a unique ID number. Other important information includes name, date of birth, contact information, position, salary, and the duration of their employment at Dawg Fitness. Each staff member is only able to work for one gym, hence the gymID being present for each row. Since gyms require many staff members to operate, this results in a one-to-many relationship.

Our Members table has a one-to-many relationship with Gym because our gym locations can be home to many members, but each member belongs to only one Dawg Fitness location. We assign a unique identifier to each member and track basic information such as name, personal details, contact information, and address. Although the Members table is not the central entity, it has the most relationships with other tables. There is a relationship with MembershipPlans that identifies which of our multiple membership options a member is under; a member can have one plan, while a plan can have multiple members. GymID is also present within the table to identify which gym our members are associated with. Members have the option to sign up for group classes taught by our trainers. Since members can sign up for multiple classes and classes can have multiple members, the associative entity "ClassRegistration" connects the two. Additionally, each member has their own payment information associated with their account.

Dawg Fitness offers a variety of membership plans to fit the different needs of our members. Each plan requires a unique identifier to differentiate between plans and their details. Each plan is named and assigned a monthly fee, along with a description of the accessibility offered by the plan.

Regarding the Payments entity, each payment method requires a unique identifier and tracks the associated fees a member needs to pay for gym access. Card information is recorded to finalize and authorize payments. MemberID is present within the table to associate each payment method with a single member, but members can have multiple forms of payment.

Though our trainers operate under the name "Dawg Fitness," they are a separate entity functioning independently. Like staff members, trainers have an ID number to track each individual trainer. Necessary details include name, salary, tenure at Dawg Fitness, and area of expertise. Trainers are associated with both Members and Classes in a many-to-many relationship. Trainers can have multiple one-on-one sessions with different members, recorded in the PrivateSessions table. Since trainers can teach multiple classes and each class type can have multiple trainers, we use the associative entity "TrainerSchedule."

Our Classes table is straightforward, tracking each class by its primary key, classID, the room where the class is taught, and the maximum number of members that can enroll. The Classes table is related to multiple tables: TrainerSchedule, ClassRegistration, and Surveys. Each class can have multiple Survey entries, registrations, and TrainerSchedule associations.

To track member satisfaction and their experience with classes, we created the Surveys table. Each survey requires a unique primary key, which is an ID number. To track recent trends in our classes, we include a date submitted attribute. To assess satisfaction, we implement a 1-5 rating system. The classID foreign key is present to attribute ratings and feedback to each class.

ClassRegistration is one of our three associative entities. The primary keys are also the foreign keys classID and memberID to track which classes and which members are associated with it. Another primary key, specific to ClassRegistration, registrationID, is present to allow multiple members to register for multiple classes instead of just one. We also believe naming each class is important.

TrainerSchedule is the associative entity linking trainers to the classes they teach. Similar to the ClassRegistration table, there are three primary keys, two of which originate from other tables. The trainerID is necessary to identify which trainer is teaching a class, and classID determines which class is within the trainer's schedule. The third primary key, scheduleID, ensures that trainers can teach multiple classes rather than just one.

PrivateSessions is designed for members interested in one-on-one training with a trainer. PrivateSessions is unique in that all attributes are primary keys. Two of the three primary keys originate from the Members table (memberID) and the Trainers table (trainerID), allowing each session to track which member is working with which trainer. The PrivateSessionID is a table-specific primary key that ensures multiple sessions can exist for each trainer and/or member.


Data Model:
![PNG image](https://github.com/user-attachments/assets/9ba72261-d399-4e10-9b93-deb4f82fe1d5)


Data Dictionary:

<img width="777" alt="Screenshot 2025-02-17 at 9 28 42 AM" src="https://github.com/user-attachments/assets/cd4caf58-a534-40ef-86aa-e8d2bcd25803" />

<img width="791" alt="Screenshot 2025-03-16 at 12 53 55 AM" src="https://github.com/user-attachments/assets/f57f1f94-3738-4b29-9b30-43af05c3e75b" />

<img width="789" alt="Screenshot 2025-03-16 at 12 53 32 AM" src="https://github.com/user-attachments/assets/6908f366-2d10-4501-b889-5c91069c67aa" />

<img width="793" alt="Screenshot 2025-03-16 at 9 03 28 PM" src="https://github.com/user-attachments/assets/675f1487-650a-4819-a525-851dae07337d" />

Ten Queries(6 complex 4 simple):
<img width="788" alt="Screenshot 2025-03-16 at 11 10 26 PM" src="https://github.com/user-attachments/assets/17a943f2-c139-4fce-894c-396bda7019a9" />


8. Query 8 lists each gym's ID, its location, a count of the members associated with that gym, and the sum of the payment amounts made by each member for that gym. The count of members is aliased as "TotalRevenue" and the sum of payments is aliased as "TotalRevenue". The results are ordered by total revenue in descending order.
   
<img width="1290" alt="Screenshot 2025-03-16 at 11 02 03 PM" src="https://github.com/user-attachments/assets/6174b0a3-4366-4aed-becb-f022180f85a0" />

Query 8 provides managers with valuable insights into the performance of each gym location. It allows managers to track how many members are active at each gym location and the total revenue generated for each gym. Understanding the revenue generated by each gym helps managers assess the gyms' financial health and see which locations possibly need more resources and marketing. Ordering the results by total revenue provides a quick identification of which gyms need the most investments.


9. Query 9 lists the staff members who are managers and make a salary greater than the average salary of managers. The employee's ID number, name, hire date, position, salary, and the gym they work at are displayed.

<img width="1286" alt="Screenshot 2025-03-16 at 11 02 30 PM" src="https://github.com/user-attachments/assets/6c777225-97c9-489e-9821-2e61f162faa8" />

Query 9 provides managers with valuable insights into the performance of managers across the different gym locations. It compiles a list of managers within the company and only those managers who make a salary above that of the average salary of all managers. This identifies the company's highest-earning managers and which gym locations have the highest-paid managers. Including the staff members' hire dates also allows managers to compare years of experience to pay granted. These results could help managers indicate any pay disparities among managers or different gym locations.

