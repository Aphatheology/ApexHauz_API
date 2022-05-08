ApexHauz
second Capstone
BUILD A PRODUCT: ApexHauz

Project Overview

ApexHauz is a platform where people can create and/or search properties for sale or rent

Required features

User can sign up
User can sign in
User can post a property advert
User can update the details of a property advert
User can mark  his/her posted advert as sold
User can delete his/her property advert
User can view all property adverts
User can view all properties of a specific type - 2 bedrooms, 3 bedrooms, mini flat etc
User can view a specific property advert
Optional features

User can reset password
User can report a posted advert as fraudulent
User can add multiple pictures to a posted advert
Preparation Guidelines

These are the steps you ought to take to get ready to start building the project

Create a GitHub Repository, add a README.md file, and clone it to your computer. find how to create a GitHub Repo here
Challenge: Create API endpoints

Summary

You are expected to create a set of API endpoints defined in the API Endpoints Specification section and use MySQL to store data

NB: You are to create pull request(PR) for each feature in the challenge and then merge it into your main branch

Tools

NodeJS
ExpressJS
MySQL
JWT => Token management
bcryptjs => Password hash
Guidelines

Version your API using URL versioning starting with the letter "v". Avoid dot notation as 1.0. An example of this will be: https://example.com/api/v1
Setup the server-side of the application using expressjs
Use separate branches for each feature
Use Cloudinary to store your images and only save the URL in your application's database
On GitHub, create a GitHub project with a basic Kanban board
On GitHub under GitHub issues, create the following issues and attach them to your created project: user can signup, user can sign in, user can post a property advert, user can update the details of a property advert, user can mark his/her posted advert as sold, user can delete his/her advert, user can view all properties, user can view all properties of a specific type, user can view a specific property
Under GitHub issues, create issues to capture any other tasks not captured above.
API Response Specification

The API endpoints should respond with the appropriate HTTP response status code and a JSON object with contains either a data property(on success) or an error property(on failure). When present, the data is always an object or an array.

On success

{ "status": "success", "data": {...}}

On Error

{ "status": "error", "error": "error-message"}

Target skills with relevant links

Project management: Click here to see how to create a GH repository project
Version control with GIT: Click here to learn how to use git & GitHub
Cloudinary with Node.js: Click here, and here
HTTP & Web services: Click here
Entity Specification

Users

{

    "id": Integer,

    "email": String,

    "first_name": String,

    "last_name": String,

    "password": String,

    "phone": String,

    "address": String,

    "is_admin": Boolean,

    ...

}

Property

{

    "id": Integer,

    "owner": Integer,  // user id

    "status": String,   // sold, available - default is available

    "price": Float,

    "state": String,

    "city": String,

    "address": String,

    "type": String,    // 2 bedrooms, etc

    "image_url": String,

    "created_on": DateTime,

    ...

}

Reports

{

    "id": Integer,

    "property_id": Integer,

    "created_on": DateTime,

    "reason": String,

    "description": String,

    ...

}



API Endpoint Specification

POST /auth/signup: Create user account

Response spec:

{

    "status": "success",

    "data": {

        "token": "token-generated-with-jwt-npm-package",

        "id": Integer,  // id of the newly created user

        "first_name": String,

        "last_name": String,

        "email": String,

        ...

    }

}

POST /auth/signin: Login a user

Response Spec:

{

    "status": "success",

    "data": {

        "token": "token-generated-with-jwt-npm-package",

        "id": Integer,  // user id

        "first_name": String,

        "last_name": String,

        "email": String,

        ...

    }

}

POST /property: Create a property advert

Response spec:

{

    "status": "success",

    "data": {

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

    }

}

PATCH /property/<:property-id>: Update property data

Note: Include any field you will like to update in your request object and only update those fields

Response spec:

{

    "status": "success",

    "data": {

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

    }

}

PATCH /property/<:property-id>/sold: Mark a property as sold

Response spec:

{

    "status": "success",

    "data": {

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

    }

}

DELETE /property/<:property-id>: Delete a property advert

Response spec

{

    "status": "success",

    "data": {

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

    }

}

GET /property/<:property-id>: Get a specific property by ID

{

    "status": "success",

    "data": {

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

    }

}



GET /property: Get all properties

Response spec

{

    "status": "success",

    "data": [{

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

        }, {

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

        }

        ...

    ]

}

GET /property/search?type=propertyType: Get all properties with a specific type

Response spec

{

    "status": "success",

    "data": [

        {

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

        }, {

        "id": Integer,

        "status": String,

        "type": String,

        "state": String,

        "city": String,

        "address": String,

        "price": Float,

        "created_on": DateTime,

        "image_url": String,

        ...

        }

        ...

    ]

}