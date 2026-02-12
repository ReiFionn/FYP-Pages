---
layout: post
title:  "New Pages New Tables"
date:   2026-02-04 16:57:01 +0000
categories: project update
---

I have added the remaining screens I believe that I will need, including porting over the messaging functionality that I had for my demo in semester 1, I changed up the look on each page to use the theme, and I modified the tabs bar to represent each new page, as well as keeping the page used for messaging hidden.

<img src="{{ '/images/IMG_3563.PNG' | relative_url }}" alt="New Index Page Look" width="300">
<img src="{{ '/images/IMG_3564.PNG' | relative_url }}" alt="Messaging Ported Over" width="300">

I need to try sort out the white still appearing at the top and bottom of the screen.

I began working on adding listings into Supabase, by first writing out some ideas for how I would like it be structured and what's included within each listing:

<img src="{{ '/images/IMG_3565.PNG' | relative_url }}" alt="Listings V1" width="300">
<img src="{{ '/images/IMG_3566.PNG' | relative_url }}" alt="Listings V2" width="300">

I then consulted Gemini to see if the structure I had was on point for the project. Gemini suggested breaking my current idea into two separate tables - one for the listing and one for the event that the listing is for. I opted for this, as having the events as a separate table will allow easier searching and filtering in the future. On top of this, Gemini suggested using "jsonb" for the field I made to be used by future AI integration to determine the tickets original price "original_purchase_metadata". jsonb stores JSON data in a binary format, allowing each field to not have to be defined, the option to add new fields in the future, and each field can be queried. This seemed ideal so I incorporated this too. 

To finish adding these two tables, I enabled RLS on the listings table.

<img src="{{ '/images/image.png' | relative_url }}" alt="Current Supabase Database" width="300">