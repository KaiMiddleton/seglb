seglb
=====

Super Epic Gallery - Light Box

Goals:
------------------------------
- ultra lightweight
- independant of any JS library, like jQuery etc
- simple to use for simple tasks
- low level functions -> more power to let user do more complicated things,
  while keeping the library itself light

Features:
------------------------------
- lightweight light box
- darken background
- center LB content
- close button
- next/back button
- closes when you click the background
- goes to next picture, when you click the current picture
- hides the niavigation when using a direct fill

Notes:
------------------------------
####List/Group of items/pictures:
A list of files which you can navigate, meaning you click on one
of the pictures and can then navigate back and fourth between those pictures.
seglb calls these a list, and to make use of this you have to first pass
a list of content items, usually a list of pictures to seglb, which you
do as follows:

The seglb object, it's functions and variables:
------------------------------
you could just read the code it's only like 16 lines of code but whatever:
* `show(bool i, bool n)` - "i" is used to decide wether to show or hide
  the light box, true means show and false means hide, usually you use,
  1 = show and 0 = hide | "n" is used to specify if you wanna clear the
  lightbox in addition to showing or hiding it, you will usually do this
  when you hide it, to for example interrupt videos that are running in
  the lightbox, for how clear works see: clr()
* `chide(bool n)` - is the conditional hide used for the effect that
  clicking the background hides the light box, if checks wether the bghide
  variable is true, and if it is it runs show(0,n), for the use of "n"
  see show(). If, bghide is false it chide() does nothing. More info see bghide
* `clr()` -  fills the lightbox with a space " ", used to interrupt things
  like videos to stop them from playing when you close the lightbox
* `fill(string f, bool i)` - fills the light box with content that is either passed
  via the variable "f", this seglb calls a "direct fill" or if a list is being used
  fill() takes the current position "pos" and uses it to take that item out of the
  active list and use that to fill the lightbox.
* `nav(int i)` - move the current position in the current list by that value
  meaning to mvoe to the next picture it would be nav(1), to move to the previous picture
  it would be nav(-1), you can obviously also jump by multiple pictures, it then
  tells fill() to refill the box according to the new list position, usually
  used by the "next" and "back" button
* `navs(bool i)` - navigation status, "i" specifies wether the navigation should be shown or not
  true = show navigation, false = hide navigation, fill() for example sets this to
  false if you use a direct fill, since there is only one fill in that case
* `load(string clist,int pos,bool i)` - used to load a picture from a list
  and fill it into the light box "clist" here is the list name you
  specified when using addList(), "pos" describes which item of the list
  it should show, if "i" is true it will also trigger show(1),
  displaying the light box.
* `setpos(int i)` - mainly used by nav() and load(), it sets the current position
  in the current list to "i", but also checks if "i" is 0 or lower it sets
  "pos" to the last item in the list, if "i" is larger than the amount of items
  in the list, it sets it to the first item in the list so 1.
* `addList(string name, array items)` - adds a list to which you can then
  use to move inbetween the items on the list, you can jump into a list using
  load(), "name" is the name under which the list is saved, it needs to
  be unique, or else it will override the list with the same name, it is
  used by load to identify which list should be used.
  "items" - is the set of objects that is passed, meaning the actual list,
  a list could look like this:
  `['<img src=\'http://kai.middleton.de/flower.jpg\' />', <img src=\'.../flower.jpg\' />]`
  as you can see this list contains 2 items.
* `pos` - contains the current position in the current list
* `a` - contains the currently active list, is empty when no list is in use
* `l` - contains all lists passed to seglb via the addList() function.
  
  

Examples:
------------------------------
**Fill** the lightbox with "hello":

    seglb.fill('hello');

**Fill** the lightbox with "hello" and display it:

    seglb.fill('hello',1);

**Fill** the lightbox with "hello" and display it:

    seglb.fill('hello',1);
  
**Fill** the lightbox with the img "http://www.middleton.de/kai/flower.jpg" and display it:

    seglb.fill('<img src=\'http://kai.middleton.de/flower.jpg\' />',1);
    
Alternative

    seglb.fill('hello');seglb.show(1);
  
**Display** the lightbox

    seglb.show(1);
  
**Hide** the lightbox

    seglb.show(0);
  
**Empty**/clear the lightbox

    seglb.clr();
    
Alternative

    seglb.fill(' ');
