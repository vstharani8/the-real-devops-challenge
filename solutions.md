# **The real DevOps challenge**

Please find the below solutions for the all challenges.

### Challenge 1. The API returns a list instead of an object

#### /api/v1/restaurant/{id} 
This endpoint having issue due to undefined variable(id) in the mongoflsk.py file. So I changed the variable from id to _id in the file.

```bash
if _id:
  query["_id"] = ObjectId(_id)
```

#### Return a json object instead of a json array if there is a match or a http 204 status code if no match found
In this challenge, will check the output of the query. Based on this query, will send the return output. 
For the json object, used to get the first element of the list. So that, will have the output of the json object

```bash
@app.route("/api/v1/restaurant/<id>")
def restaurant(id):
    restaurants = find_restaurants(mongo, id)
    if not restaurants:
        return jsonify(
                    message="Wrong ID  provided.",
                    category="error",
                    status=204
         )
    return jsonify(restaurants[0])

```
### Challenge 2. Test the application in any cicd system
In this challenge, we used Gitlab-CI tool to automate the deployment of the app and created new pipeline file for that. 
Pipeline File 
```bash
.gitlab-ci.yml.
```
In this pipeline, having 2 stages. 
* Test -  To test the application using tox package
* Deploy - - To deploy the application (Here just installing the app requirements)
If I commit any changes in the repo, automatically will start the pipeplien to deploy the solution. 
