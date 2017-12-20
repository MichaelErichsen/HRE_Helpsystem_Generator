Convert Word to Eclipse Help System

Create Eclipse Development Environment 

In your Eclipse goto “Install Software” and install “Eclipse XSL Developer Tools”.

Install a Web Page Editor:

Install new software...

http://download.eclipse.org/releases/xxxx/

Select Web Page Editor

Download Docbook 4.5 from http://www.oasis-open.org/docbook/xml/4.5 [direct link: http://www.oasis-open.org/docbook/xml/4.5/docbook-xml-4.5.zip] 

https://www.oasis-open.org/docbook/xml/5.0b5/docbook-5.0b5.zip 

Download XSLT stylesheets from http://docbook.sourceforge.net. I used version 1.79.1
       
2. Create a project 

Create a general project

Configure – Convert to Plug-in project

Import from file system org.apache.xalan_2.7.1.v201005080400.jar, org.apache.xml.serializer_2.7.1.v201005080400.jar, and org.eclipse.wst.xsl.core_1.1.301.v201405151730.jar

Xalan 2.7.2

(or the relevant versions) to the root of the project.

Import docbook-xml-4.5 and docbook-xsl as folders.

Create the following subfolders: odf, docbook, eclipsehelp, and stylesheets.

Import Odt2DocBook.xsl to the stylesheets folder, docbookbuild.xml to docbook, and eclipsehelpbuild.xml to eclipsehelp

Import eclipse33.xsl to docbook-xsl/eclipse

3. Transform a Word Document 

Edit Microsoft Office Word Document 

Edit a document and define 1-4 header levels

Save it as Open Document Text (odt)

Extract text and images 

Unzip the odt document, e.g. using 7-zip, into a separate folder

Transform into DocBook Format 

Import content.xml from the unzipped file into the odf folder

Edit and run DocBookBuild.xml as an Ant Build

Note that you should set JRE to Run in the same JRE as the workspace in Run, External Tools , External Tools Preferences tab JRE

Check the output in the docbook folder

Rename .tmp files in the media folder to .png

Convert to Eclipse Help System 

Edit and run eclipsehelpbuild.xml as an Ant Build, again using the same JRE as the workspace.

Import the media folder as a subfolder under the html folder.

Add to HRE Help system 

Create a new folder in the HRE Help system project html folder and import the contents of the generated html subfolder.

Rename the images and copy them to the images folder.

Rename toc.xml and copy it into the xml folder. Edit it in the Table of Contents editor by changing “Name” to the image title, “Anchor” to an anchor name in a higher-level table of content, e.g. “toc.html#toolbox”, and specify the location of the index.html file in the html subfolder

Edit the higher-level table of content to include the new table of content and HTML pages.

Switch to source mode and change all href=”html/… to the html subdirectory under the new folder.

Each new table of contents needs to be registered in the plugin.xml file, while unselecting “primary”.
