MVC 





Model-View-Controller architecture : 

A fundamental design pattern in web development. Moving from static to dynamic websites requires a structured approach to managing data, user interfaces, and program logic.



The Need for Architecture

Static vs. Dynamic: While HTML and CSS are sufficient for designing static pages, they cannot perform calculations or interact with databases. To build dynamic applications, developers must combine frontend design with backend languages (like Java, Python, or PHP) and database systems (like Oracle or MySQL).



Division of Labor: 

A professional web application separates responsibilities. Frontend developers focus on design, programmers handle logic, and database administrators manage data storage.





Understanding MVC Components

* View : This is the user-facing part of the website. It is created using HTML and CSS to display information and collect user input.
* Controller : This acts as the bridge. It receives inputs from the View, processes the logic, and determines what data needs to be retrieved or saved. Technologies like Java (JSP) or Python (Django) operate here.
* Model : This represents the database layer where data is stored and managed (e.g., MySQL, MongoDB). It interacts with the Controller to fetch or update records.





How it Works:

Although the acronym is MVC, the process typically starts with the View, which sends requests to the Controller, which then interacts with the Model if necessary. 

## Remember MVC as input, decision, and data

The **View** presents information and captures interaction; the **Controller** handles the request and coordinates a use case; the **Model** represents domain data and rules. Keep rendering out of persistence and database mechanics out of the view. The exact naming varies by framework, but separation of concerns is the useful idea.

Request flow: `user action → controller → model/domain operation → controller chooses result → view`. Validate input and authorize the operation before changing protected data; hiding a button in the view is not access control.

**Recall check:** A calculation rule is copied into three controllers. Which layer should own the shared rule? The domain/model layer or a dedicated service used by those controllers.













