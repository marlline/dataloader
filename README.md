## DATA LOADER README 

---------------------------------------------
I.  Building Data Loader
---------------------------------------------

There are two "out of the box" ways to build Data Loader.

The first way is to use Eclipse to build Data Loader.  Go to File->Import->Import Existing Project.  Choose the base directory and it should find the dataloader project. Before you do this you need to follow the instruction below for the ant build and run the "ant pre" target.

The second way to build Data Loader is through apache ant.  This requires that you have ant and perl installed.  Go to the build directory and edit the build.properties file.
Set the values for ANT_HOME, JAVA_HOME, and app.home.  Also, if your files are not on the c: drive, then you'll need to set the home.dir as well.  Open a command prompt, and from the build directory
you can issue ant commands to build Data Loader.  The current commands are:

* ant partnerwsdl  - 

* ant jar_partnerwsdl - Generates the Java src from the partner.wsdl, compilers, and jars the partnerwsdl code.  Use this task if you need to use a new WSDL.

* ant compile - Compiles the Data Loader src.

* ant compile_test - Compiles the Data Loader JUnit test src.

* ant compile_all - Compiles all the Data Loader src, including the WSDL jar.

* ant jar_dataloader - Creates one jar with all the necessary classes.  Most of the time you will only want to run this command.

* ant run_dataloader - Runs the GUI Version of Data Loader

* ant run_process - Runs the command-line version of Data Loader and uses the config.properties file

* ant test - Runs a JUnit test. The -Dtestcase switch can be used to specify the test file or class to execute.

* ant autobuild - Compiles and runs a JUnit test suite and sends email specified by the test.emailToList property via mailhost in testEmail target. See autobuildWeekly for an example of how to do that.


II. Running Data Loader
---------------------------------------------

To run the Data Loader you must have Java 1.5.0_06 or a later version of Java 1.5.0 installed.

Put the dataloader jar and the swt libs - swt-awt-win32-3063.dll, swt-awt-win32-3062.dll, and swt-win32-3062.dll in the base directory.

To run the Data Loader GUI, use the command:

java -Xms64m -Xmx512m -DentityExpansionLimit=128000 -Dsalesforce.config.dir=CONFIG_DIR -classpath "%cd%\DataLoader.jar" com.salesforce.dataloader.process.DataLoaderRunner

If you don't specify the salesforce.config.dir, then Data Loader looks in the base dir.  The config files are log-conf.xml, process-conf.xml, database-conf.xml, and config.properties.


To run the Data Loader from the command line, use the command:

java -Xms256m -Xmx384m -Dsalesforce.config.dir=CONFIG_DIR -classpath DataLoader.jar com.salesforce.dataloader.process.ProcessRunner

The command-line version runs with whatever properties you have in your config.properties file, but you can also pass paramters at runtime as arguments to the program.

For example, the following command sets the operation to insert regardless of what settings are contained in the config.properties file:

java -Xms256m -Xmx384m -Dsalesforce.config.dir=CONFIG_DIR -classpath DataLoader.jar com.salesforce.dataloader.process.ProcessRunner process.operation=insert

The process-conf.xml file can be used to define properties for multiple processes.  Look at a sample\conf\process-conf.xml for examples on how to configure it.  The way to run a process defined in process-conf.xml is to specify process name on command line like this:

java -Xms256m -Xmx384m -Dsalesforce.config.dir=CONFIG_DIR -classpath DataLoader.jar com.salesforce.dataloader.process.ProcessRunner process.name=opportunityUpsertProcess


III. Resources
---------------------------------------------
For more information see the [wiki](http://wiki.apexdevnet.com/index.php/Tools), or the [Data Loader Developer's Guide](https://na1.salesforce.com/help/doc/en/salesforce_data_loader.pdf) 

Questions can be directed to the [open source forum](http://boards.developerforce.com/t5/Open-Source/bd-p/sforceExplorer)

