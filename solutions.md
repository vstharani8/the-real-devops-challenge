# **The real DevOps challenge**

Please find the below solutions for the all challenges.

### Challenge 1. The API returns a list instead of an object

/api/v1/restaurant/{id} - This endpoint having issue due to undefined variable(id) in the mongoflsk.py file. So I changed the variable from id to _id in the file.

```bash
if _id:
  query["_id"] = ObjectId(_id)
```