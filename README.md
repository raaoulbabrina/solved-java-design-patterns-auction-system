Download Link: https://assignmentchef.com/product/solved-java-design-patterns-auction-system
<br>
5/5 - (1 vote)

Implement a simple auction system. You may put the “auction server” and the “auction client” on the same machine.

The server will be used to maintain a list of items available for auction purchase. Clients will be allowed to make bids on available items or put new items up for auction. Clients can also be notified when the current bid on a particular item changes.

The server is an object which implements the following interface:

public interface IAuctionServer {public void placeItemForBid(String ownerName, String itemName,String itemDesc, double startBid, int auctionTime);public void bidOnItem(String bidderName, String itemName, double bid);public Item[] getItems();public Item getItem(String itemName);public void registerListener(IAuctionListener al, String itemName);}

These methods do the following:

public void placeItemForBid(String ownerName, String itemName,String itemDesc, double startBid, int auctionTime);/* Puts a new item up for auction by the owner with name ownerName.The itemName argument uniquely identifies the new item to be auctioned.If an item by that name already is up for auction in the server,an Exception is thrown. A description of the item is given bythe itemDesc argument. The starting (minimum) bid is given bythe startBid argument. The item will be available for auction forthe number of seconds given by the auctionTime argument. */

public void bidOnItem(String bidderName, String itemName, double bid);/* The bidder with name bidderName makes a new bid on the item specified bythe itemName argument. The bid amount is specified by the bid argument.For the bid to be accepted it must be higher than the current bid on thespecified item, else an Exception is thrown. */

public Item[] getItems();/* Returns an array of items available for auction.Each Item object consists of the owner’s name, item name,item description, current bid, current bidder’s name andtime remaining on the auction period for the item. */

public Item getItem(String itemName);// Returns the item for auction specified by itemName.

public void registerListener(IAuctionListener al, String itemName);/* Registers a listener with the auction server for changes in the itemspecified by the itemName argument. Whenever the current bid onthe specified item changes (or its auction period expires),the IAuctionListener is notified via its update() method. */

Any client object which desires to be notified of changes in the bid status of a specific item must implement the following interface:

public interface IAuctionListener {public void update(Item item);}

The update() method of this interface does the following:

public void update(Item item);/* Invoked by the auction server for each IAuctionListenerwhich has registered to be notified of changes in the bid status ofthe specified item. */

Use the above interfaces to write a working version of the auction application.

The application must implement the following design patterns:

• Observer PatternEach item for auction is an observable object. Do NOT use java.util.Observable to implement the Observer pattern here. Provide your own implementation. (Please explain why you chose the implementation method you used.)

• Abstract Factory PatternCreate the server object using a factory.

• Singleton PatternAllow only one instance of the server object to be instantiated.

.

Feel free to use any other patterns you feel appropriate.

Show the application with at least 3 auction items and 2 listener objects.