---
layout: post
title: "Final Update?"
date:   2026-04-27 18:51:00 +0000
categories: project update
---

We are on the home straight now! 

To start, each page received a UI overhaul, which can be seen in each of the screenshots! I'm stating this now, despite it happening later in development than
the first few updates I will cover.

Shortly after the previous post on this site, I managed to add full offer functionality in conversations for listings that are owned by the other user.
Offers can be withdrawn, accepted or declined. Once an offer has been accepted, the listing's status becomes "pending" and the buyer can proceed to 
checkout with this new price. 

Offers function by using a JSON as the "body" column in the conversation_messages table. This JSON is parsed and contextually displayed in the conversation depending 
on who is the buyer and who is the seller. A new column was added to the conversation_messages table called "message_type" which is used when rending the conversation 
to correctly display the message's text.

Once an offer has been accepted, the user proceeds to checkout like they would if they were buying the listing directly on the listing's page. 

The header of the conversation has been changed to display the other user's display name and profile picture, upon clicking on it the user will be redirected
to a new page for viewing other user's profiles, userId (more on this later...).

<img src="{{ '/images/finalquestionmark/ohterUserIdScreen.PNG' | relative_url }}" alt="otherUserIdScreen" width="300">
<img src="{{ '/images/finalquestionmark/offers.PNG' | relative_url }}" alt="offers" width="300">


I have also moved the checkout logic into a new hook: useCheckout. This is to be able to easily reuse this functionality across multiple pages. 

Agorex has been linked to the Expo website to be able to send notifications to users. When a user first logs in on a new device they will be prompted for
notification privileges. When a listing is sold and the funds land in the Agorex's Stripe account, the seller receives a notification requesting them to pass 
the ticket onto the buyer.

Once a buyer has sent their money to Stripe to buy a ticket, the listing changes to sold and the view changes so that the seller receives a button to confirm that they have sent the ticket, and the buyer's view has a button to confirm the ticket has been received. Buyers cannot confirm that a ticket was sent until after the Seller confirms that they have sent the ticket. 
If anything were to go astray in this transaction, users are able to submit reports where they fill out a text box and select an option that best matches their issue. These
reports are insert into the new support_tickets table. One field of reports is the ai_investigation_report, which is filled out by a response from Google Gemini after
sending it a lengthy prompt that includes all information about the users, the conversation and the transaction. Once this response has been inserted into the table, an RPC
is used to send the ticket to a Slack channel of Agorex admins for them to resolve. During different stages of the transaction, "system" messages will be inserted into the conversation between the two users to prompt them to complete their next steps.

<img src="{{ '/images/finalquestionmark/buyer1.PNG' | relative_url }}" alt="" width="300">
<img src="{{ '/images/finalquestionmark/seller1.PNG' | relative_url }}" alt="" width="300">
<img src="{{ '/images/finalquestionmark/buyer2.PNG' | relative_url }}" alt="" width="300">
<img src="{{ '/images/finalquestionmark/seller2.PNG' | relative_url }}" alt="" width="300">
<img src="{{ '/images/finalquestionmark/notifications.PNG' | relative_url }}" alt="" width="300">

Users are now able to view they past and present listings from their profile by clicking on the "Manage my Listings" button. Each listing has a badge that displays the 
status of the listing in the transactional flow: Active, Pending, Expired, Needs Transfer, Awaiting Buyer, Rate Buyer, Complete. 

<img src="{{ '/images/finalquestionmark/userListingsScreen.PNG' | relative_url }}" alt="" width="300">

User's can avail of simple user settings by clicking the gear icon on the top right of their profile. Current options include: changing display name, and onboarding for
Stripe Connect... 

Releasing funds to Sellers now works by using an Edge Function and Stipe Connect. Users are required to create a Stripe Connect account in order to receive funds. The
ID created by Stripe is saved to user in the new column on the profiles table: stripe_account_id. 

<img src="{{ '/images/finalquestionmark/userSettingsScreen.PNG' | relative_url }}" alt="" width="300">


After a transaction has completed, users are prompted to rate each other. The ratings involve providing a star rating out of 5 and an optional message. These reviews
are then used to calculate the user's average trust rating, and they are displayed on the user's profile. 

<img src="{{ '/images/finalquestionmark/buyerRate.PNG' | relative_url }}" alt="" width="300">

If at some point during the transaction, the Buyer has sent their funds and the Seller has confirmed that they have sent their ticket to the Buyer, if the Buyer is not responding to 
messages and the date for the event of the ticket passes, the funds are automatically sent to the Seller's account. 

The search page has been fleshed out to allow users to search for listings by event titles, venue names or cities, filter by category or date range, and sort by recently 
added, price low to high or high to low. 

<img src="{{ '/images/finalquestionmark/exploreScreen.PNG' | relative_url }}" alt="" width="300">

Now when a user creates a listing, a check is done to see if the even has been created before. If it has, a new event isn't created and that event is attached to the 
listing. If an event that was previously queried by Gemini to determine a price, that price will be reused UNLESS the listing is for a different ticket type. 

Users are no longer required to be authenticated to browse listings, but will be required to have an account to create a listing, message users or view their profile. 

When viewing a listing, the Seller is now prominently displayed using their display name, profile picture and trust rating. When a user clicks on this card, they will be redirected 
to a userId.

<img src="{{ '/images/finalquestionmark/listingIdScreen1.PNG' | relative_url }}" alt="" width="300">
<img src="{{ '/images/finalquestionmark/listingIdScreen2.PNG' | relative_url }}" alt="" width="300">

On this userId page, users can view the current listings and reviews of users. 

<img src="{{ '/images/finalquestionmark/profile.PNG' | relative_url }}" alt="" width="300">

The minimum amount for listing prices was changed to 50 cent to cater for Stripe's minimum transaction. 

Signing up now allows you to set a display name, with a check in place to see if that display name is unique. 

The traffic light colour coding was tweaked to make the margins between each colour larger for a better effect. 

Other general cleaning/fixing bits and pieces were done.

I have just about finished my project report, I have just sent what I have currently onto Rob to assess. Once that is done, I will tweak the document, record my demo and that
may be it for the project! If I have any fixes I need to add I will detail them in a new post after this, but for now this is the final update for Agorex!