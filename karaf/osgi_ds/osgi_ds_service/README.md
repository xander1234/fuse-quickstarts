OSGi Declarative Services Publisher
====================================
This bundle defines a simple Hello World OSGi service using Declarative Services that can be consumed and used by other bundles. 

### Requirements:
 * Red Hat Fuse 7.6.0
 * Maven 3.0 or Greater (http://maven.apache.org/)
 * Java 8

Building
-----------------------
To build the project.

     mvn clean install

This will build the bundle including the manifest information.

Deploying to Red Hat Fuse
-----------------------

To start up Fuse browse to your fuse install directory. Then run

     /bin/fuse

This will bring up the fuse console. Once in the console you will be able to install your bundle. Usually we would install multiple bundles using a feature file, but in this case since we only have one bundle to install we can just install it using the file by the following command. Another option is to set up your local m2 repository in fuse in the fuse/etc/org.ops4j.pax.url.mvn.cfg file. Then you can use the mvn syntax below.

     karaf@root> osgi:install -s file:/home/yourUser/.m2/repository/com/redhat/consulting/fusequickstarts/karaf/osgi_ds/osgi_ds_service/7.6/osgi_ds_service-7.6.jar
        OR
     karaf@root> osgi:install -s mvn:com.redhat.consulting.fusequickstarts.karaf.osgi_ds/osgi_ds_service/7.6

 The -s here indicates to also start the bundle.  Alternatively you can omit the -s and after the install run

     karaf@root> osgi:start <bundleId>
     

Customizing the service message
------------------------

By default, the message returned by the service is OSGi service is "This is a Default Message". To customize this message, you can create a file called `com.redhat.consulting.fusequickstarts.karaf.osgi_ds.service.cfg` and place it in the `$FUSE_ROOT/etc` folder for the Config Admin Service

The file should have the following content:

```
message=<custom_message>
```

