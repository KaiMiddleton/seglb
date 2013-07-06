seglb
=====

Super Epic Gallery - Light Box

Features:
  - lightweight light box
  - darken background
  - center LB content
  - close button
  - next/back button
  - closes when you click the background
  - goes to next picture, when you click the current picture
  - hides the niavigation when using a direct fill
  
Examples:

*Fill* the lightbox with "hello":
 seglb.fill('hello');

*Fill* the lightbox with "hello" and display it:
 seglb.fill('hello',1);
Alternative
  seglb.fill('hello');seglb.show(1);
  
*Display* the lightbox
 seglb.show(1);
  
*Hide* the lightbox
 seglb.show(0);
  
*Empty*/clear the lightbox
 seglb.clr();
Alternative
 seglb.fill(' ');
