This guide shows how you build your own app using the Coin.Kred API.

## Home Page
<p align="center">
  <img width="80%" src="https://files.readme.io/68ba12d-CK_Explore.PNG" title="Explore">
</p>  

Our home view is the Explore tab.   We've created this with three calls to the [/coins](https://docs.coin.kred/v1.0/reference#coins)  method, sorting respectively by likes, creation date, and circulation.  Each of these calls can be paginated, so that the groups of coins are bound to individual carousels and can be browsed by the user.

<p align="center">
  <img width="80%" src="https://files.readme.io/01f0755-CK_Marketplace.PNG" title="Marketplace">
</p>  

The Marketplace tab is created using a single call to a specialised method [/marketplace](https://docs.coin.kred/v1.0/reference#marketplace).  This call merges, filters, and sorts active sales and auctions to present a single unified view.  We use pagination again to provide infinite scroll, preloading pages on desktop to ensure smooth loading of additional coins.

<p align="center">
  <img width="80%" src="https://files.readme.io/01f0755-CK_Marketplace.PNG" title="Marketplace">
</p>  

The Collection tab shows the user's own collection of coins - coins they have created, bought at sale or auction, claimed from giveaways, been gifted by other users.  This view is another call to [/coins](https://docs.coin.kred/v1.0/reference#coins), simply specifying the user, and supporting infinite scroll.

The same call can be used to embed the user's collection in other pages - their Engagement Profile, blog, or other home page.

<p align="center">
  <img width="80%" src="https://files.readme.io/ee9e8ab-CK_Newsfeed.PNG" title="Collection">
</p>  

The Newsfeed tab combines several functions: A feed of coin activity related to the user - coins created, requests from other users, coins received and sent, sold and auctioned.  This is provided by the [/messages](https://docs.coin.kred/v1.0/reference#messages) call, requesting the user's timeline.  The [/messages](https://docs.coin.kred/v1.0/reference#messages) call can also be used to view messages relating to any single coin (or batch of coins if the coins are in a mesh network).

The Pending widget uses [/remind](https://docs.coin.kred/v1.0/reference#remind) to list reminders for actions started but not yet complete.

The Search Contact widget uses the SocialOS Contact API (documented separately).

<br><br>

## Batches and Coins


<p align="center">
  <img width="80%" src="https://files.readme.io/f8a39eb-CK_Batch1.PNG" title="Batched View">
</p>  

Clicking on a coin that is part of a batch brings up the batch view.  We use the *batched* parameter in [/coins](https://docs.coin.kred/v1.0/reference#coins) and [/marketplace](https://docs.coin.kred/v1.0/reference#marketplace) to show a single entry for each batch along with the number of coins available (total in the Explore tab, and just the number on sale in the Marketplace tab).

<p align="center">
  <img width="40%" src="https://files.readme.io/d79c8a4-Spacecoin.png" title="Batched coin">
</p>  

From the batch view we can edit certain details for all coins in the batch:

Add and edit tags using [/tag](https://docs.coin.kred/v1.0/reference#tag)
Hide or show the coins using [/hide](https://docs.coin.kred/v1.0/reference#hide) and [/show](https://docs.coin.kred/v1.0/reference#show)
Make the coins private or public using [/private](https://docs.coin.kred/v1.0/reference#private) and [/public](https://docs.coin.kred/v1.0/reference#public)
Showcase the coins (if the user has showcase privileges) using [/showcase](https://docs.coin.kred/v1.0/reference#showcase) and [/unshowcase](https://docs.coin.kred/v1.0/reference#unshowcase) 
Update metadata such as the coin description and link using [/meta](https://docs.coin.kred/v1.0/reference#meta)

Specifying the batch on these API calls allows you to update all the coins in the batch that you own.

<p align="center">
  <img width="80%" src="https://files.readme.io/d5db70a-CK_Batch2.PNG" title="Batch edit">
</p>  

We can give a coin from this screen, either directly to an on-platform user using [/send](https://docs.coin.kred/v1.0/reference#send) or to any user via Email, SMS, or Twitter using [/hold](https://docs.coin.kred/v1.0/reference#hold).

[/hold](https://docs.coin.kred/v1.0/reference#hold) uses a two-step processes, reserving the coin, creating a secure code, and notifying the recipient via the designated method.  The recipient can then log in to the app, which will use the [/claim](https://docs.coin.kred/v1.0/reference#claim) method to accept the sent coin.
