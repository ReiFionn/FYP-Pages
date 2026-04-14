---
layout: post
title:  "Easter Work and Final POA"
date:   2026-04-13 22:09:01 +0000
categories: project update
---

I once again did not mean to leave such a large gap between updates, but I'm here now so let's dive in! 

First, I wanted to mention that I haven't achieved the amount of work I wished to have done by this stage. This comes as a result of currently being 
on a second dose of antibiotics for a chest infection that had me floored for most of the first week of the Easter holidays. I was wrecked with little to no 
energy and was unable to work, but I did catch up on some well needed rest and sleep!

Theres a lot to cover in this update, starting with a new app name: Agorex (It was a name being workshopped but I needed one for the poster and so I had to stick
with it lol)! The name comes from a combination of Agora (meaning "gathering place" or "assembly", a central place for political, social, and economic activities in ancient Greek cities) and exchange! Pages where the placeholder name was displayed have now all been updated to Agorex!

Each page has been updated to match the theme's colours, as well as getting makeovers (I will mention these later as they come up with each page).

The "Make offer" button on a listing page will now open a conversation between the two users, using the same logic that was used in my Semester 1 demo app. Each conversation shows the
user that is being messaged display name at the top of the conversation page. The messages tab was also updated to only show the conversations that the current logged in user is a part of,
previously it was showing every conversation in Supabase. Both the conversation and messages pages both recieved a UI overhaul (this was done much later after the previous code update to 
these pages but I thought I might as well mention it now!), check them out: 

<img src="{{ '/images/easter/messages.PNG' | relative_url }}" alt="new messages tab" width="300">
<img src="{{ '/images/easter/conversation.PNG' | relative_url }}" alt="new conversation tab" width="300">

Following this, functionality was added back to the search bar on the index page, and the layout was tidied:

<img src="{{ '/images/easter/search.PNG' | relative_url }}" alt="search bar functionality" width="300">

Next, I added a Stripe webhook to the app to be able to detect when a user begins to pay for a ticket, and when the funds are recieved in Agorex's Stripe account. Originally I was just running
this locally, but later on I move this onto Supabase... Once the webhook is fired, it is able to directly change the ticket's status field on Supabase. 

When a user now begins a transaction, the Stripe ID that is created by Stripe is retrieved and set as the stripe_customer_id field. A check is done before every transaction to see if the user
has a Stripe ID associated with their account. If they do, that ID is used, otherwise an ID is created and set to the empty field.

<img src="{{ '/images/easter/profileTable.png' | relative_url }}" alt="profile table">

The ticket listing page was updated to show details about the ticket. I will come back to this and make it prettier if I have the time!

When a user now goes to create a listing, a Supabase edge function is used to call a Spotify API and retrieve an image of the artist for the specific listing, and that image's URL is saved
in the artist_image_url field for the listing. The image is displayed in the listing's card on the index page and on the listing's page itself!

<img src="{{ '/images/easter/index.PNG' | relative_url }}" alt="listing cards show image" width="300">
<img src="{{ '/images/easter/listing.PNG' | relative_url }}" alt="listing showing ticket details + image" width="300">

The profile page was finally properly created. It features the user's profile picture (which can be changed by clicking on the default profile picture) which is uploaded and retrieved from a 
bucked on Supabase, the user's average trust rating, their current lisitngs and their past purchases. The bottom of the screen contains the logout button. 

<img src="{{ '/images/easter/profile.PNG' | relative_url }}" alt="new profile page" width="300">

Circling back to the transactions now, when a transaction begins by the user clicking the buy button on the listing, that user's ID is set as the active_buyer_id field on the lisitng. Dismissing the payment sheet or failing the transaction will nullify the active_buyer_id. This field will be used to fully support the Escrow system within the app. As well as this, when a transaction begins, the listing's status field is set to pending by using PostgresRPCs (Remote Procedure Calls).


Finally, the categories and events for today buttons underneath the search bar on the index page are now functional!

<img src="{{ '/images/easter/sorting.PNG' | relative_url }}" alt="sorting buttons work" width="300">
<img src="{{ '/images/easter/searching+sorting.PNG' | relative_url }}" alt="sorting buttons work with searching" width="300">

This was still a decent bit of work done, but my original roadmap had me finishing the code this week which I don't think is achievable. I didn't realise that the code and report for the project are due at the end of April, I thought I would have been able to submit the code and do the report afterwards so I have a good bit of work ahead of me because of this mishap.

Currently, the Escrow system is not fully in place yet. Most of the pieces are ready to work together to achieve this and I will begin bouncing money around between accounts ASAP. The entire search page needs to be done but that can be one of the last things I do. After a completed transaction/conversation, the user's need to be prompted to rate the other user. The conversation tab needs to be updated to allow the seller to set the agreed price, this will take a lot of inspiration from the way that Vinted acheieves communication between it's users. After all these key features are in place, anything after that will be a bonus!

It's going to be a difficult few weeks, but I believe I can wrap this up into a functional final product! 

