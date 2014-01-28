Hackathon Textbook App
=========
Design Spec
----

> Purchase & sale of used textbooks with privacy and easy transactions.

A solution to the maze that is textbook buying & selling.  

Problems with current system:
- Personal information must be given out (phone #, email address) so that other person can contact you.
- Sales must be done in cash, so this requires getting cash (ATM) and having change
  - The person never has the right bill denominations/amount, tries to haggle, etc.
- There isn't really a way to "list" yourself as wanting a certain book, to be notified when it is posted.
- Similarly, it is difficult to list **exactly** the book you are selling.

Solution:
- An app/website combination that allows for easy (read: no password, some other method of auth) account creation & login
- Easy posting of books, complete with:
  - Title
  - Author
  - Version
  - Class (eg. ECE 240)
  - Price
  - Condition
- Can list yourself as "looking for **X**", where **X** is the book for a certain class. 
  - eg. Need textbook for [CHEM] [101], or
  - eg. Need [Silberberg 13th Ed.]
- User can contact seller with an *offer* of a certain price, and offer a place & time to meet up.
    - Buyer either declines (and life goes on), or:
    - Buyer accepts and picks a time & place, or suggests other options
- Purchase:
  - Buyer & Seller meet up, Buyer has a chance to check condition of the book.
  - Buyer scans QR code of Seller (generated dynamically?), and enters password or some sort of auth.
  - PayPal is used to handle the payment.
  - Both parties get a receipt emailed to them.
  - Done!
    - Note: (BUMP API is no longer available as of 1/31/14)

Tech
-----------

Objective-C on iOS for the prototype.  
Remote server database (SQL probably, have to hit it with API requests from app) for storage of *listings*, *users*, etc. Maybe use [Kumulos](http://www.kumulos.com/) as a database backend - they offer tables in the cloud that you can hit with API calls from iOS.  
[PayPal API](https://developer.paypal.com/docs/classic/lifecycle/apps101/) for transactions (iOS version **or** [REST HTTP](blog.strikeiron.com/bid/63338/Integrate-a-REST-API-into-an-iPhone-App-in-less-than-15-minutes) version, will have to research)  
[Firebase](https://www.firebase.com/docs/security/simple-login-ios-email-password.html) for authentication  
Some kind of chat functionality for communciating between buyer & seller

Minimum Viable Product
-----------
iOS app that allows for:
- Anonymous browsing of listings (dummy database)
- To post a listing **or** to make an offer on a listing:
  - Must create an account
- QR scan -> fake paypal transaction

Business
-----------
The app could be monetized fairly easily. Two important things:  
1. **DO NOT TAX THE BUYER**. Buyer interest will be the only thing that makes the service worth anything.  
2. **DO NOT TAX THE AVERAGE SELLER**. It needs to be dead simple to sell something. If you want extra options/sticky listings/whatever, those can be monetized.

Monetization options:
- "Featured listings" aka sticky listings that stay at the top of pages.
- "Bump" aka pushing your listing back to the top of recent (have rules to not be abused)
- Others probably, I'm not a business guy.    
