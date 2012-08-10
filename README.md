Turt2Live Pages
===============

A small API for creating in-game pages to send to people.

This can be run as a plugin or compiled into a plugin for use.

API Use
-------

If you are compiling the source into your own plugin, you must put it under your package (eg: com.you.plugin.pages).

To create an easy pagination, simply do the following:

```java
// Setup lines
List<SimpleLine> myLines = new ArrayList<SimpleLine>();
myLines.add(new SimpleLine("line 1"));
myLines.add(new SimpleLine("line 2"));
myLines.add(new SimpleLine("line 3"));

// Create pagination
Pagination pageination = new Pagination(myLines);

// Setup (the 3 colors are to define menu colors. Play with them to see what happens!)
String title = "My Title";
String prefix = ChatColor.GRAY + "[Prefix]";
ChatColor mainColor = ChatColor.DARK_GREEN;
ChatColor titleColor = ChatColor.GREEN;
ChatColor pageColor = ChatColor.GREEN;

// Generate the pagination
pagination.generate(title, prefix, mainColor, titleColor, pageColor); 

// As an example, we'll send the pagination (page 1) to everyone online
for(Player player : Bukkit.getOnlinePlayers()){
	pagination.showTo(player, 1);
}
```

That's it!

If you want more control over the style in Pagination, extend Pagination yourself and set it, like so.

```java
public class MyPagination extends Pagination{
	
	public MyPagination(List<? extends Line> lines, Style style){
		super(lines);
		super.style = style; // Here is where the style is set
	}
	
}
```

Of course there are more things you can override, simply take a look at the [JavaDocs](http://jd.t2ldev.com/PagesAPI) to play with the API!