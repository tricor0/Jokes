## Description

This system will provovide a random family friendly jokes. The user will be able to upvote and downvote jokes. There will also be a relevant image or a gif.

## Entity definition
Joke:
- id - number, min - 1, max - 1000000
- type - string, 50 char length, lower case (eg.: family, programming)
- setup - string, 200 char length
- punchline - string, 200 char length
- points - number, min - -5000, max - 5000


## API definition

GET /api/1/joke/:id - will return joke of this particular id
- 400 - {error: 'invalid joke ID'}

POST /api/1/joke/newJoke - will allow to add a new joke
- 409- {error: 'this ID is already in use'}
- 409- {error: 'type size is invalid'}
- 409- {error: 'setup size is invalid'}
- 409- {error: 'punchline size is invalid'}

GET /api/1/joke/topTen - will return ten jokes with the most points
- 400 - {error: 'invalid joke ID'}

DELETE /api/1/joke/:id - will delete joke with this particular id
- 400 - {error: 'invalid joke ID'}


- 404 - {error: 'REST service is not found'} //path not found
- 500 - {error: 'server error'}


## UI definition

https://wireframe.cc/Lvupzm
