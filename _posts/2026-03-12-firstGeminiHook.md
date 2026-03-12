---
layout: post
title:  "First Gemini Hook & More!"
date:   2026-03-12 23:26:01 +0000
categories: project update
---

Since my previous post I've been able to bang out a good collection of little bits and pieces! 

I've been working away mostly with the listing creations. I've added my first Gemini AI hook into the project to be able to fill the ai_suggest_price field of listings. It was fairly easy to implement, and along with Gemini's help,  it was a painless process. 

Now when a user goes to create a listing, they have a few fields to fill in that are about the original purchase of the ticket they are reselling. Currently the fields are: platform of purchase, data & time of purchase, and an optional proof of puchase image upload. These fields are then used to engineer a prompt to post to Gemini so it responds with what would have been around the price to purchase that ticket for at that time. 

This price is then used to choose a colour for the price that is displayed with the listing on the home page. I'm using a three colour system to quickly indicate to users how fair of a price the ticket is currently being listed for: red means the ticket is being listed for +10% and above what Gemini determined the price to be, orange is between +5% and +10%, and green is anything lower than that!

<img src="{{ '/images/traffic.PNG' | relative_url }}" alt="AI Price Three Colour System" width="300">

I plan on having alerts sent to the user if they list a ticket too high or when they set the price super low. If the price is super low the user will just be asked to confirm they want to set that price, if its super high the user WILL NOT be allowed to create that listing. 

I have also added a dropdown menu for choosing a category/genre when creating a listing. 

I spruced up the theme a bit so I can get some nice screenshots for my poster that's due this month.

<img src="{{ '/images/new_theme.PNG' | relative_url }}" alt="New Theme" width="300">

The test payment logic now works with the buy button on each listing's page, with the price being set as what the current listing's asking price is. 

I also managed to remove the white bars that appeared at the top and bottom of the screen, but I would still like to fix the elevation of the tabs bar at the bottom.

<img src="{{ '/images/no_bars.PNG' | relative_url }}" alt="No Bars" width="300">

My current list of things to do includes:
- have checks for multiple events in Supabase (if a listing is created for an event that already exists, then do not create a new event)
- add functionality to the sorting/searching functions on the home screen
- basic profiles page created
- make offer button on listings page will create a conversation between the buyer and the seller, then this conversation can always be accessed from the messages tab
- have Gemini parse the uploaded proof of purchase image (when applicable) in order to find further details on the purchase/verify information the user entered.
- more safety checks on the Gemini calls to ensure they won't end up breaking the system
- have Gemini retrieve images for listings
- have the listing's ticket details explained on it's page
- tidy up the create listings page
- establish the escrow system functionality between the app, supabase, and stripe