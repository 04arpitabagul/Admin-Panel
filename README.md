<a href="https://drive.google.com/file/d/1MBC1rAk6T5QYIJBd22MY6Bp_k21Kpkkt/view?usp=sharing">VIDEO OF OUTPUT</a>

# MAKE ADMIN PANEL ON REQUIREMNT

# zip file :-

[make_admine.zip](https://prod-files-secure.s3.us-west-2.amazonaws.com/0e407914-e744-431a-b6b6-e3dde459be4e/4e95287f-404e-47ce-8d3f-3e0b662bab91/make_admine.zip)

## **Maximum Marks - 8 (Rubrics as per the problem statement)**

```
✅ able to submit the application - 1 mark (minimum score)
✅ should able to post the data and send the appropriate response on hitting at POST "/add/hero" - 1 mark
✅ should able to get the data and send the appropriate response on hitting at GET "/heroes" - 0.5 mark
✅ should be able to add villain for the hero PATCH "/update/villain/:hero_id" route - 1.5 mark
✅ should be able to delete the hero DELETE "/delete/hero/:hero_id" route - 1.5 mark
✅ "logger" middleware should be working fine - 0.5 mark
✅ "auth" middleware should be working fine - 1 mark
✅ "addID" middleware should be working fine - 1 mark

```

Initialize a backend project using the right command for it and create an express app.

There will be a `db.json` file containing the sample data, which you will be using as a database for performing CRUD operations, Following is the sample structure:

```
{
    "heroes": [
        {
            "id":1,
            "name": "IronMan",
            "powers": [
                "robot",
                "money"
            ],
            "health": 33,
            "villains": [
                {
                    "name": "Mandarin",
                    "health": 50
                }
            ]
        }
    ]
}

```

The application should provide the following functionalities through API endpoints:

## **1. Add a new hero**

- Endpoint: `POST` `/add/hero`
- Description: Adds a new hero to the system.

Request Body:

It should contain the details of the hero that you want to add.

```
{
      name: "Captain Marvel",
      powers: ["superhuman strength", "energy projection", "flight"],
      health: 95,
      villains: [
        {
          name: "Yon-Rog",
          health: 60,
        }
      ],
}

```

Response:

```
OK: Returns the details of all the heroes along with the newly updated one.
err: Returns the error

```

- Middleware: `addID` - Generates a new id for the hero and add it to the request body, you need to see if the last hero's `id` is `3` for the new hero the `id` should be `4` and so on.

## **2. Retrieve details of all heroes**

- Endpoint: `GET` `/heroes`
- Description: Retrieves all the heroes.

Response:

```
OK: Returns the details of all the heroes.
err: Returns the error

```

## **3. Update villains for a hero**

- Endpoint: `PATCH` `/update/villain/:hero_id`
- Description: Updates the villains for a specific hero.
- URL Parameter: hero_id - Unique id of the hero.

Request Body:

It should contain the details of the villain that you want to add for a hero.

```
{
    name: 'King Peen',
    health: 20
}

```

Response:

```
In case of hero not found with hero_id - { message: "Hero not found"}

OK: Returns the updated hero data only, not all the heroes.
err: Returns the error

```

- Middleware: auth - Provides authentication for the endpoint. If the `role` and `pass` are `admin` and `saveEarth` respectively then this route should work otherwise following response should be sent:

```
{ message: "Not Authorized" }

```

## **4. Delete a hero:**

- Endpoint: `DELETE` `/delete/hero/:hero_id`
- Description: Deletes a specific hero.
- URL Parameter: hero_id - Unique id of the hero.

Response:

```
OK: Returns the details of all the heroes after deleting this specific one.
err: Returns the error

```

- Middleware: auth - Provides authentication for the endpoint. If the `role` and `pass` are `admin` and `saveEarth` respectively then this route should work otherwise following response should be sent:

```
{ message: "Not Authorized" }

```

## **Middleware Details**

1. `addID:`
- Description: Generates a unique id for the hero before adding it to the system.
1. `logger:`
- Logs the API endpoint along with the method at which client has made the request, with a proper time stamp

```
URL: /heroes, Method: GET, Timestamp: Fri May 19 2023 02:24:57 GMT+0530 (India Standard Time)
URL: /add/hero, Method: POST, Timestamp: Fri May 19 2023 04:56:24 GMT+0530 (India Standard Time)

```

1. `auth:`
- Provides authentication for the protected endpoints (`update/villain/:hero_id` and `delete/hero/:hero_id`). It ensures that the user is authenticated before allowing access to these endpoints.

## **Installation**

- Use node version(LTS) should be
- Don't change/override package.json
- 

```
npm install 

// complete functions

// test locally
npm run test
`make sure when you test locally server is not running locally.`

```

## **Requirements**

- The code should be written in Node.js.
- Use the built-in modules and external modules that are required.
- Add comments throughout your code to explain the logic behind each step

## **Evaluation Criteria**

- Correct implementation of all the routes
- Proper handling of edge cases
- Code readability and organization
- Comments explaining the logic behind each step
