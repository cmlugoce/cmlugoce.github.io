---
layout: post
title:      "Parks-book: Now with jQuery!!"
date:       2018-09-04 17:43:36 -0400
permalink:  parks-book_now_with_jquery
---


For the fourth project, Rails app with jQuery, I decided to keep working with my previous app, Parks-book. The goal of the project was to develop dynamic features through jQuery and JSON API. Honestly, I had fun using Javascript, but I had some challenges in coding what I wanted hahahaha!



##  Must render one index page via jQuery and an Active Model Serialization JSON Backend.

 I decided to work with my User model. In the previous portfolio project the User's Profile showed the list of parks       logged. Now, I built a button that when clicked, displays the list of the user's parks. Also, in the Trails index view, there is a   'Read More' button that displays the trails' description without refreshing the page. 
 
```
///////////View parks on 'users/show'//////////////

$(function() {
    $(".js-view-parks").on('click',  function(event) {
      
     let id = event.target.getAttribute("data_id");
   
      $.get("/users/" + id + ".json", function(data) {
       
        
        loadUsersParks(data);
      })
      event.preventDefault();
    }
  });
```
   
	 

## The Rails API must reveal at least one has-many relationship in the JSON that is then rendered to the page.

Trail `has_many` Comments. The comments were rendered in the 'Trails show page'.
   
        


## Must render one show page via jQuery and an Active Model Serialization JSON Backend. 

The  Park show page has a 'Previous' and 'Next' button that allows the user to sift through the parks posts.

```
/////////////////////view prev/////////////////////

$(function(){
  $(".js-previous-park").on("click", function (event) {
    let id = event.target.getAttribute("data-id");
      
  $.get("/parks/" + id + "/previous", function(data) {
  // console.log(data)
    
   loadPark(data);
   
  });
  event.preventDefault();
  
 })
})
```



## Must use your Rails API to create a resource and render the response without a page refresh.


This means that we have to use AJAX Post to create a new object. For instance, when a user adds a comment, the comment is serialized, submitted through an AJAX Post request, with the response being the new object in JSON and then appending that new comment to the DOM. In the 'Trails show page' the user can create a new comment and the comment will append without a page refresh.

```
 $(function (){
       $("#new_comment").on("submit", function(event){
      
       
        
         $.ajax({
             type: "POST",
             url: this.action,
             data: $(this).serialize(), // takes our form data and serializes it
             success: function(response) {
      
                let comment = new Comment(response);
                comment.renderComments();
                $(".commentBox").val("");
              }
            });
            event.preventDefault();
            
        })
      });
```

## Must translate the JSON responses into Javascript Model Objects. The Model Objects must have at least one method on the prototype. 

`Comment.prototype.renderComments` – The data of a comment is passed into the `renderComments()` function and appended to the DOM without refreshing the page.  

```
function Comment(data) {
       this.id = data.id;
       this.body = data.body;
       this.user = data.user;
      };
			Comment.prototype.renderComments = function() {
   let html = "" ;
   html += 

  `<div class=\'well'>
  <strong>${this.user.name}</strong> says: <br></br>
   <p>${this.body}</p>
  </div>`;
 
   $(".comment-sec").append(html);

   
   };
			
```

	

## Conclusion

I like the functionality of my app, but I'm planning on adding more features such as editing and deleting comments. I learned a lot while doing this project. I'm excited and terrified to move onto React!!!
