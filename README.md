START

DISPLAY "Welcome to Greenfield Local Hub"
DISPLAY "1. Register"
DISPLAY "2. Login"
DISPLAY "3. Exit"

INPUT userChoice

IF userChoice = 1 THEN

    DISPLAY "Enter Name"
    INPUT name

    DISPLAY "Enter Email"
    INPUT email

    DISPLAY "Enter Password"
    INPUT password

    IF email already exists in database THEN
        DISPLAY "Account already exists"
    ELSE
        HASH password
        CREATE new user record
        STORE name, email, hashed password
        SET loyaltyPoints = 0
        DISPLAY "Account created successfully"
    ENDIF

ENDIF


IF userChoice = 2 THEN

    DISPLAY "Enter Email"
    INPUT email

    DISPLAY "Enter Password"
    INPUT password

    RETRIEVE user from database

    IF user exists AND password is correct THEN

        DISPLAY "Login successful"

        DISPLAY "Select Role"
        DISPLAY "1. Customer"
        DISPLAY "2. Producer"

        INPUT roleChoice

        IF roleChoice = 1 THEN

            REPEAT

                DISPLAY "Customer Menu"
                DISPLAY "1. Browse Products"
                DISPLAY "2. View Previous Orders"
                DISPLAY "3. Track Shipments"
                DISPLAY "4. View Loyalty Points"
                DISPLAY "5. Logout"

                INPUT customerChoice

                IF customerChoice = 1 THEN

                    RETRIEVE active products from database
                    DISPLAY product list

                    DISPLAY "Select product ID"
                    INPUT productID

                    RETRIEVE product details

                    DISPLAY product information
                    DISPLAY "Enter quantity"

                    INPUT quantity

                    IF quantity <= product.stockLevel THEN

                        totalPrice = quantity * product.price

                        DISPLAY "Total Price: ", totalPrice
                        DISPLAY "Confirm order (YES/NO)"

                        INPUT confirm

                        IF confirm = YES THEN

                            CREATE order record
                            STORE userID, productID, quantity, totalPrice

                            UPDATE product stockLevel
                            stockLevel = stockLevel - quantity

                            ADD loyaltyPoints = totalPrice * 10

                            DISPLAY "Order placed successfully"

                        ELSE

                            DISPLAY "Order cancelled"

                        ENDIF

                    ELSE

                        DISPLAY "Not enough stock available"

                    ENDIF

                ENDIF


                IF customerChoice = 2 THEN

                    RETRIEVE all orders where userID = current user
                    DISPLAY order history

                ENDIF


                IF customerChoice = 3 THEN

                    RETRIEVE shipment status
                    DISPLAY tracking information

                ENDIF


                IF customerChoice = 4 THEN

                    DISPLAY loyaltyPoints

                ENDIF

            UNTIL customerChoice = 5

        ENDIF


        IF roleChoice = 2 THEN

            REPEAT

                DISPLAY "Producer Dashboard"
                DISPLAY "1. Add Product"
                DISPLAY "2. Edit Product"
                DISPLAY "3. Update Stock"
                DISPLAY "4. View Orders"
                DISPLAY "5. Logout"

                INPUT producerChoice

                IF producerChoice = 1 THEN

                    DISPLAY "Enter Product Name"
                    INPUT productName

                    DISPLAY "Enter Description"
                    INPUT description

                    DISPLAY "Enter Price"
                    INPUT price

                    DISPLAY "Enter Stock Level"
                    INPUT stock

                    CREATE new product record
                    STORE productName, description, price, stock

                    DISPLAY "Product added successfully"

                ENDIF


                IF producerChoice = 2 THEN

                    DISPLAY "Enter Product ID to edit"
                    INPUT productID

                    DISPLAY "Enter new product details"
                    INPUT newDetails

                    UPDATE product in database

                    DISPLAY "Product updated"

                ENDIF


                IF producerChoice = 3 THEN

                    DISPLAY "Enter Product ID"
                    INPUT productID

                    DISPLAY "Enter new stock level"
                    INPUT stockLevel

                    UPDATE product stockLevel

                    DISPLAY "Stock updated"

                ENDIF


                IF producerChoice = 4 THEN

                    RETRIEVE orders related to producer products
                    DISPLAY order list

                ENDIF

            UNTIL producerChoice = 5

        ENDIF

    ELSE

        DISPLAY "Invalid login credentials"

    ENDIF

ENDIF


IF userChoice = 3 THEN
    DISPLAY "Goodbye"
ENDIF

END




Test Plan:
Date of Test
Component to be Tested
Type of Test to be Carried Out
Prerequisites and Dependencies
10/12/2025
Homepage
Functionality Testing – Verify that the homepage loads correctly and navigation links (Browse Products, Producers, Loyalty Rewards, Login/Register) redirect to the correct pages.  Usability Testing – Test whether users can easily understand the layout and navigate to key features within a short time.  Compatibility Testing – Ensure the homepage displays correctly across browsers such as Chrome, Firefox, Safari and Edge and across desktop, tablet and mobile devices.  Performance Testing – Measure page load speed and determine how many users can access the homepage simultaneously before performance degrades.  Accessibility Testing – Ensure the page works with screen readers, keyboard navigation and includes proper semantic HTML for accessibility.  Load Testing – Simulate large numbers of users accessing the homepage to test server capacity.  Beta Testing – Provide the homepage to a limited group of real users to gather feedback before final release.
Prerequisites – Homepage layout must be fully implemented including navigation menus and links to other pages. Web hosting environment and domain configuration must be active.  Dependencies – Depends on the web server, hosting platform and content delivery network (CDN). If these services fail the homepage cannot be accessed.
10/12/2025
Product Browsing Page
Functionality Testing – Verify products are correctly retrieved from the database and displayed with correct names, prices and images.  Usability Testing – Check that users can easily search and filter products using categories or keywords.  Interface Testing – Ensure filters, search bars and pagination controls function correctly.  Database Testing – Confirm the correct product data is retrieved and displayed from the database.  Performance Testing – Test loading times when displaying large numbers of products.  Compatibility Testing – Confirm layout works across browsers and different screen resolutions.  Accessibility Testing – Ensure product descriptions and images contain alt text and are readable by assistive technologies.  Boundary Testing – Test search with very long queries or empty inputs.
Prerequisites – Product data must be populated in the database and API/database connections must be active.  Dependencies – Depends on database availability and image hosting services that store product images.
10/12/2025
Product Detail Page
Functionality Testing – Ensure product details such as name, description, price and stock availability display correctly.  Usability Testing – Verify users can clearly identify the product and locate the Add to Cart button easily.  Interface Testing – Ensure buttons such as Add to Cart and navigation links respond correctly.  Database Testing – Confirm that the product is retrieved using the correct ProductID.  Performance Testing – Ensure images and product descriptions load efficiently.  Security Testing – Prevent malicious input through URL parameters or form fields.  Accessibility Testing – Ensure images include alt text and content is compatible with assistive technology.  Black Box Testing – Test functionality from the user perspective without reviewing internal code.
Prerequisites – Product records must exist in the database and be linked correctly with product IDs.  Dependencies – Depends on the database server and media storage system hosting product images.
10/12/2025
Customer Dashboard
Functionality Testing – Ensure users can view order history, track shipments and view loyalty reward points.  Usability Testing – Check if users can easily navigate the dashboard and understand their order status.  Interface Testing – Verify that dashboard buttons, menus and links work correctly.  Database Testing – Confirm that order data and loyalty points are retrieved correctly for the logged-in user.  Security Testing – Ensure only authenticated users can access their own dashboard information.  Performance Testing – Ensure dashboard loads quickly even when multiple orders are displayed.  Integration Testing – Verify the dashboard correctly integrates with order and loyalty systems.  Accessibility Testing – Ensure dashboard navigation works with keyboard input and screen readers.
Prerequisites – Users must be registered and authenticated within the system. Order and loyalty data must exist in the database.  Dependencies – Depends on authentication systems, order databases and loyalty reward calculation modules.
10/12/2025
Producer Dashboard
Functionality Testing – Ensure producers can add new products, edit product details, update stock levels and view orders.  Usability Testing – Confirm producers can manage products efficiently through the dashboard interface.  Interface Testing – Verify forms and buttons respond correctly when creating or editing products.  Database Testing – Ensure product updates are correctly stored and reflected in the database.  Security Testing – Confirm only authorised producer accounts can access the dashboard.  Performance Testing – Test system performance when multiple producers update products simultaneously.  Integration Testing – Verify product updates are reflected immediately in the product browsing system.  Accessibility Testing – Ensure forms contain accessible labels and can be navigated using a keyboard.
Prerequisites – Producer accounts must be registered and verified within the system. Product management modules must be implemented.  Dependencies – Depends on database services storing product information and authentication systems verifying producer permissions.
10/12/2025
Login / Registration Page
Functionality Testing – Ensure users can successfully create accounts and log in using their credentials.  Usability Testing – Check that form instructions are clear and users can complete the process easily.  Interface Testing – Ensure input fields, buttons and validation messages work correctly.  Database Testing – Confirm new user accounts are stored correctly in the database.  Security Testing – Verify passwords are securely hashed and the system prevents SQL injection and brute-force login attempts.  Compatibility Testing – Ensure login forms work across different browsers and devices.  Input Validation Testing – Ensure invalid email formats or weak passwords are rejected.  Accessibility Testing – Ensure form fields have proper labels and are usable with assistive technologies.
Prerequisites – User authentication system must be implemented and connected to the database. Password encryption must be configured.  Dependencies – Depends on authentication services, database availability and security middleware protecting login endpoints.





Here are brief explanations of each diagram:

Image 1 – Entity Relationship Diagram (ERD)
This diagram shows the database structure for Greenfield Local Hub. It maps out six tables — Users, Orders, Producers, Products, OrderItems, and LoyaltyRewards — and the relationships between them. For example, a User can be linked to a Producer profile, a Producer supplies Products, and Orders contain multiple OrderItems. The LoyaltyRewards table connects back to Users to track points balances and tier status.

Image 2 – Use Case Diagram
This diagram shows what each type of user can do on the platform. It is divided into three actor roles: Customer (register, log in, browse products, place orders, track shipments, earn rewards), Producer (view orders, add products, edit product details, update stock levels), and Admin (manage users, manage producers, manage the catalogue, resolve disputes, view platform analytics).

Image 3 – Class Diagram
This diagram shows the object-oriented structure of the system. It defines the key classes — Customer, User, Producer, Order, OrderItem, Product, and LoyaltyAccount — along with their attributes and methods. For instance, the Order class holds methods like addItem() and calculateTotal(), while the LoyaltyAccount class handles accruePoints() and redeemPoints(). Customer and Producer both generalise from the base User class.

Image 4 – Data Flow Diagram (DFD) Level 0
This diagram shows how data moves through the entire Greenfield Local Hub system. The central Marketplace Database acts as the core data store, feeding information to and from five main processes: Manage Account, Process Orders, Manage Products, Update Loyalty Rewards, and Track Shipments. Customers interact with account management, order processing, loyalty rewards, and shipment tracking, while Producers interact primarily with order notifications and product management. An optional Shipping Carrier external entity feeds delivery updates back into the tracking process.
