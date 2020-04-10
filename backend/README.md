# Full Stack Trivia API Backend

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py.

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server.

## Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

## Running the server

From within the `backend` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `flaskr` directs flask to use the `flaskr` directory and the `__init__.py` file to find the application.

## API Reference

### Getting Started
- Base URL: At present this app can only be run locally. The backend app is hosted at default: `http://127.0.0.1:5000` or `http://localhost:5000`, which is set as a proxu in the frontend configuration.
- Authentication: At this moment, the app does not require API keys.

### Endpoints
#### GET `/categories`
- General:
    - Returns a categories dictionary, where keys are the categories id and the value is the corresponding string of the category. Returns total number of categories and success value.
- Sample: `curl http://127.0.0.1:5000/categories`
```{
        {
          "categories": {
            "1": "Science",
            "2": "Art",
            "3": "Geography",
            "4": "History",
            "5": "Entertainment",
            "6": "Sports"
          },
          "success": true,
          "total_categories": 6
        }
      ```

#### GET `/questions`
- General:
    - Returns a list of questions objects, categories dictionary, total number of questions and success value.
    - Resulst are paginated in groups of 10. Include a request argument to choose page number, starting from 1.
- Sample: `curl http://127.0.0.1:5000/questions`
```{
    {
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "current_category": null,
  "questions": [
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    }
  ],
  "success": true,
  "total_questions": 2

  }
  ```

#### GET `/categories/<int:category_id>/questions`
- General:
    - Returns a list of questions based on category, total number of questions, categories, current category, and success value.
- Sample: `curl http://127.0.0.1:5000/categories/3/questions`
``` {
  {
    "categories": {
      "1": "Science",
      "2": "Art",
      "3": "Geography",
      "4": "History",
      "5": "Entertainment",
      "6": "Sports"
    },
    "current_category": 3,
    "questions": [
      {
        "answer": "The Palace of Versailles",
        "category": 3,
        "difficulty": 3,
        "id": 14,
        "question": "In which royal palace would you find the Hall of Mirrors?"
      },
      {
        "answer": "Agra",
        "category": 3,
        "difficulty": 2,
        "id": 15,
        "question": "The Taj Mahal is located in which Indian city?"
      },
      {
        "answer": "Lake Victoria",
        "category": 3,
        "difficulty": 2,
        "id": 29,
        "question": "What is the largest lake in Africa?"
      }
    ],
    "success": true,
    "total_questions": 3
  }
```

#### POST `/questions`
- General:
    - Creates a new question using the question, answer, difficulty, and category. Returns the id of the created questions, success value, total number of questions and the list of questions on current page number to update the frontend.
- Sample: `curl -X POST -H "Content-Type: application/json" -d '{"question":"sample question?","answer":"sample answer!", "difficulty":"3", "category":"2"}' http://127.0.0.1:5000/questions`
``` {
{
  "created": 39,
  "questions": [
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    },
    {
      "answer": "Agra",
      "category": 3,
      "difficulty": 2,
      "id": 15,
      "question": "The Taj Mahal is located in which Indian city?"
    },
    {
      "answer": "Escher",
      "category": 2,
      "difficulty": 1,
      "id": 16,
      "question": "Which Dutch graphic artist\u2013initials M C was a creator of optical illusions?"
    },
    {
      "answer": "Mona Lisa",
      "category": 2,
      "difficulty": 3,
      "id": 17,
      "question": "La Giaconda is better known as what?"
    }
  ],
  "success": true,
  "total_questions": 22
}
```

#### POST `/questions/search`
- General:
    - Returns the list of questions that contains the input anywhere within the question, total number of questions, category, and success value.
- Sample: `curl -X POST -H "Content-Type: application/json" -d '{"searchTerm": "title"}' http://127.0.0.1:5000/questions/search`
```{
  {
    "current_category": null,
    "questions": [
      {
        "answer": "Edward Scissorhands",
        "category": 5,
        "difficulty": 3,
        "id": 6,
        "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
      },
      {
        "answer": "Manchester City",
        "category": 6,
        "difficulty": 2,
        "id": 25,
        "question": "Which team won their second Premier League title in 2014?"
      }
    ],
    "success": true,
    "total_questions": 2
  }
```

#### POST `/quizzes`
- General:
    - Creates a new random question based on the category selected, `quiz_category = 0` to select all categories and opt-out given list of previous questions.
    - Request arguments sample:
    ```{
      {
        previous_questions: [],
        quiz_category: 1
    }
    ```

#### DELETE `/questions/<int:question_id>`
-General:
    - Deletes the question of the given id if it exists. Returns the updated list of questions on current page to update the frontend, total number of questions, and success value.

#### Error Handling
Errors are returned as JSON objects in the following format:
```{
  {
    "success": False,
    "error": 400,
    "message": "bad request"
   }
```

The API will return three error types when requests fail:
- 400: Bad Request
- 404: Resource Not Found
- 422: Unprocessable

## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
