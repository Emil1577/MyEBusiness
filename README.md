# MyEBusiness

## Decription

MyEBusiness is a challenge to build the back end for an e-commerce site. Working on Express.js API and configure it to use Sequelize to interact with a MySQL database.

Here is the link of the walkthrough video demonstrating the functionality.

https://drive.google.com/file/d/1iLioXrgMt14pjzHe6LBuVzUqc1B6E556/view

Here is the GitHub repository.

https://github.com/Emil1577/MyEBusiness

## Installation Instructions

First you need to clone my repository. Go to https://github.com/Emil1577/MyEBusiness. Then run your terminal on the folder of the cloned repository.  You'll also need to install the npm by writing "npm install' and the MYSQL.  On MySQL run the schema.sql then exit.   Then type in "npm run seed" in the terminal to run the seed, then after which is "npm start" to run the program.  Then open Insomia.

## Table Of Contents

1. [Webpage Screenshot](#webpage-screenshots)
2. [Code Snippets](#code-snippets)
3. [How to use:](#how-to-use)
4. [My Contact Information](#my-contact-information)

## Webpage Screenshots:

![Screen Shot 2023-02-06 at 9 39 46 PM](https://user-images.githubusercontent.com/119825000/217158088-376197fd-7bd4-4f97-9c41-026442ca2681.png)

![Screen Shot 2023-02-06 at 9 40 18 PM](https://user-images.githubusercontent.com/119825000/217158170-3926a0e9-d735-46ce-81b8-4e6b066f0286.png)


## Code Snippets: 
    
### Sample Get routes

    router.get("/", (req, res) => {
      // find all categories
      Category.findAll({
        attributes: ["id", "category_name"],
        include: [
          {
            model: Product,
            attributes: ["id", "product_name", "price", "stock", "category_id"],
          },
        ],
      })
        .then((categoryData) => res.json(categoryData))
        .catch((err) => {
          console.log(err);
          res.status(500).json(err);
        });
    });


### Sample Post routes

    router.post("/", (req, res) => {
      // create a new category
      Category.create({
        category_name: req.body.category_name,
      })
        .then((productData) => res.json(productData))
        .catch((err) => {
          console.log(err);
          res.status(500).json(err);
        });
    });

### Sample Delete Routes

    router.delete("/:id", (req, res) => {
      // delete a category by its `id` value
      Category.destroy({
        where: {
          id: req.params.id
        }
      })
        .then(categoryData => {
          if (!categoryData) {
            res.status(404).json({ message: 'There was no category found with this id.' });
            return;
          }
          res.json(categoryData);
        })
        .catch(err => {
          console.log(err);
          res.status(500).json(err);
        });
    });
    
## How to use:

### On Insomia and terminal:

    GIVEN a functional Express.js API
    WHEN I add my database name, MySQL username, and MySQL password to an environment variable file
    THEN I am able to connect to a database using Sequelize
    WHEN I enter schema and seed commands
    THEN a development database is created and is seeded with test data
    WHEN I enter the command to invoke the application
    THEN my server is started and the Sequelize models are synced to the MySQL database
    WHEN I open API GET routes in Insomnia for categories, products, or tags
    THEN the data for each of these routes is displayed in a formatted JSON
    WHEN I test API POST, PUT, and DELETE routes in Insomnia
    THEN I am able to successfully create, update, and delete data in my database

## My Contact Information:

* [My LinkedIn](https://www.linkedin.com/in/emil-ronquillo-76832a32/)
* [My Github](https://github.com/Emil1577)
* [My Email](mailto:emilronquillo@gmail.com)

## Thank you for stopping by. 

Special thanks to all my Instructor, tutors and my colleagues
