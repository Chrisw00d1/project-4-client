![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)
### General Assembly, Software Engineering Immersive

# note-it-down

## Table of contents
* [Overview](#overview)
* [Brief](#brief)
* [Technologies Used](#technologies)
* [Planning](#planning)
* [Backend](#backend)
* [Frontend](#frontend)
* [Lessons learned](#lessons)
* [Future improvements](#future)
* [Contributors](#contributors)

<a name="overview"></a>
## Overview
This was the final project we were given with General Assembly and we had 7 days to build a full stack website. We decided to use create an app that allows users to share tunes that they create with eachother.

You can try it out [here](https://note-it-down-net.netlify.app/).

<a name="brief"></a>
## Brief
* Work either as a pair, group or solo
* Build a full-stack app by creating the frontend and the backend
* Use Django REST Framework with PostgresSQL for the database
* Create the frontend with React
* Build a complete product
* Have CRUD features
* Deployed online

<a name="technologies"></a>
## Technologies Used
* JavaScript
* Python
* Django
* PostgreSQL
* React
* Tone.js
* SCSS
* HTML5
* Cloudinary
* Heroku
* Netlify

<a name="planning"></a>
## Planning
After we decided that we wanted to make a music making app, we worked on planning out the layout of our application using Excalidraw. We both discussed how we wanted to focus mainly on the frontend to make it visually appealing and so it works well for the user. This meant that our backend would not be very complicated so when we planned out our models, using entity relationship diagrams, we only had three.

![](/src/images/screenshot1.png)

I made a start on finding a package we could use for the music while Guy worked on the backend.

<a name="backend"></a>
## Backend
The most difficult model to setup was the songs model as we were not sure on how we should store the notes. At this point I had made some progress on getting Tone.js to work and suggested if there was a way to store arrays of Boolean values for each of the rows of the grid. Guy found that it was possible to store information in a JSONField. This meant we could just simply convert the JSON back into an object to easily apply the data to the grid.

![](/src/images/screenshot2.png)

Guy then created the views necessary for the CRUD requirement. Some features like deleting were made easier with Django as the cascading effect means the relevant data gets deleted with it. Once Guy tested all the views with the client.http, he joined me in working on the frontend.

<a name="frontend"></a>
## Frontend
When Guy joined me here I had created the grid for that has the ability to start and stop a song with the ability to change the notes and tempo while it is playing.  We used a PolySynth for the synthesiser and changed the scale to C major. I also added the addition to being able to hear what the note sounds like when you click it so that you don’t have to guess until you play the song.

![](/src/images/screenshot3.png)

When the user hits the play button, a scheduleRepeact is called on a function which works in a similar way to how a setInterbal works.  All the notes are stored in an object with the notes as keys and array of booleans referring to which button is on or off. The step is which column Tone.js is looking at and then if any are on the PolySynth plays the note. Once that is done, it increases the stepper to look at the next column. 

![](/src/images/screenshot4.png)

Once we had that working and tested that we could save songs and view them using the inbuilt Django admin feature, we split up again. Guy worked on the Song Index page and the Song expanded page while I worked on the login, register, nav and other functionalities of the app. Guy decided the theme for our app should be minimalist with frosted glass effect that looked like an IOS. 

Once I created the nav I noticed that the song would keep playing when changing to different pages of the app. To solve this I read into the documentation of how scheduleRepeat works and that it time it is run it has a unique ID to be able to stop it. So I added a feature to the nav that stopped the repeatSchedule that was playing whenever the location pathname changed.

![](/src/images/screenshot5.png)

For the login and register pages I made the most of the Django error responses which were set up already. I also decided to add an optional profile picture so that a bit more could be shown in the Song Expanded as well as in the nav.  Once we got the login working I changed the save song feature to push the user to the login page when they aren’t currently logged in. I created a temporary system to save their song that they created while they are moved away from that page by storing it in the local storage. Then when they are taken back to the main page after logging in the data is loaded in and then deleted from local storage to prevent it from being loaded every time. The edit and the clone function work in the same way by storing the JSON data from the backend into the local storage.

![](/src/images/screenshot6.png)
![](/src/images/screenshot7.png)


Once I finished the login and register pages I added the comment feature to the expanded view as well as the icons and buttons that were used on the song index page. I then added a filter and search function to the song index page so it could be made easier look for certain songs.

![](/src/images/screenshot8.png)

Finally once we finished the final touches to the app we decided to try and make it mobile friendly. The challenging part was getting the grid to fit onto the screen but once we got that done the rest of the app was easy to change to phone screens.

<a name="lessons"></a>
## Lessons learned
Despite getting Tone.js to work in this project it proved very difficult to get it working in the way that we wanted it to work. There are still cases where the app still breaks when the user clicks too many buttons on the grid or the user creates  spends too long on the app. We realise that we needed to spend more time learning how the library works and that we couldn’t get it working exactly how we wanted.
We also learnt that having a project that was fun to work on made it easier top work on as well as us both wanting to spend time to work on . 

<a name="future"></a>
## Future Improvements
* Looking into how Tone.js works so that it works better for the website
* Improving phone optimisation so that it looks better on phones

<a name="contributors"></a>
## Contributors
I worked with Guy for this project and you can find his Github [here](https://github.com/guykozlovskij).