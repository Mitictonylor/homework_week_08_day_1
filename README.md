# star_wars

## Project setup
```
npm install
npm install vue-router
npm install vue-moment
npm update
```

### Compiles and hot-reloads for development
```
npm run serve
```




### BRIEF
Learning Objectives
Be able to set up a Vue application
Be able to read data from an API
Be able to make requests using Promise.all
Be able to implement filters
Brief
You have been asked to build an app to display information about Star Wars films.

Use the data from this url to allow the user to display a list of films and further film information.

MVP
The app should initially display a list of the film titles

When a film title is clicked the app should load the film details including title, episode number, release date and director.

When the film detail loads, the films characters details (name and height) should also be displayed.

Extensions
Add a filter to format the height from centimetres into meters (i.e. 172cm => 1.72m)
Add a filter to format the date as dd MMM YYYY. (19 May 1999) (Hint- Look into Moment npm package)
Also show details of a characters home world (name, terrain) along with the character name and height.
Advanced Extensions
Use router to add a link to the film details. When this is clicked it should take you to a view that displays the films opening crawl text. (Doesn’t need to be fancy!). The crawl view should take in the film as a prop to access the crawl.
