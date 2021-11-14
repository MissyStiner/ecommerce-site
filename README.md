# E-commerce Back End

## Description
This challenge builds out the back end of an e-commerce site. A working Express.js API is configured to use Sequelize to interact with a MySQL database.<br>

Why it's important: Internet retail, also known as e-commerce, is the largest sector of the electronics industry, having generated an estimated US$29 trillion in 2017 (Source: United Nations Conference on Trade and Development). E-commerce platforms like Shopify and WooCommerce provide a suite of services to businesses of all sizes. Due to the prevalence of these platforms, developers should understand the fundamental architecture of e-commerce sites.

## GitHub URL
https://github.com/MissyStiner/ecommerce-site

## Walkthrough Demo Video URL
Your walkthrough video should also show the POST, PUT, and DELETE routes for products and tags being tested in Insomnia Core.

## User Story
AS A manager at an internet retail company<br>
I WANT a back end for my e-commerce website that uses the latest technologies<br>
SO THAT my company can compete with other e-commerce companies

## Acceptance Criteria
GIVEN a functional Express.js API<br>
WHEN I add my database name, MySQL username, and MySQL password to an environment variable file<br>
THEN I am able to connect to a database using Sequelize<br>
WHEN I enter schema and seed commands<br>
THEN a development database is created and is seeded with test data<br>
WHEN I enter the command to invoke the application<br>
THEN my server is started and the Sequelize models are synced to the MySQL database<br>
WHEN I open API GET routes in Insomnia Core for categories, products, or tags<br>
THEN the data for each of these routes is displayed in a formatted JSON<br>
WHEN I test API POST, PUT, and DELETE routes in Insomnia Core<br>
THEN I am able to successfully create, update, and delete data in my database

## Getting Started
You’ll need to use the MySQL2 (https://www.npmjs.com/package/mysql2) and Sequelize (https://www.npmjs.com/package/sequelize) packages to connect your Express.js API to a MySQL database and the dotenv package (https://www.npmjs.com/package/dotenv) to use environment variables to store sensitive data, like your MySQL username, password, and database name.<br>

Use the schema.sql file in the db folder to create your database using MySQL shell commands. Use environment variables to store sensitive data, like your MySQL username, password, and database name.

## Mock-Up
The following animations show examples of the application's API routes being tested in Insomnia Core.<br>

The first animation shows GET routes to return all categories, all products, and all tags being tested in Insomnia Core:
![image](./assets/13-orm-homework-demo-01.gif)

The second animation shows GET routes to return a single category, a single product, and a single tag being tested in Insomnia Core:
![image](./assets/13-orm-homework-demo-02.gif)

The final animation shows the POST, PUT, and DELETE routes for categories being tested in Insomnia Core:
![image](./assets/13-orm-homework-demo-03.gif)

## Database Models
Your database should contain the following four models, including the requirements listed for each model:

### Category
- id
- Integer
- Doesn't allow null values
- Set as primary key
- Uses auto increment
- category_name
- String
- Doesn't allow null values

### Product
- id
- Integer
- Doesn't allow null values
- Set as primary key
- Uses auto increment
- product_name
- String
- Doesn't allow null values
- price
- Decimal
- Doesn't allow null values
- Validates that the value is a decimal
- stock
- Integer
- Doesn't allow null values
- Set a default value of 10
- Validates that the value is numeric
- category_id
- Integer
- References the category model's id

### Tag
- id
- Integer
- Doesn't allow null values
- Set as primary key
- Uses auto increment
- tag_name
- String

### ProductTag
- id
- Integer
- Doesn't allow null values
- Set as primary key
- Uses auto increment
- product_id
- Integer
- References the product model's id
- tag_id
- Integer
- References the tag model's id

## Associations
You'll need to execute association methods on your Sequelize models to create the following relationships between them:
- Product belongs to Category, as a category can have multiple products but a product can only belong to one category.
- Category has many Product models.
- Product belongs to many Tag models. Using the ProductTag through model, allow products to have multiple tags and tags to have many products.
- Tag belongs to many Product models.
- HINT: Make sure you set up foreign key relationships that match the column we created in the respective models.

## Fill Out the API Routes to Perform RESTful CRUD Operations
- Fill out the unfinished routes in product-routes.js, tag-routes.js, and category-routes.js to perform create, read, update, and delete operations using your Sequelize models.
- NOTE: The functionality for creating the many-to-many relationship for products is already done for you.
- HINT: Be sure to look at your module project's code for syntax help and use your model's column definitions to figure out what req.body will be for POST and PUT routes!

## Seed the Database
After creating the models and routes, run npm run seed to seed data to your database so that you can test your routes.

## Sync Sequelize to the Database on Server Start
Create the code needed in server.js to sync the Sequelize models to the MySQL database on server start.