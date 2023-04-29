Safetysheets from the Makerspace Leiden (http://makerspaceleiden.nl/).  
Now adapted for Bristol Hackspace (https://bristolhackspace.org/).

### Compiling 
Option A: use GitHub Actions to compile the LaTeX online.

Option B: download and run the repository locally.
Required:
	LaTeX (e.g. TexShop, etc).
	PDF reader.

Optional:
	(pip install) pywikibot for the image uploader to the wiki

### Principle

1) safety-sheets.tex

	Contains one entry for each machine called a MachinePage.
	
	Each MachinePage command needs 5 pairs of curly braces
	
		\machinepage{Name}{additional tokens}{specific instructions}{warning symbols}{footer information}
	
	Each warning symbol command takes 3 pairs of curly braces. These three commands exist because extracting the images from the Italian ISO document needs three different "offsets" within the pages in the ISO document  
		\warn{iso page number}{title}{subtitle}  %Page 49 to 74
		\alert{iso page number}{title}{subtitle}  %Page 75 to 106
		\prohib{iso page number}{title}{subtitle}  %Page 107 to 135
		There is no command for the green safety symbols (yet).

2) base.tex
	
	macro's or `functions' that build the pages.

	machinePage - a page about a machine - see file for arguments.
		
		lots of 'if' statements to have the standard text
		no-noice after 19:00, dust extractor, etc all
		in one place.

	action, prohib and warn -- extractors for the images from
		the itialian ISO standard document. The numbers are
		the coordinates on the page.
		Of note: symbols/pages 88, 77, and 107 have non-standard symbol heights, so they use a different "command" to what you might expect. This *should* be made clear in the tex files, but isn't always!

	decal -- thing that actually extracts the images from the
		document. Has some funnyness as the gutter on the
		left and right page is different; and hence the
		horizontal position of the image.

### Changing things
When compiling (in a LaTeX desktop app or using GitHub Actions, LaTeX can sometimes fail. This is generally due to a syntax error, and all applications should give you access to the errors. You can use these to pinpoint where the issue is and what it might be, although fixes sometimes take trial and error. Ask Google or the forum for assistance.


LaTeX notes:
LaTeX has special characters: # $ % & \ ^ _ { } ~. Most of them can be escaped prepending a simple backslash, but \, ^ and ~ need special escapes.
Pasting URLs in to LaTeX will likely require modifications before it will compile properly.
