---
layout: post
title:  "The App's Humble Beginnings"
date:   2026-02-04 16:57:01 +0000
categories: project update
---

I have created a basic skeleton for what I would like the "home"/"listings" page to look like. It currently has no functionality. I have brought over the login/singup system I had in my demo app, and got that working. Currently, the user is able to visit the listings page without logging in/signing up - this was at first a mistake but I realised could be useful for the actual app, allowing anyone to scroll through listings without making an account, then prompting them to create an account/login once they want to procede with purchasing. 

Here is what the app looks like currently: 

<img src="{{ '/images/IMG_3506.PNG' | relative_url }}" alt="Login/Sign Up Screen Layout" width="300" height="200">
<img src="{{ '/images/IMG_3505.PNG' | relative_url }}" alt="Home/Listing Screen Layout" width="300" height="200">

The layout is inspired by the app Vinted's layout, as I found it a very simple and easy to use marketplace app. I enjoyed being able to quickly browse items while scrolling on the main screen, and getting further detail upon clicking on an item. 

## My Plan For The Month

Had a meeting with Rob today where we discussed where I'm currently at with the project, some queries I had, and what I should aim to have done by the end of February. I said I would like to have constructed skeletons for each page that I need in the app, as mentioned in my previous post, I would like to port over the messaging system I had for my demo app, and begin constructing how I want the listings to work and start on filling in the backend for the listings page. 

Other discussions included AI usage (how I am using it, making sure to log when I do use it, how I can use it, perhaps creating an ethical statement for the document?), running Supabase locally for development and then pushing to the Supabase cloud once I'm satisfied with the work, create a name for the app, and a possible use for AI in the app itself - I will discuss this in more detail now.

I had been struggling with coming up with some way to ensure that the prices that users would be listing their tickets for would be less than or equal to the amount that they spent to originally purchase the ticket from a ticket vendor. Rob and I are toying with the idea of using some AI model (right now looking at Google Gemini) and constructing a query to post to the API once a listing is created to be able to see if the price the ticket is listed for is around the price that the ticket was originally purchased for. The model would take in information provided by the user when they are creating the listing to be able to find the prices that the tickets were sold at and sort the price the ticket was listed for into one of three sections - green, amber or red. If a listing's price is green the price is around the same or less than the original tickets price, if the price is orange the listing's price is around the same or a little bit more that the original ticket's price, and if the listing's price is red then the ticket is listed for too high of a price AND SO futher information is required in order to determine if the listing should be made public - this is where some human agent can step in and open a conversation with the user asking for more details on the original ticket before determining if that listing's price is accurate/fair. I hope that makese sense! 

SO, by the end of February I will aim to have full CRUD done on listings, port over the messaging system I have in the demo app, create skeletons for each page of the app, and perhaps have some AI hook in place! :D