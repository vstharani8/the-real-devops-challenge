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
    return jsonify(restaurants)

```
