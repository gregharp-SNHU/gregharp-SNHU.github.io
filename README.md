# Greg Harp — Computer Science ePortfolio

---

**Contents**
- [Professional Self-Assessment](#professional-self-assessment)
- [Code Review](#code-review)
- [Artifact Overview](#artifact-overview)
- [Enhancement One: Software Design and Engineering](#enhancement-one-software-design-and-engineering)
- [Enhancement Two: Algorithms and Data Structures](#enhancement-two-algorithms-and-data-structures)
- [Enhancement Three: Databases](#enhancement-three-databases)
- [References](#references)

---

## Professional Self-Assessment

### Background

My name is Greg Harp. I have spent more than three decades in information technology
with a focus on network engineering and architecture, working on the cutting edge of
that technology for the majority of those years alongside exceptional people from
around the world. Three years ago I decided to complete the computer science education
I had begun decades before, a decision that has deepened my understanding of the
discipline underlying the work I have done professionally throughout my career.

As I reflect on that career and this educational journey, I am reminded of the
influence that Edsger Dijkstra had upon me. I attended the University of Texas at
Austin when Dijkstra was head of the department, and his thinking shaped mine in ways
I only fully appreciated later. He is perhaps best known for the Shortest-Path First
algorithm that bears his name, which has dominated network routing and convergence
methods for decades and played a central role in my career as a network engineer and
architect (Dijkstra, 1959). He also coined the phrase "separation of concerns" in a 
1974 paper, a principle so fundamental to good design that I have applied it to both 
software and hardware design throughout my career (Dijkstra, 1974). This ePortfolio 
presents my capstone project for the SNHU Computer Science program. Through three 
enhancements I transformed a classroom Android inventory management application into 
a production-ready multi-user system, with separation of concerns as a guiding 
principle throughout.

### Collaborating in a Team Environment

Code review is among the most important collaborative practices in software
development. It surfaces defects, maintains shared understanding of the codebase, and
creates an environment where quality is a team responsibility rather than an individual
one. Best practices include reviewing small changes frequently, focusing on clarity and
maintainability rather than stylistic preferences, and ensuring that reviewers
understand the purpose of the code being examined before evaluating how it accomplishes
that purpose (OWASP, 2017).

For this capstone I conducted a structured code review of my CS 360 artifact covering
all three enhancement categories before beginning any implementation work. The
discipline of preparing and delivering that review -- examining existing code
critically, documenting planned improvements, and communicating those plans clearly --
mirrors the practices I employ professionally with my peers and employees. I have 
consistently emphasized the value of clear in-code documentation and logical modularity 
not because they make my own work easier, but because they make it possible for others 
to understand, maintain, and extend that work. The constant classes I introduced in 
Enhancement One (`DbKeys`, `Roles`, and `Prefs`) are a direct expression of this value.
They eliminate common and subtle bugs caused by repeated string literals and make the 
codebase easier for any developer to navigate.

### Communicating with Stakeholders

A theme of my career has been the need to communicate technical concepts clearly to
audiences with varying levels of technical depth, from network and software engineers
to non-technical business executives. The ability to adapt both the content and the
register of a technical explanation to its intended audience is a skill I have
developed over decades and consider essential.

This capstone has given me an opportunity to demonstrate that skill in written and 
verbal communications. The code review video demonstrates my ability to communicate 
planned enhancements to a technical peer audience. The enhancement narratives explain 
specific implementation decisions and their trade-offs in detail appropriate for a 
technical evaluator. This self-assessment is written for a broader professional 
audience. The ePortfolio as a whole is structured to allow any visitor (from an 
experienced software engineer to someone with a non-technical background) to navigate 
directly to the content most relevant to them and understand what they find there.

### Data Structures and Algorithms

Algorithmic thinking has been central to my personal and professional work far longer
than it has been a formal part of my education. Network engineers use algorithms
constantly. Routing protocols such as OSPF and IS-IS are direct implementations of
Dijkstra's Shortest-Path First algorithm, and effective network troubleshooting
requires the same kind of structured decomposition and complexity analysis that
algorithm design demands. Good network engineers must think algorithmically.

This capstone gave me the opportunity to apply that thinking explicitly in software.
The skills I demonstrated include selecting algorithms appropriate to the problem,
justifying those selections with time and space complexity analysis, designing
multi-key comparators with deterministic behavior, and structuring code to be
independently testable. I also made deliberate architectural trade-offs such as 
choosing in-memory filtering over database queries to demonstrate algorithm mastery 
and to preserve separation of concerns across the data layer boundary. The value of 
that decision was confirmed when a subsequent enhancement replaced the entire data 
layer without requiring any changes to the filtering and sorting code.

### Software Engineering and Databases

My career has given me a practical education in what separates software that survives
from software that doesn't. Systems that are designed for change, that separate their
concerns cleanly, and that treat security as a constraint rather than an afterthought
tend to outlast the ones that don't. This capstone gave me the opportunity to
demonstrate those principles in code.

The skills I applied include cloud service integration, secure authentication and
authorization design, role-based access control, real-time data synchronization, and
resource lifecycle management. I also demonstrated the ability to migrate a data layer
from local SQL storage to a cloud-hosted NoSQL document store while preserving the
architecture above it -- a skill directly relevant to modern application development
where the underlying data platform is frequently subject to change. The architectural
discipline required to accomplish that cleanly is the same discipline I developed
building infrastructure that had to scale from hundreds of thousands to tens of
millions of users without being redesigned from scratch.

### Security

Security by design is not a feature to add after the fact. It is a constraint that
should shape decisions from the beginning. The zero-trust security model formalizes
this idea, replacing the historically dominant perimeter model (which assumed that
users and systems inside a security boundary could be trusted) with the principle that
no user, device, or system is trusted by default regardless of location, and that
access is granted only after explicit verification of identity and authorization for
each resource (Rose et al., 2020). This approach shifts security from a boundary that
can be breached to an inherent property of the system itself.

This principle guided my enhancement work throughout. Firebase Authentication provides
cryptographically secure credential management with no plaintext storage. Role
assignments are stored in Firestore and verified at the application layer before any
privileged operation is permitted. Firestore security rules enforce access controls at
the database layer independently of the application, ensuring that authenticated
credentials alone are not sufficient to read or write inventory data. A role assignment
is also required. This defense-in-depth approach means that a compromise at one layer
does not automatically grant access at another.

### Portfolio Summary

The three enhancements in this portfolio address a single artifact across all three
categories, each building on the work that preceded it. Enhancement One established
the foundation of a secure, multi-user identity system. Enhancement Two added
filtering and sorting capabilities whose architecture was explicitly designed to be
independent of the data layer. Enhancement Three completed the migration of the data
layer to the cloud. The result is an application that began as a standalone classroom 
project with local storage and plaintext credentials and ended as a cloud-hosted,
role-controlled, real-time multi-user system with a tested and documented algorithmic 
layer.

The skills demonstrated here -- secure authentication and authorization, cloud
integration, algorithm design with time complexity analysis, separation of concerns,
defensive coding, and clear technical communication -- are the foundation of
reliable, maintainable, and secure systems. These are essential skills that the
field of software engineering demands.

## References

Dijkstra, E. W. (1959). A note on two problems in connexion with graphs. *Numerische
Mathematik, 1*(1), 269--271. https://doi.org/10.1007/BF01386390

Dijkstra, E. W. (1974). *On the role of scientific thought* (EWD447). E. W. Dijkstra
Archive, University of Texas at Austin.
https://www.cs.utexas.edu/~EWD/transcriptions/EWD04xx/EWD447.html

OWASP. (2017). *OWASP Code Review Guide* (Version 2.0). https://owasp.org

Rose, S., Borchert, O., Mitchell, S., & Connelly, S. (2020). *Zero trust architecture*
(NIST Special Publication 800-207). National Institute of Standards and Technology.
https://doi.org/10.6028/NIST.SP.800-207

[↑ Top](#greg-harp--computer-science-eportfolio)

## Code Review

The embedded video comprises a code review of my original CS 360 project which serves 
as the artifact for all three enhancement categories in this capstone project. The 
review covers the existing functionality, identifies areas for improvement, and outlines 
the planned enhancements for software design and engineering, algorithms and data structures, 
and databases.

<iframe width="800" height="450" src="https://www.youtube.com/embed/i5u14bmPsuk" frameborder="0" allowfullscreen></iframe>

[↑ Top](#greg-harp--computer-science-eportfolio)

## Artifact Overview

The code for the original CS-360 project is recorded here as a branch called 
[`baseline`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/tree/baseline).

Through three enhancements, I have transformed it into something closer to a production application. In a demonstration of good 
software design and engineering, I have replaced the local credential storage with Firebase Authentication and implemented 
role-based access control (RBAC). In an application of the principles of algorithms and data structures, I have implemented 
search, filter, and sort features using memory- and processor-efficient algorithms evaluated for time complexity as well as 
reliability, maintainability, and security. Finally, I have moved the inventory database from local storage to the cloud, 
Firebase Firestore specifically, making the application finally truly multi-user in nature.

The following sections contain detailed narrative and key examples from each enhancement.

[↑ Top](#greg-harp--computer-science-eportfolio)

## Enhancement One: Software Design and Engineering

The original authentication system stored user credentials in plaintext in a local database and gave all users the same access
despite assignment of different roles. The first enhancement I implemented was the replacement of the local SQLite credential 
storage with Firebase Authentication, a cloud-based identity management service. This service handles secure credential storage, 
login, and password reset. 
Additionally, user profile data including assigned roles and stored phone numbers was moved to Firebase Firestore. The use 
of Firebase Authentication also enabled me to add a forgot password function with minimal additional code, as Firebase 
handles the messaging and reset process directly. These changes are key to transforming the application into a truly multi-user 
system.

Another key enhancement was role-based access control across three roles: User, Manager, and Owner. Users can view and 
manage inventory. Managers can do this as well as view inventory reports. Owners have these privileges plus the ability 
to manage other users, including changing roles and deleting accounts. All new accounts are created with basic User access 
only and must be elevated by an Owner.

I also centralized string literals used throughout the code into dedicated constant classes
(`DbKeys`, `Roles`, and `Prefs`) to ensure consistency and eliminate a class of bug where
typos in repeated strings produce unexpected behavior. Finally, I removed the old SQLite user
database implementation entirely, including `User.java` and `UserDao.java`.

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
[`enhancement_1_sde`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/tree/enhancement_1_sde) 
branch ([compare to baseline](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/compare/baseline...enhancement_1_sde)).

The written narrative is available for download as a
[PDF](https://github.com/gregharp-SNHU/gregharp-SNHU.github.io/blob/main/Narrative/CS-499_Enhancement_1_SDE_Narrative_Greg_Harp.pdf) or
[Word document](https://github.com/gregharp-SNHU/gregharp-SNHU.github.io/blob/main/Narrative/CS-499_Enhancement_1_SDE_Narrative_Greg_Harp.docx).

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

[↑ Top](#greg-harp--computer-science-eportfolio)

## Enhancement Two: Algorithms and Data Structures

The original application had no ability to search, filter, or sort items in the inventory or reports activities. Users 
were presented the full inventory list in a fixed alphabetical order with no way to locate specific items or limit the 
view. In professional use, the usability of the application would diminish as the size of the inventory increases.

The primary enhancement is the new `InventoryFilter` utility class, which contains all filtering and sorting logic as 
static methods operating on lists of items in memory. I made the deliberate design decision to perform filtering and 
sorting in application code rather than through database queries in order to demonstrate mastery of these algorithms. 
Following the philosophy of separation of concerns, keeping the filtering and sorting code separate from the database 
layer ensured that no rewrites would be required during the migration to Firebase Cloud Firestore in Enhancement Three.

I implemented three filtering capabilities: a real-time case-insensitive text search, a stock status filter with an 
adjustable low stock threshold, and a minimum/maximum quantity selection. The results of the text search are reflected 
immediately in the inventory list as partial matches occur with each keypress. The stock status filter allows users to 
view items according to four different stock levels: all items, in-stock-only, low stock, and out of stock. The 
editable threshold value is stored in `SharedPreferences` on the device to persist across runs.

I implemented sorting options providing the user with case-insensitive ascending and descending alphabetical order as
well as ascending and descending item quantity. Rather than writing a custom sort, I chose to build the appropriate 
comparator based upon user selection and feed it to the standard library Timsort implementation. Timsort is a hybrid 
merge sort and insertion sort that achieves `O(n log n)` in the average and worst case, and as fast as `O(n)` when the 
list is already partially sorted. I took special care with the comparators to ensure stable results. For example, 
when sorting by item quantity, collisions are likely so I used item names as a tie-breaker with a deterministic result.
This promotes a stable user interface where items aren't shifting in some arbitrary order.

All filters and sorting are combined into a single `processAll()` method which applies the specified filter pipeline 
and then sorts the result. Since each filter stage is `O(n)` and the sort is `O(n log n)`, the overall complexity is 
`O(n log n)`, dominated by the sort step. All methods within the `InventoryFilter` class return new lists without 
modifying the input, which is important for safe interaction with LiveData.

Additionally, I implemented unit tests for the `InventoryFilter` class using JUnit. Because this class is pure Java 
with no Android dependencies, the tests run locally on the development machine without requiring the emulator. This 
test suite covers null and empty cases, name filtering, quantity range filtering, sorting, and combined integration 
of the full filtering and sorting pipeline.

This enhancement demonstrates the ability to design computing solutions using algorithmic principles, the application 
of time complexity analysis, selection of appropriate algorithms, and evaluation of design trade-offs. The separation 
of the filtering and sorting logic into a pure utility class with full unit test coverage demonstrates adherence to 
well-established software engineering best practices. Making settings such as the low stock threshold both configurable 
by the user and persistent across application runs demonstrates recognition and capability to deliver features that 
bring value to end users.

This enhancement addresses Course Outcomes 3 and 4. The filtering algorithms, the selection of Timsort, the time 
complexity analysis, the design of multi-key comparators, and the trade-off decisions all demonstrate my ability to 
design solutions using algorithmic thinking and to evaluate the trade-offs involved in various design choices (Outcome 3). 
The separation into a testable utility class and the user-configurable, persistent settings demonstrate well-founded 
techniques that deliver value (Outcome 4).

The complete code for this enhancement is available in the 
[`enhancement_2_dsa`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/tree/enhancement_2_dsa) 
branch ([compare to baseline](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/compare/baseline...enhancement_2_dsa)).

The written narrative is available for download as a
[PDF](https://github.com/gregharp-SNHU/gregharp-SNHU.github.io/blob/main/Narrative/CS-499_Enhancement_2_DSA_Narrative_Greg_Harp.pdf) or
[Word document](https://github.com/gregharp-SNHU/gregharp-SNHU.github.io/blob/main/Narrative/CS-499_Enhancement_2_DSA_Narrative_Greg_Harp.docx).

### Key Files

The following files are central to this enhancement. Links open the file in the GitHub repository.

**Filtering and sorting logic**
- [`InventoryFilter.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_2_dsa/app/src/main/java/com/mobile2app/gregharpinventory/util/InventoryFilter.java)

**Unit tests**
- [`InventoryFilterTest.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_2_dsa/app/src/test/java/com/mobile2app/gregharpinventory/InventoryFilterTest.java)

**Updated activities with filter/sort UI**
- [`InventoryActivity.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_2_dsa/app/src/main/java/com/mobile2app/gregharpinventory/ui/InventoryActivity.java)
- [`ReportsActivity.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_2_dsa/app/src/main/java/com/mobile2app/gregharpinventory/ui/ReportsActivity.java)

**Layouts (portrait and landscape)**
- [`activity_inventory.xml`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_2_dsa/app/src/main/res/layout/activity_inventory.xml)
- [`activity_inventory.xml (land)`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_2_dsa/app/src/main/res/layout-land/activity_inventory.xml)

[↑ Top](#greg-harp--computer-science-eportfolio)

## Enhancement Three: Databases

The inventory item data was the last remaining component of the application still stored in a local SQLite database 
managed via Room. While the authentication and user profile data were already cloud-hosted, the inventory itself 
remained on the device and thus inaccessible to other users on other devices. Completing the migration of inventory 
data to Firebase Cloud Firestore closed the final gap in transforming this application from a single-user prototype 
into a true multi-user system.

The primary enhancement is the migration of the inventory data layer from Room/SQLite to Firebase Cloud Firestore. 
This required changes across multiple layers of the application. The most significant change was a complete rewrite 
of `ItemRepository`, which previously used Room's data access object pattern with a background thread executor. The 
new implementation attaches a real-time Firestore snapshot listener to the items collection on construction, wraps 
the results in a `MutableLiveData` list, and posts updates to observers whenever the cloud data changes. This approach 
preserves the `LiveData` interface used by `ItemViewModel` and the user interface layer, so those components required 
minimal changes. The snapshot listener is detached in the `onCleared()` method of both `ItemViewModel` and 
`ReportsViewModel` to prevent memory leaks when those ViewModels are destroyed.

I rebuilt the report query methods, which previously executed SQL queries in `ItemDao`, as client-side transformations 
of the base snapshot using `Transformations.map()`. Each report type (all items, low stock, and out of stock) is 
derived from the same live data stream rather than requiring separate database queries. Firestore uses a String type 
document ID rather than the long integer which was auto-generated by SQLite. This difference drove changes throughout 
the `InventoryItem`, `ReportRow`, `ItemRepository`, `ItemViewModel`, `EditItemActivity`, `InventoryActivity`, 
`InventoryAdapter`, and `ReportAdapter` classes.

After completing this migration, I removed the last vestiges of the old SQLite item database implementation by deleting 
the `AppDatabase` and `ItemDao` classes entirely from the project.

I also updated the Firestore security rules to add an items collection with appropriate read and write controls. 
Without these rules, Firebase would have allowed anyone with an authenticated user account to alter the inventory 
database even without an appropriate role assignment within the application. The rules require that a user be both 
authenticated and have a role assignment in order to read and write to the inventory database.

Finally, the sample inventory data seeding feature in `AccountActivity` required a redesign. The original 
implementation used a `SharedPreferences` flag to track whether sample data had been loaded, which worked when the 
database lived on the device but no longer works in a multi-user, multi-device implementation. I replaced the 
preferences-based guard with a direct check of the cloud-based inventory database. If at least one item appears 
in the collection, the database has been seeded and the button is disabled. This logic ensures that the source of 
truth is always the cloud database and not local storage.

This enhancement demonstrates the ability to migrate a data layer from local SQL storage to a cloud-based NoSQL 
document store while preserving the existing application architecture above that layer, understanding and 
implementation of real-time data synchronization in a multi-user environment, awareness of security considerations 
at the database layer including role-based access controls, the ability to recognize and correct design assumptions 
that become invalid when the underlying data architecture changes, and attention to resource management to prevent 
memory leaks.

This enhancement addresses Course Outcomes 1, 4, and 5. With the inventory data now stored in Firebase Cloud 
Firestore, the application is fully multi-user. Authenticated users on separate devices can read and update a 
shared inventory simultaneously, and changes propagate in real time (Outcome 1). The migration to Firebase Cloud 
Firestore demonstrates the use of modern, industry-standard cloud database technology, and the use of snapshot 
listeners, `Transformations.map()` for reactive data derivation, and `ListenerRegistration` for resource clean-up 
demonstrates best practices in Android development (Outcome 4). The Firestore security rules for the items collection 
reflect a deliberate security mindset — the check for a user role assignment anticipates cases where credentials 
exist but a role has not been assigned or granted (Outcome 5).

The prediction I made in Enhancement Two that the `InventoryFilter` class would survive the migration to Firebase Cloud Firestore without changes proved correct. The deliberate design choice to keep filtering and sorting logic separate from the data source paid off directly during this milestone.

The complete code for this enhancement is available in the 
[`enhancement_3_dbs`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/tree/enhancement_3_dbs) 
branch ([compare to baseline](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/compare/baseline...enhancement_3_dbs)).

The written narrative is available for download as a 
[PDF](https://github.com/gregharp-SNHU/gregharp-SNHU.github.io/blob/main/Narrative/CS-499_Enhancement_3_DBS_Narrative_Greg_Harp.pdf) or
[Word document](https://github.com/gregharp-SNHU/gregharp-SNHU.github.io/blob/main/Narrative/CS-499_Enhancement_3_DBS_Narrative_Greg_Harp.docx).

### Key Files

The following files are central to this enhancement. Links open the file in the GitHub repository.

**Migrated repository layer**
- [`ItemRepository.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_3_dbs/app/src/main/java/com/mobile2app/gregharpinventory/data/ItemRepository.java)

**Updated ViewModels with listener cleanup**
- [`ItemViewModel.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_3_dbs/app/src/main/java/com/mobile2app/gregharpinventory/viewmodel/ItemViewModel.java)
- [`ReportsViewModel.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_3_dbs/app/src/main/java/com/mobile2app/gregharpinventory/viewmodel/ReportsViewModel.java)

**Model with String ID**
- [`InventoryItem.java`](https://github.com/gregharp-SNHU/CS-499-GregHarpInventory-Android/blob/enhancement_3_dbs/app/src/main/java/com/mobile2app/gregharpinventory/model/InventoryItem.java)

[↑ Top](#greg-harp--computer-science-eportfolio)