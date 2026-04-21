Development Log – Iterative Development (Code Versions)

⸻

Version: Code – Copy 1 (Initial Prototype)

Task: Creating the basic structure of the system

In the first version of the project, I focused on building a basic static prototype using HTML. I created the core pages including the homepage, browse products page, and navigation bar. At this stage, the system was purely structural, with minimal styling and no interactivity.

The homepage included basic sections such as headings, product placeholders, and navigation links. However, there was no consistent styling or layout control.

Evaluation:
This version successfully established the foundation of the system, but lacked usability, styling, and functionality.

⸻

Version: Code – Copy 2

Task: Introducing CSS styling and layout improvements

In the second version, I introduced a central CSS file to improve the appearance of the system. I implemented a consistent colour scheme and began structuring the layout using Flexbox and basic CSS positioning.

I improved the navigation bar and introduced styled sections such as product cards and content blocks. This version made the interface more visually appealing and aligned more closely with my original wireframes.

Challenges:
Maintaining consistency across multiple pages.

Solution:
I reused CSS classes and applied consistent styling rules across all pages.

Evaluation:
This version significantly improved usability and visual design but still lacked interactivity.

⸻

Version: Code – Copy 3

Task: Expanding functionality and adding more pages

In this version, I expanded the system by adding additional pages such as the cart, checkout, login/register, and dashboards. I also improved page structure and navigation between pages.

The system now resembled a complete multi-page application, with all major sections required by the project brief included.

Evaluation:
This version demonstrated full coverage of system requirements but remained mostly static.

⸻

Version: Code – Copy 4

Task: Adding JavaScript interactivity

In this iteration, I introduced JavaScript to add dynamic behaviour. This included:

* Product search functionality (filtering items)
* Login/register form toggling
* Cart delivery option toggle with price updates

Challenges:
The search feature initially did not work correctly due to case sensitivity.

Solution:
I standardised text comparison by converting values to uppercase.

Evaluation:
This version marked a significant improvement, transforming the system from static pages into an interactive prototype.

⸻

Version: Code – Copy 5

Task: Beginning backend development

In this version, I introduced a Python backend using Flask. This marked a major transition from a purely frontend system to a full-stack approach.

I began structuring the application using:

* Templates (HTML files)
* Static folder (CSS)
* Backend file (app.py)

Challenges:
Understanding how to connect frontend pages to backend routes.

Solution:
I organised the project using Flask conventions, allowing pages to be rendered dynamically.

Evaluation:
This version significantly increased the technical complexity of the project and demonstrated advanced development skills.

⸻

Version: Code – Copy 6 (Final Version)

Task: Database integration and advanced features

In the final version, I implemented a SQLite database (greenfield.db) to support data storage. This allowed the system to move beyond a simple prototype and towards a realistic web application.

I also refined existing features and improved system structure. Additionally, I implemented a loyalty points system, allowing users to earn rewards and receive discounts based on purchases.

Improvements over previous versions:

* Added database for persistent data
* Introduced backend logic for handling data
* Implemented loyalty rewards system
* Improved organisation of files (templates + static)

Challenges:
Ensuring all components (frontend, backend, database) worked together correctly.

Solution:
I carefully structured file organisation and tested each component individually before integrating them.

Evaluation:
This version represents the most complete and advanced implementation of the system. It demonstrates strong technical ability, including full-stack development, and meets the majority of the project requirements at a high level.

⸻

Overall Iteration Reflection

Across all versions, the system evolved from a basic static prototype into a more advanced, data-driven web application. Each iteration introduced new features and improvements, including styling, interactivity, backend integration, and database functionality.

This iterative approach allowed continuous testing and refinement, ensuring that issues were identified and resolved progressively. The final system demonstrates a clear progression in complexity, functionality, and technical skill, meeting the requirements of the project brief and exceeding expectations in several areas.