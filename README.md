# Project 3 ReadMe

Name: The Divorce Party GuestBook
Team: Chewing the CRUD

## Description

A MERN full-stack website that allows users to sign-up for an account, read, post, edit and delete comments in a Divorce Party Guest Book. This was implemented as a group project consisting of four General Assembly students with the amusing team name of “Chewing the CRUD”.

## Why a Divorce Party Guestbook

While never being married myself, a lot of people will attest to their experience of a divorce as one of the best things that has ever happened to them. Of course they will want to celebrate with lots of friends and family. What better way to commemorate the celebration than with a Divorce Party Guestbook? The app was developed to help recent divorcees enjoy their divorce party to the fullest and will hopefully let users relive all the happy memories. A divorce isn't the end; merely the beginning to either a new chapter or a whole new sequel.
Deployment Links
[The Divorce Party Guestbook](https://hpramanathan.github.io/project3-mernstack-app/)
[GitHub Repo](https://github.com/khouryb/project3-mernstack-app)

## Brief

A set of minimum requirements were given to project teams for the front-end, back-end, styling and deployment:

## MVP Requirements

### Planning

- Have a thoroughly documented Team Expectations Google document / markdown file.
- Have a thoroughly developed, beautiful README.md file.
- Take time for each team member to discuss where they feel strongest and weakest, in terms of coding ability.
- Create a Excalidraw or Whimsical document to convey the data flow with component hierarchy included.

### Collaboration

- Contribute equally.
- Have a solid understanding of the entire project. (Even the features implemented by other team members.)
- Take time to pair program with teammates to reinforce learning.
- Be prepared to explain sections of code that were written by teammates.

### Client (Front End)

-Have a working, interactive React app, built using npx create-react-app client
-Have at least 6 separate, rendered components in an organized and understandable React file structure.
-Use only React for DOM Manipulation.
-Consume data from your API, and render that data in your components.
-Utilize React Router, for client-side routing.
-Authentication!

### Server (Back End)

- Have generic router actions for CRUD using Express, Mongoose, and MongoDB.
- Have at least 2 models (more if it makes sense)
- Have full CRUD on at least one of your models
- Be able to Add/Delete on any remaining models (if it makes sense)
- Authentication!

### Styling

- Be styled with CSS.
- Use flexbox (display: flex) or CSS Grid.
- Implement responsive design on 2 screen sizes (including desktop) using a media query (mobile).
- You can use a CSS framework if you want to.

### Linting

- Indent properly.
- Utilise high-quality, semantic variable names and follow naming conventions.
- Remove unnecessary boilerplate React files and code.
- Remove all console.log()s and commented out code (functional notes/comments are okay).

### Deployment

- Deploy the fully functional front-end via GitHub Pages or Vercel.
- Deploy the back-end via Heroku (or vercel).
- Deploy the MongoDB database on MongoDB Atlas.

## Planning

Day one consisted of the planning of our project. The first thing we did was to write a Team Expectations Document which outlines which team member will take on which role, how much time we would each dedicate to the project daily and other things like who the Git maintainer is and timeline of the project. We also used this day getting used to pushing and pulling from the team repository on GitHub.

### FLOW CHART, USER STORIES AND WIREFRAME

#### Wireframe

We decided to peel off at this point and each person was assigned a task. I was tasked with making the wireframes for our project, which I did on Excalidraw.

![click](https://i.ibb.co/hdnPhKF/project-3-wireframe.png)

#### User Stories

- As a user I should be able to access the website from different devices/browsers.
- As a user I should be able to register with a username and password.
- As a user I should be able to login with my username and password.
- As a user I should be able to view all posts.
- As a user I should be able to view my posts.
- As a user I should be able to write new posts.
- As a user I should be able to delete my posts.
- As a user I should be able to edit my posts.
- As a user I should be able to log off from the website.

#### Database Models Flowchart

![flow chart](https://i.ibb.co/16fXVx0/project-3-flow-chart.png)

#### LAYOUT

Franziska took the lead with researching a number of colour schemes online and as a team we agreed upon the first colour scheme below:

![flow chart](https://i.ibb.co/yhDWMbb/Colour-Schemes.png)

We used the Tailwind CSS framework for our styling. We added the chosen colour scheme above to our Tailwind config file.

This is what our final homepage layout looked like:

![homepage](https://i.ibb.co/Y3b7cjZ/Layout.png)

## BUILD/CODE PROCESS

## Schemas

Finally we would get to writing some code and decided to split off individually. I was tasked with creating the Schemas for Users and Posts. This was done using mongoose.js here are some code snippets of the schemas:

User schema:

```javascript
const mongoose = require('mongoose')
const Schema = mongoose.Schema;

const userSchema = new Schema({
    username: { type: String, required: true },
    password: { type: String, required: true },
    name: { type: String, required: true },
    posts: [{
        type: mongoose.Schema.Types.ObjectId,
        ref: "Post"
    }]

}, { timestamps: true })

const User = mongoose.model('User', userSchema)

module.exports = User;
```

Posts schema:

```javascript
const mongoose = require('mongoose')
const Schema = mongoose.Schema;

const postSchema = new Schema({
    author: { type: String, required: true },
    title: String,
    content: { type: String, required: true }
}, { timestamps: true })

const Post = mongoose.model('Post', postSchema)

module.exports = Post;
```


We established as a team that we needed a one to many relationship between the Users and Posts ie. one user has many posts. I decided to make two schemas and reference the Post schema inside of the User schema. I felt that referencing was the best choice as opposed to using a sub-document nested inside of the User schema as this allowed for more flexibility and scalability if needed.

## User Authentication

On day 3 we decided to split off individually and I was tasked with implementing user authentication. I’m not going to lie, at first I found this quite difficult being my first time trying to use it and so I asked for help from a team mate and Katie came to help. We used Passport.js to handle authentication with passport-jwt as our strategy.

## CHALLENGES

Seeding: The team faced challenges while implementing the seed file to populate initial data into the database. It required careful handling and synchronisation to ensure the data was properly seeded.
Authentication: Developing user authentication posed challenges. I found user authentication particularly difficult, but got there in the end with help from teammates.

## WINS

Authentication: Successfully implementing user authentication using bcrypt for password hashing and Passport JWT for user authentication was a significant win for the team. It ensured secure access and protected user data.
Tailwind CSS: Utilising the Tailwind CSS framework for layout and styling proved to be a success. The chosen colour scheme and styling enhanced the overall design of the website.
Git conflicts: Initially this was the most annoying part of the project. Merge conflicts were common at the beginning and we decided to resolve them as part of a team. I feel like I gained knowledge in this area and eventually we got used to them and they happened less.

## KEY LEARNINGS

I learnt a lot about the back end in this project. Especially dealing with authentication, whilst difficult at first, ended up to be a great learning experience that I hope I can implement in further projects. I also did a bit of the front end using Tailwind for the first time and I’m glad I got a bit of practice with it so I will be able to use it in future projects.

## BUGS

One notable challenge encountered at the end of the project was the issue with the Front-End deployment prep and its relation to the (back-end) Heroku server. This connectivity issue caused a disruption in the expected flow of data and functionality, hindering the full operation of the website. The team worked diligently to troubleshoot and resolve this bug, but were unable to do so. Hence the website is only accessible via a localhost.

## FUTURE IMPROVEMENTS

Create a file upload facility for user profile pictures and party pictures within a post: Enhancing the website by adding a file upload feature would allow users to upload profile pictures and images related to their divorce party posts, further enriching the user experience.
Get quotes about divorce via an external API: Integrating an external API that provides quotes specifically related to divorce would add interesting and relevant content to the website. It could enhance the overall user engagement and provide additional value to the users.

