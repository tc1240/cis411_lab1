# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Tyler Collins
GitHub: tc1240(https://github.com/tc1240)
(if appropriate) Collaborators: none


# Step 0: Reviewing Architectural Patterns
See the [lecture / discussion](https://docs.google.com/presentation/d/1nUcy63FWPFYO3OJmERJpMjEtdaFtaIBbuUkpmNRVRas/edit#slide=id.g45345bd5ea_0_136) from CIS 411. You'll need to be familiar with the content from this lecture to complete this assignment.

Note: you are free to work with classmates on this assignment. _Good architecture is born out of collaboration - not reclusive mad-scientist behavior._ However, if you work with colleagues:

1. You must specifically note your collaborators by name at the top of your report.
2. You may not completely copy each others work (diagrams and descriptions, even if your solutions are identical).

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on the [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing

| Use Case #1 | |
|---|---|
| User Registers for Event | |
| A registered user wants to register for a volunteering event
1. User selects desired event and clicks the register button
2. the user is then prompted for any additional data required by the event planner
3. the user data is then passed into the event's "attendies" section of the database
4. the system then notifies the user via email that they are now registered for the event | |
| Volunteer user | |
| The user must have an account made with ServeCentral | |
| The user must be either sent a confirmation email or be presented with an error message due to unforseen error before use case ends | |

| Use Case #2 | |
|---|---|
| Organization Creates Event | |
| A registered organization wants to create an event for volunteers to register for
1. An organization user clicks the create event button
2. the "create event" screen comes up and the user fills out the required information and hits submit
3. the data is then stored in the "events" section of the database
4. the user is then given a confirmation via email 
5. the map of the database is then, by transferrence, updated with the new event| |
| Organization user | |
| The user must have an account with ServeCentral| |
| The user must be either sent a confirmation email or be presented with an error message due to unforseen error before use case ends | |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| user data table | login page | login system |
| event data table | map page | event creation |
| organization data table | event creation page | user registration |
| volunteer data table | event registration page | logout system |
|  | profile page |  |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

![Diagram](https://github.com/tc1240/cis411_lab1/blob/master/labreports/Diagram.JPG)

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
Personally I would choose to have a layered architecture so that we could create a layer that handles thirdparty services and another that handles embedding. Overall I feel that this architecture has both flexibility and scalability, however managing all the layers will be difficult if the amount of layers increases drastically.
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.
![Diagram](https://github.com/tc1240/cis411_lab1/blob/master/labreports/Diagram2.JPG)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.
I think that a blackboard architecture would be best for this kind of growth due to its multi-component architecture and its overall flexibility. 

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.
Personally I feel that this assignment would have been better had the diagrams been left out, and had step one been more about the architecture. I feel i learned a lot more about markup and submitting markup to git, however with how short step 2 and 3 were in comparison I felt that there could have been more emphasis on the architechture overall.
