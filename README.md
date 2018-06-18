cs-studio-SNS
=============

SNS specific additions and build for CS-Studio


Example for compiling the SNS products
--------------------------------------

 1) Somewhere on your computer, execute what's in build/get_all.sh .
    As a result, you should have a directory with these sub-dirs:

    diirt
    maven-osgi-bundles
    cs-studio-thirdparty
    cs-studio
    org.csstudio.display.builder
    org.csstudio.sns

 2) `cd org.csstudio.sns/build`
 
 3) `source setup.sh`
 
 4) `sh make.sh`
   Note that this build setup is self-contained.
   You can start out without any `~/.m2` directory,
   in fact you may want to delete an existing org.csstudio.display.builder
   to assert a clean plate.
   Maven is invoked with the `settings.xml` from `org.csstudio.sns/build`,
   which in turn enable a composite repository from `org.csstudio.sns/css_repo`
   that is configured as the combination of all the repositories that
   we are about to build locally: diirt, maven-osgi-bundles, etc.

As a result, you should find log files for the various build steps in the original directory:
`0_diirt.log`, `1_maven-osgi-bundles.log`, `2_cs-studio-thirdparty.log`, `3_core.log`, `4_applications.log`, `5_display_builder.log`, `6_sns.log`.

The directory `org.csstudio.sns/repository/target/products` will contain the binary products.

To import into Eclipse IDE:
1) `Import->Maven->Existing Maven Products` and find the code that you are interested in editing e.g. cs-studio\applications\archive
2) `Import->Maven->Existing Maven Products` org.csstudio.sns/repository
3) Create a target platform and add a directory pointing at org.csstudio.sns/repository/target/repository/plugins
4) Run the product you are interested from org.csstudio.sns/repository. You may need to right click on the product `Run As...->Run Configurations->Plug-ins->Add Required Plug-ins`

`org.csstudio.sns/repository/target/repository` is a P2 repository from which the UI product
can install optional features.
