# AY24/25 Semester 2 BED CA1 Assignment

This assignment consists of building a Fitness Challenge System and a game system related to fitness challenges.

This is the endpoint diagram of the server.

```mermaid

flowchart LR
    A["/localhost"]
    A --> B["/users"]
    A --> C["/challenges"]

    
    B --> B1["POST /users"]
    B1 --> B1A["201 Created (New user)"]
    B1 --> B1B["409 Conflict (Username already exists)"]
    B1 --> B1C["400 Bad Request (Missing username in request body)"]


    B --> B2["GET /users"]
    B2 --> B2A["200 OK (List of users returned)"]

    
    B --> B3["PUT /users/{user_id}"]
    B3 --> B3A["200 OK (User updated)"]
    B3 --> B3B["404 Not Found (Requested user_id does not exist)"]
    B3 --> B3C["409 Conflict (Username already exists)"]


    C --> C1["POST /challenges"]
    C1 --> C1A["201 Created (New challenge)"]
    C1 --> C1B["400 Bad Request (Missing challenge, user_id, or skillpoints in request body)"]

    C --> C2["GET /challenges"]
    C2 --> C2A["200 OK (List of challenges returned)"]

    C --> C3["PUT /challenges/{challenge_id}"]
    C3 --> C3A["200 OK (Challenge updated)"]
    C3 --> C3B["404 Not Found (Requested challenge_id does not exist)"]
    C3 --> C3C["400 Bad Request (Missing challenge, skillpoints, or user_id in request body)"]
    C3 --> C3D["403 Forbidden (creator_id different from user_id)"]

    C --> C4["DELETE /challenges/{challenge_id}"]
    C4 --> C4A["204 No Content (Challenge Deleted)"]
    C4 --> C4B["404 Not Found (Requested challenge_id does not exist)"]

    C --> C5["POST /challenges{challenge_id}"]
    C5 --> C5A["201 Created (New completion record)"]
    C5 --> C5B["404 Not Found (Requested user_id or challenge_id not found)"]
    C5 --> C5C["400 Bad Request (Missing creation_date in request body)"]

    C --> C6["GET /challenges/{challenge_id}"]
    C6 --> C6A["200 OK (List of participants attempted challenge returned)"]
    C6 --> C6B["404 Not Found (Requested challenge_id does not have any user attempts)"]


    class B2 GET_Color
    class B4,B1 POST_Color
    class B3 PUT_Color

    class B1A 2xx_Color
    class B1B,B1C 4xx_Color

    classDef GET_Color color:#6bdd9a;
    classDef POST_Color color:#ffe47e;
    classDef PUT_Color color:#6a9ddc;
    classDef DELETE_Color color:#f79a8e;

    classDef 2xx_Color color:#6bdd9a;
    classDef 4xx_Color color:#f79a8e;
```
