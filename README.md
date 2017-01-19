# P-Brain.ai - Voice Controlled Personal Assistant

## Install

Clone repo, cd to its directory and type `npm install` & `npm start`

Add api info for http://openweathermap.org/api and https://newsapi.org/account to `config/index.js`

Open Chrome and enter http://localhost:4567/

Say `Hey Brain`, `Brain` or `Okay Brain` followed by your query (i.e `Hey Brain, What is the weather in Paris`).

## Adding Skills

Add a skill by creating a new folder with the name of your new skill and adding an `index.js`.



Add functions for `_intent` and `{skill_name}_resp` to that index, the latter contining the logic that will respond to a query. The `{skill_name}_resp` function must have a response type of `String`



In `_intent` add `return {keywords:['key 1','key 2'], module:'{skill_name}'}` where `keywords` are the phrases you wish the skill to respond to and `{skill_name}` is the name of your new skill.



Add `module.exports = {intent:_intent, get: {skill_name}_resp};` to the end of your `index.js`



Add that new folder to the `skills` directory in the project.



And bang, Brain will automatically import and enable your new skill!


### End Points
`http://localhost:4567/api/ask?q={query}`
`http://localhost:4567/`


# Docker

You can run this application via Docker. Prequisites are that you have docker installed
and cloned this repository locally. Then execute the following command to create an docker image
called _p-brain_ and a container called _p-brain_.

    docker build -t p-brain .
    docker run --name=p-brain -v `pwd`:/home/app -v /home/app/node_modules -p4567:4567  p-brain npm start

After doing this you can stop the container by running `docker stop p-brain`. Starting it again
is done by running `docker start p-brain`.
