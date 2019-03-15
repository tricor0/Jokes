## Description

This system will provovide a random family friendly jokes. The user will be able to upvote and downvote jokes. There will also be a relevant image or a gif.

## Entity definition
Joke:
- id - number, min - 1, max - 1000000
- type - string, 15 char length, lower case (eg.: family, programming)
- setup - string, 200 char length
- punchline - string, 200 char length
- points - number, min - -5000, max - 5000

- [x] Define the entity ("object" that will be manipulated) of WEB system
- [x] Entity should have a name
- [x] Entity should have 3 mandatory attributes:
    - [x] ID - depending on specific service this could be a number or string
    - [ ] Creation date - (if applicable for specific service) ISO 8601 format date string
    - [ ] Modification date - (if applicable for specific service) ISO 8601 format date string
- [x]Entity should have at least 5 custom attributes
    - [x]Each attribute should have a type defined: number, string, ISO 8601 date string, boolean, object, array or other
    - [x]Each attribute should have restrictions defined: list of constants, or number range, or string length, or string format, or object schema, or array schema or other. For example, you can use `joi` language to define restrictions: https://github.com/hapijs/joi/blob/v13.1.2/API.md

## API definition

GET /api/1/joke/:id - will return joke of this particular id
- 400 - {error: 'invalid joke ID'}
POST /api/1/joke/newJoke - will allow to add a new joke
- 409- {error: 'this ID is already in use'}
- 409- {error: 'setup size is invalid'}
- 409- {error: 'punchline size is invalid'}
GET /api/1/joke/topTen - will return ten jokes with the most points
- 400 - {error: 'invalid joke ID'}
DELETE /api/1/joke/:id - will delete joke with this particular id
- 400 - {error: 'invalid joke ID'}


- 404 - {error: 'REST service is not found'} //path not found
- 500 - {error: 'server error'}


- [x] Define specific service (konkrečios paslaugos) API methods that WEB system is going to use
- [ ] Optionally define additional API methods that WEB system is going to expose
- [x] API should have at least 4 methods
    - [ ] A method to return entity by ID. Should not have request body
    - [ ] A method to return multiple entities (Array) by ID. This method should support at least one header value to:
        - [ ] Return only entities that match pattern in one of its attributes
        - [ ] Return 10 entities starting provided index
        - [ ] Return sorted entities by one of its attributes (both ascending and descending)
        - [ ] Other (should be approved by Product Owner (PO))
    - [ ] A method to remove entity by ID. Returns removed entity. Should not have request body
    - [ ] A method to update entity by ID. Accepts entity to update and returns updated entity
- [x] Each method should have HTTP method defined
- [x] Each method should have URI defined (use {id} as entity ID placeholder)
- [ ] Should return all 4xx errors in unified format. Define format using `joi` language
- [ ] Should return all 5xx errors in unified format. Define format using `joi` language

## UI definition



- [ ] Define the structure of how visually the WEB system is going to look like
- [ ] Should have at least one view defined with https://wireframe.cc (or other wireframe tool):
- [ ] The view should have a title
- [ ] The view should have a description of a service provided by web system
- [ ] The view should include at least 2 UI components:
    - [ ] A component to display multiple entities with all their attribute values visible. It should be posible to remove and edit selected entity.
        - [ ] Depending on chosen header of API method that returns multiple entities, it should be posible to select specific 10 entities starting index, sort entities by attribute, filter entities by attribute pattern, or other (should be approved by Product Owner (PO))
    - [ ] A component to create a new entity/edit existing entity. It should be possible to create new entity and edit selected entity
        - [ ] Each attribute should have a dedicated editor field: text box for string or number, checkbox or radio buttons for boolean, date picker for date, etc.
