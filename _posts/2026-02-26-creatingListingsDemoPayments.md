---
layout: post
title:  "Creating Listings & Demo Payments"
date:   2026-02-26 16:57:01 +0000
categories: project update
---

I didn't mean to leave such a large gap between my last update, but rest assured I have been chipping away at the project and have made some good strides!

To start, I have created a new page for creating listings. Each listing requires an Event Title, a Price, the event's Date & Time and Venue. The Date & Time is chosen using
a datetimepicker. The venue is a bit more technical. I debated having the user enter minimal details about the venue (probably just the name) and then having some AI agent figure out the address of that venue and fill out the rest of the details for the listing, but after taking this idea to Gemini, it suggested that I use GooglePlacesAutocomplete. GooglePlacesAutocomplete allows the user to almost "search" in the text box for the venue the event is taking place at, it will begin to autofill suggestions and the user can select one. From this, the API will give a big JSON file that can be picked apart for seperate components (like the fields I have in the events table!). This is a really good solution to the problem I was facing and I chose to follow through with it as it didn't seem too difficult to implement and I get to use another API in the app! Here is what the new create listing page looks like:

<img src="{{ '/images/create_listing.PNG' | relative_url }}" alt="New Create Listings Page" width="300">

Following this, I added some bits to refresh the listings on the home page whenever the user navigates there or when they scroll down from the very top. The listings are also more compact. 

<img src="{{ '/images/new_listings.PNG' | relative_url }}" alt="New Listings Page" width="300">

Each individual listing can now be clicked on and the user will be brought to the page for that listing, where I will put all the details of the listing in the future. This page will also have the buttons to begin a transaction to purchase the ticket for the listed price or begin a conversation with the seller to negotiate a price. 

<img src="{{ '/images/indiv_listing.PNG' | relative_url }}" alt="New Individual Listing Page" width="300">

Speaking of purchases, I have added Stripe integration into the app! I added a new field for profile in Supabase called stripe_customer_id to be used in the future and keep all user iteractions tied to the one profile. I have a test page for payments that allows the user to "checkout" for nothing, but all the API calls are in place to begin testing soon. I am currently waiting for my GitHub Education benefits to come into effect so I can start using up to $1000 on my Stripe account to mess around with transactions. 

<img src="{{ '/images/demo_paymenty.PNG' | relative_url }}" alt="Demo Purchasing Page" width="300">

Currently the app is still pretty bare bones, I haven't put any effort into the design really and a lot of the text is almost unreadable but I'm trying to get the basic functions on the entire app in place before beginning to tidy everything up. I still need to implement full CRUD on the listings and get my Stripe account sorted to be part of the escrow system. I NEED TO FINALIZE AN IDEA FOR TICKET TRANSFERS!!! Those are probably my biggest issues at the moment, other than that I am chugging along nicely! :D
