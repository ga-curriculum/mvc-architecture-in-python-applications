<h1>
  <span class="headline">MVC Architecture in Python Applications</span>
  <span class="subhead">MVC Examples in Python Frameworks</span>
</h1>

**Learning Objective:** By the end of this lesson, you will be able to **explain** the functionality of a Model-View-Controller (MVC) architecture using a Books REST API example and **understand** the differences in how MVC is implemented in Python frameworks like FastAPI, Flask, and Django.

## Understanding MVC with an example: Books REST API

To understand how MVC works, let's walk through an example of a **Books REST API**. Imagine a user wants to view a list of books on your website or API. Here's how MVC organizes the flow of information:

### Step-by-step:

1. **Request**: The user makes a request to `/books` in the browser.

2. **Router**: The router intercepts the request and directs it to the `books` controller.

3. **Controller**: The controller processes the request and calls the `books` model to fetch data.

4. **Model**: The model interacts with the database, retrieves the list of books, and sends the data back to the controller.

5. **Controller**: The controller formats the data as needed (ex: into JSON or a format the view expects).

6. **View**: The view presents the data to the user. In a REST API, this could mean converting the data into a JSON payload.

7. **Response**: The final response is sent back to the user's browser or application.

> **Note**: In web APIs like FastAPI, Flask, or Django, the "View" often corresponds to the JSON payload sent to the client, rather than a visual template like in traditional web applications.

## MVC across Python frameworks

While the core concept of MVC remains consistent, Python frameworks implement it differently depending on their focus. Here's how FastAPI, Flask, and Django approach MVC:

<img src="./assets/fastAPI-logo.png" alt="fast-api-logo" style="width:250px;"/>

### **[FastAPI](https://fastapi.tiangolo.com/)**

_API-Focused_

- **Model**: Defined using **Pydantic** for data validation and **SQLAlchemy** (or another ORM) for database interaction.
- **View**: Typically the JSON response sent to the client. This is often defined directly in the controller (endpoint function).
- **Controller**: FastAPI endpoints act as controllers. They handle routing, process logic, and return responses.
- **Router**: Explicitly defined in FastAPI, allowing clear organization of API routes.

<img src="./assets/flask-logo.png" alt="fast-api-logo" style="width:250px;"/>

### **[Flask](https://flask.palletsprojects.com/en/stable/)**

_Minimalist Framework_

- **Model**: Flask doesn’t enforce a specific structure, so you can use an ORM like **SQLAlchemy** or any database library of your choice.
- **View**: Views can be HTML templates (using Flask’s [Jinja2](https://jinja.palletsprojects.com/en/stable/) templating engine) or JSON responses in REST APIs.
- **Controller**: Typically, Flask route functions serve as controllers, managing logic and connecting models and views.
- **Router**: Routes are defined via decorators like `@app.route`, which is more manual compared to FastAPI’s modular routers.

**Key Difference**: Flask provides more freedom but less built-in structure than FastAPI, requiring you to define your architecture.

<img src="./assets/django-logo.png" alt="fast-api-logo" style="width:250px;"/>

### **[Django](https://www.djangoproject.com/)**

_Full-Stack Framework_

- **Model**: Uses Django’s built-in ORM, which tightly integrates with the framework. Models are powerful and handle database interaction and validation.
- **View**: Views are typically HTML templates rendered with Django’s template engine or JSON responses for APIs (using Django REST Framework).
- **Controller**: In Django, controllers are abstracted within Django’s views. You write **class-based views** or **function-based views** to handle logic.
- **Router**: Django has a built-in URL routing system, and for APIs, Django REST Framework extends this with robust routing features.

**Key Difference**: Django provides a "batteries-included" approach, offering more built-in tools for traditional MVC applications but may feel more rigid for API development.

---
