---
title: Sails lift
description: First struggling with assignment 1
layout: post
---

We are really into the assignment 1 now. We finalized our idea during week 2 and then had a couple of discussions about what would be in the technology stack. Tough choice, you know the Web Development world already has tons of frameworks for both front-end and back-end. Finally, we decided to use a fairly new and less common framework called [Sails.js](http://sailsjs.org/) as our core.

### <i>Sails is the new Rails ?</i>
[Ruby on Rails](http://rubyonrails.org/), needless to say, has become a big player among web dev field for years. I think two of the biggest advantages of Rails over other frameworks are its great execution of MVC model and its ability to perform "magic stuffs" (convention over configuration). On the other hand, [Node.js](http://nodejs.org/) is gaining more and more popularity thanks to the recent trend of realtime data-driven websites and the technologies supporting it ([Socket.io](http://socket.io/)). It seems to me that the framework which can combine all of these features will become the next domination. And Sails is created with this ambition.

The underlying infrastructure of Sails is Node.js + [Express](http://expressjs.com/). On top of that, they build a MVC model and some "Railsly" things such as auto RESTful routing and built-in generating commands. One of the interesting feature is usage of Socket.io by default which listens to all changes in the database/models.

### <i>Imperfect</i>
Sails is fairly young (first commit on GitHub just 5 months ago !!), thus it still lacks a lot of features and some existing features are just incomplete/<s>weird</s>/inconvenient.</br>
For example, asynchronous database query is nice but it really needs to come with model association. Image we have this schema:
<pre><code>Course has_many: Students
Student has_many: Questions
</code></pre>
Then to fetch the students' questions within one course, we might to do something like this:
<pre><code>Course.find({id: id}).done(function(err, course) {
  Students.find({course_id: course.id}).done(function(err, student) {
    Questions.find({student_id: student.id}).done(function(err, question) {
      ... // Do things
    });
  });  
});
</code></pre>
Nested models usually result in a callbacks hell like above :-( One good news is that the missing association feature is currently being developed, according to the framework author.

### <i>Lesson</i>
Working with an immature framework certainly brings you some unwanted worries. The incomplete set of features, the lacking of documentation usually bite us hard. Looking at our code, we can easily tell that we have used a lot of hacking to do even the most trivial stuffs. However, it also maybe a good thing because we can learn a lot during the project and have a very deep understanding of the framework. We just feel better at our ninja skills =) I hope my group still have enough strength to continue our hacking way :)