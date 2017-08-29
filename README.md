# Force.com Migration Tool Starter Kit
Before installing FMT, you'll need to install Java and Ant as prerequisites. The instructions for the FMT install guide begin here. After installing everything, make sure your environment paths are set for Java and Ant, and be sure to copy the salesforce.jar from the FMT download into your Ant /lib/ folder. 

Without any experience with ant, the contents of these folders may be a little overwhelming. The workhorses in each folder are build.xml, build.properties, and /src/package.xml. The .bat files I'll cover last.

### build.properties
Who and Where? User and SF Environment.

Set your login credentials and target environment url (either test.salesforce.com or login.salesforce.com) Notice no quotes on the values here, and the password is your password concatenated with your security token.

### /src/package.xml
Which SF metadata? Explicitly defines deployable SF Metadata by metadata type and component name.

Within the /src/ folder is the package.xml. This is the explicit definition of what SF Metadata Types you wish to operate with from the build.xml. If my package.xml only contains a single profile, then only this profile will be processed by the task from the build.xml.

Often I will begin my work with a copy of the package.xml from our repository which contains everything. Then I will remove all items I don't want, until I am left with a package.xml that contains only the items I want to retrieve or deploy.

### build.xml
What to do? Deploy or Validate, with or without tests.
References the build.properties file for various `sf.` variables like `sf.username`.
References the /src/package.xml for the list of SF metadata to operate against.
Defines tasks, known in ant as targets, to be run against your desired SF environment. Tasks such as Deploy with tests, without tests, validate only, validate only with tests, or simply retrieve.

The build.xml I have shared is a custom build file that I have created from the FMT's sample build.xml.
