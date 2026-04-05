# Greg Harp — Computer Science ePortfolio

## Introduction

My name is Greg Harp. I have enjoyed a career of more than three decades in information technology with a focus in network
engineering and architecture. I have been fortunate enough to work on the cutting edge of network technology for the majority
of those years, and even more fortunate to work with incredible people from all over the world who bring their unique thoughts
and ideas to the evolution of that technology. 

Three years ago I decided to complete the computer science education that I began decades before. As I reflect upon my career 
and my educational journey, I recognize the influence that Edsger Dijkstra had upon me. Dr. Dijkstra is perhaps most famous for
the Shortest-Path First algorithm that is more commonly called "Dijkstra's Algorithm" which has played a large part in my 
career as a network engineer and architect. Dijkstra also authored a paper in 1974 entitled *On the role of scientific thought* 
in which he coined the phrase "separation of concerns" (Dijkstra, 1974). The separation of concerns is fundamentally important
to the design of both software and hardware such as that used to build computer networks. This structured approach leads to
systems and software that are more reliable, more maintainable, and as has become increasingly important over time, more secure.

This ePortfolio presents my capstone project for the SNHU Computer Science program. I selected my CS 360 final project, an 
Android inventory management application, as the artifact for all three enhancement categories. The original application was 
a functional classroom project with a local database and basic authentication. 

The code for the original CS-360 project is recorded here as a branch called 
[`baseline`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/tree/baseline).

Through three enhancements, I have transformed it into something closer to a production application. In a demonstration of good 
software design and engineering, I have replaced the local credential storage with Firebase Authentication and implemented 
role-based access control (RBAC). In an application of the principles of algorithms and data structures, I have implemented 
search, filter, and sort features using memory- and processor-efficient algorithms evaluated for time complexity as well as 
reliability, maintainability, and security. Finally, I have moved the inventory database from local storage to the cloud, 
Firebase Firestore specifically, making the application finally truly multi-user in nature.

## Code Review

The embedded video comprises a code review of my original CS 360 project which serves as the artifact for all three 
enhancement categories in this capstone project. The review covers the existing functionality, identifies areas for 
improvement, and outlines the planned enhancements for software design and engineering, algorithms and data structures, 
and databases.

<iframe width="800" height="450" src="https://www.youtube.com/embed/i5u14bmPsuk" frameborder="0" allowfullscreen></iframe>

## Enhancement One: Software Design and Engineering

My selected artifact is the inventory management application I originally developed for CS-360 in the summer of 2025. 
The application allows users to manage an inventory of items, with features for adding, editing, and deleting items, adjusting 
quantities, viewing reports, and receiving SMS alerts when items reach zero stock.

I selected this artifact because it provides a solid foundation for enhancement into a more professional, production application. 
The original authentication system stored user credentials in plaintext in a local database and gave all users the same access
despite assignment of different roles.

The first enhancement I implemented was the replacement of the local SQLite credential storage with Firebase Authentication, 
a cloud-based identity management service. This service handles secure credential storage, login, and password reset. 
Additionally, user profile data including assigned roles and stored phone numbers was moved to Firebase Firestore. The use 
of Firebase Authentication also enabled me to add a forgot password function with minimal additional code, as Firebase 
handles the messaging and reset process directly. These changes are key to transforming the application into a truly multi-user 
system.

Another key enhancement was role-based access control across three roles: User, Manager, and Owner. Users can view and 
manage inventory. Managers can do this as well as view inventory reports. Owners have these privileges plus the ability 
to manage other users, including changing roles and deleting accounts. All new accounts are created with basic User access 
only and must be elevated by an Owner.

I also centralized string literals used throughout the code into dedicated constant classes — `DbKeys`, `Roles`, and 
`Prefs` — to ensure consistency and eliminate a class of bug where typos in repeated strings produce unexpected behavior. 
Finally, I removed the old SQLite user database implementation entirely, including `User.java` and `UserDao.java`. No 
stranded code or abandoned hooks remain from the previous implementation.

This enhancement demonstrates the ability to identify and implement requirements consistent with real-world multi-user 
applications, the recognition of and implementation of secure authentication and role-based access control, integration 
of cloud technologies into a previously standalone application, and implementation of software design best practices 
including separation of concerns, centralization of constants, and consistent error handling.

This enhancement addresses Course Outcomes 1, 4, and 5. The application now supports multiple authenticated users with 
different roles — a necessary foundation for the multi-user cloud system completed in Enhancement Three. The integration 
of Firebase Authentication demonstrates the use of modern, industry-standard cloud services rather than a custom credential 
management solution. And the replacement of plaintext password storage with Firebase Authentication, combined with role-based 
access control, directly addresses the security mindset outcome.

The most significant learning experience in this enhancement was working with Firebase's asynchronous callback model, 
which required significant restructuring of every activity that touches authentication or user data compared to the original 
SQLite and Executors approach. I also encountered a real-world security lesson when I briefly exposed an API key by making the 
repository public before adding `google-services.json` to `.gitignore`. I was able to remove the file, update the gitignore 
rules, and regenerate the key promptly.

The complete code for this enhancement is available in the 
[`enhancement_1_sde`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/tree/enhancement_1_sde) branch.


### Key Files

The following files are central to this enhancement. Links open the file in the GitHub repository.

**Authentication and account management**
- [`LoginActivity.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_1_sde/app/src/main/java/com/mobile2app/gregharpinventory/ui/LoginActivity.java)
- [`CreateAccountActivity.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_1_sde/app/src/main/java/com/mobile2app/gregharpinventory/ui/CreateAccountActivity.java)

**Role-based access control**
- [`ManageUsersActivity.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_1_sde/app/src/main/java/com/mobile2app/gregharpinventory/ui/ManageUsersActivity.java)
- [`Roles.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_1_sde/app/src/main/java/com/mobile2app/gregharpinventory/model/Roles.java)

**Centralized constants**
- [`DbKeys.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_1_sde/app/src/main/java/com/mobile2app/gregharpinventory/model/DbKeys.java)
- [`Prefs.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_1_sde/app/src/main/java/com/mobile2app/gregharpinventory/model/Prefs.java)

## Enhancement Two: Algorithms and Data Structures
*(Coming soon)*

## Enhancement Three: Databases
*(Coming soon)*

## Professional Self-Assessment
*(Coming in Module Seven)*

## References

Dijkstra, E. W. (1974). *On the role of scientific thought* (EWD447). E. W. Dijkstra Archive, University of Texas at Austin. https://www.cs.utexas.edu/~EWD/transcriptions/EWD04xx/EWD447.html
