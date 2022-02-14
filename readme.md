# Full API mini_projetc
this api allows us to collect existing books and categories for various uses, to add new categories as well as new books, to modify or even supress certain books
## Getting Started

### Installing Dependencies

#### Python  3.10.1
#### pip 20.0.3 from /usr/lib/python3/dist-packages/pip (python  3.10.1)

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/livres(books)_api` directory and running:

```bash
pip install -r requirements.txt
or
pip3 install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

## Database Setup
With Postgres running, restore a database using the livres(books)_database.sql file provided. From the backend folder in terminal run:
```bash
psql projetflask_database < projetflask.sql
```

## Running the server

From within the `Library_api` directory first ensure you are working using your created virtual environment.

To run the server on Linux or Mac, execute:

```bash
export FLASK_APP=Nancy.py
export FLASK_ENV=development
flask run
```
To run the server on Windows, execute:

```bash
set FLASK_APP=Nancy.py
set FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `flaskr` directs flask to use the `flaskr` directory and the `__init__.py` file to find the application. 

## API REFERENCE

Getting starter

Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, http://localhost:5000; which is set as a proxy in frontend configuration.

## Error Handling
Errors are retourned as JSON objects in the following format:
{
    "success":False
    "error": 400
    "message":"Bad request
}

The API will return four error types when requests fail:
. 400: Bad request
. 500: Internal server error
. 422: Unprocessable
. 404: Not found

## Endpoints
. ## GET/livres

    GENERAL:
        This endpoints returns a list of livres object, success value, total number of the livres. 
    
        
    SAMPLE: curl http://localhost:5000/livres

        {
        "Livres": [
            {
                "auteur": "Aghata Christie",
                "categorie_id": 1,
                "date_publication": "Fri, 25 Dec 1998 00:00:00 GMT",
                "editeur": "Presses de l'ete ",
                "id": 1,
                "isbn": "4655-5355-454545",
                "titre": "Le crime de l'orient express"
            },
            {
                "auteur": "Soumangourou",
                "categorie_id": 1,
                "date_publication": "Sat, 17 Aug 2002 00:00:00 GMT",
                "editeur": "La cite",
                "id": 2,
                "isbn": "453-42-5352-jf-5",
                "titre": "Sous l'orage"
            },
            {
                "auteur": "Velocity",
                "categorie_id": 2,
                "date_publication": "Fri, 25 Aug 1995 00:00:00 GMT",
                "editeur": "La pegre",
                "id": 3,
                "isbn": "245-5662-526555",
                "titre": "Papa maman"
            },
            {
                "auteur": "Toto",
                "categorie_id": 3,
                "date_publication": "Sat, 06 Jul 1985 00:00:00 GMT",
                "editeur": "La mer",
                "id": 5,
                "isbn": "6523-45dd-5d5",
                "titre": "Sacrileges"
            },
            {
                "auteur": "fuck01",
                "categorie_id": 3,
                "date_publication": "Wed, 12 Mar 2003 00:00:00 GMT",
                "editeur": "Coco",
                "id": 6,
                "isbn": "959-459-vd4",
                "titre": "FUCK"
            },
            {
                "auteur": "je t'aime",
                "categorie_id": 4,
                "date_publication": "Wed, 30 May 2012 00:00:00 GMT",
                "editeur": "La passion",
                "id": 7,
                "isbn": "5464",
                "titre": "L'amour"
            },
            {
                "auteur": "Je te deteste",
                "categorie_id": 4,
                "date_publication": "Sat, 25 Jan 2014 00:00:00 GMT",
                "editeur": "Souffrir",
                "id": 8,
                "isbn": "646d-",
                "titre": "La haine"
            },
            {
                "auteur": "Tu as peur",
                "categorie_id": 5,
                "date_publication": "Sat, 01 Feb 2003 00:00:00 GMT",
                "editeur": "Poltron",
                "id": 9,
                "isbn": "544-cscs-9494",
                "titre": "La peur"
            },
            {
                "auteur": "mama",
                "categorie_id": 5,
                "date_publication": "Sat, 26 Apr 2008 00:00:00 GMT",
                "editeur": "total",
                "id": 10,
                "isbn": "561-656-656",
                "titre": ""
            },
            {
                "auteur": "Hermann",
                "categorie_id": 2,
                "date_publication": "Fri, 14 Jul 2000 00:00:00 GMT",
                "editeur": "Leslo baleines",
                "id": 4,
                "isbn": "456-5665-465-45l",
                "titre": "Sacrifices"
            }
        ],
        "success": true,
        "total_livres": 10
    }
```
. ## DELETE/categorie)

    GENERAL:
        Delete the categorie of the given ID if it exists. Return the id of the deleted categorie, success value, total of (books) a

        Results are paginated in groups of 25. include a request argument to choose page number, starting from 1.

        SAMPLE: curl -X DELETE http://localhost:5000/categories/25
```
            {
        "Categorie": [
            {
                "id": 1,
                "libelle_categorie": "Romans policiers"
            },
            {
                "id": 2,
                "libelle_categorie": "Romance"
            },
            {
                "id": 3,
                "libelle_categorie": "Horreur"
            },
            {
                "id": 4,
                "libelle_categorie": "Vie"
            },
            {
                "id": 5,
                "libelle_categorie": "Action"
            }
        ],
        "success": true,
        "total_categories": 5
    }
```
. ##PATCH/livres/id
  GENERAL:
  This endpoint is used to update a primary_color of plant
  We return a livre(book) which we update

  SAMPLE.....For Patch
  ``` curl -X PATCH http://localhost:5000/livres/42-H "Content-Type:application/json" -d "{"titre": "Peter punk au pays des merveilles"}"
  ```
  ```
    {
        "auteur": "Hermann",
        "categorie_id": 2,
        "date_publication": "Fri, 14 Jul 2000 00:00:00 GMT",
        "editeur": "Leslo baleines",
        "id": 4,
        "isbn": "456-5665-465-45l",
        "titre": "Sacrifices"
    }
    ```

. ## POST/categories

    GENERAL:    
    This endpoint is used to create a new plant or to search for a plant in relation to the terms contained in the livres(books).
    When the searchTerm parameter is passed from the json, the endpoint performs the search. Otherwise, it is the creation of a new question.
    In the case of the creation of a new question:
    We return the ID of the new plant created, the plant that was created, the list of plant and the number of livres(books).

    SAMPLE.....For Search:
    ```
    curl -X POST http://localhost:5000/categories -H "Content-Type:application/json" -d "{"search":"title"}"
    ```

                

    SAMPLE.....For create

    curl -X POST http://localhost:5000/categories -H "Content-Type:application/json" -d "{"id": 6,"libelle_categorie": "personnalite"}"
```
    {
        "Categorie": [
            {
                "id": 1,
                "libelle_categorie": "Romans policiers"
            },
            {
                "id": 2,
                "libelle_categorie": "Romance"
            },
            {
                "id": 3,
                "libelle_categorie": "Horreur"
            },
            {
                "id": 4,
                "libelle_categorie": "Vie"
            },
            {
                "id": 5,
                "libelle_categorie": "Action"
            },
            {
                "id": 6,
                "libelle_categorie": "personnalite"
            }
        ],
        "success": true,
        "total_categories": 6
    }
```      


## Testing
To run the tests, run
```
dropdb livres_database
createdb livres_database
psql livres_database_test < livres_database.sql
python test_flaskr.py
```