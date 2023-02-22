Safetysheets for the Makerspace Leiden (http://makerspaceleiden.nl/).

Required:
	LaTeX (e.g. TexShop, etc).
	PDF reader.

Optional:
	(pip install) pywikibot for the image uploader to the wiki

Principle

1) safety-sheets.tex

	one entry for each machine called a MachinePage.
	Each MachinePage command needs 5 pairs of curly braces
		\machinepage{Name}{additional tokens}{specific instructions}{warning symbols}{footer information}
	Each warning symbol command takes 3 pairs of curly braces. These three commands exist because extracting the images from the Italian ISO document needs three different "offsets" within the pages in the ISO document
		\warn{iso page number}{title}{subtitle}
		\alert{iso page number}{title}{subtitle}
		\prohib{iso page number}{title}{subtitle}
	Certain symbols act as commands in LaTeX and need to be escaped, such as & should be written with \&.

2) base.tex
	
	macro's or `commands' that build the pages.

	machinePage - a page about a machine - see file for arguments.
		
		lots of 'if' statements to have the standard text
		no-noice after 19:00, dust extractor, etc all
		in one place.

	action, prohib and warn -- extractors for the images from
		the itialian ISO standard document. The numbers are
		the coordinates on the page.

	decal -- thing that actually extracts the images from the
		document. Has some funnyness as the gutter on the
		left and right page is difference; and hence the
		horizontal position of the image.

Changing things
