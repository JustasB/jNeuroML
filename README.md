jNeuroML
========

There are a number of repositories in active development under GitHub for handling [NeuroML](https://github.com/NeuroML) 
and [LEMS](https://github.com/LEMS) with Java. To make it easier to access all of this functionality, we've created a single package, jNeuroML, which allows access to most of this functionality through a simple command line interface and requires minimal installation. 

jNeuroML can:

- **Validate** NeuroML v1.8.1 and v2.x files
- **Simulate** most NeuroML 2 models (simulation should be specificed in [Simulation element in LEMS file](https://github.com/NeuroML/NeuroML2/blob/master/LEMSexamples/LEMS_NML2_Ex5_DetCell.xml))
- **Export** NeuroML 2 and LEMS to many formats such as Neuron, Brian, Matlab, etc.
- **Import** other languages into LEMS (e.g. SBML)

Binary installation
-------------------

To get a precompiled binary for jNeuroML:
 1. Go to https://github.com/NeuroML/jNeuroML/releases and download the latest **jNeuroML.zip** file
 2. Unzip it to your local machine
 3. Add environment variable *JNML_HOME*, pointing to the root *jNeuroML* folder
 4. Add the location of the *jNeuroML* folder to the *PATH* variable. This and the previous step will ensure you can run the *jnml* utility from any folder.
 
Usage
-----

Typing *./jnml* (or *jnml.bat* on Windows) will list the options available. Some of the current options include:

    ./jnml -validate MyNeuroML.nml              (validate NeuroML 2 document against the current schema)
    ./jnml -validatev1 MyNeuroML1.xml           (validate NeuroML v1 document against the v1.8.1 schema)
    ./jnml MyLEMS.xml                           (parse & simulate a LEMS model using jLEMS)
    ./jnml MyLEMS.xml -graph                    (generate png of structure of LEMS model using GraphViz)
    ./jnml MyLEMS.xml -neuron                   (generate code to run on the NEURON simulator)

Export and import features for [NEURON](http://www.neuron.yale.edu/neuron/), [SBML](http://sbml.org), 
[Brian](http://www.briansimulator.org/) etc. are under active development (see https://github.com/NeuroML/org.neuroml.export 
and https://github.com/NeuroML/org.neuroml.import).


Getting the source for jNeuroML
-------------------------------

If you prefer to clone all of the individual repositories and build the jNeuroML application yourself, 
use the [getNeuroML.py](https://github.com/NeuroML/jNeuroML/blob/master/getNeuroML.py) utility in the jNeuroML repo.

Eensure you have:
  - git
  - [Java Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/index.html) and JAVA_HOME variable set (see [here for Ubuntu](https://askubuntu.com/a/175547/702527)).
  - Maven: Download [here](http://maven.apache.org/) or use package managers for Linux (e.g. `sudo apt-get install maven`) or Mac (`brew install maven`). 

Then in terminal, run:

    git clone git://github.com/NeuroML/jNeuroML.git neuroml_dev/jNeuroML
    cd neuroml_dev/jNeuroML
    python getNeuroML.py

This will clone ~11 repos for NML2 & LEMS (including Python based libraries) into *neuroml_dev/* and compile 
the Java based ones using Maven. The full process may take 5-10 mins on first installation, but subsequently running:

    git pull
    python getNeuroML.py

in the jNeuroML folder will get the stable version of each repo & compile using Maven if necessary. 

**To access the very latest version** (the [development](https://github.com/NeuroML/jNeuroML/tree/development) branches of the GitHub repos) use:

    python getNeuroML.py clean
    python getNeuroML.py development

Use of Maven is a great way to manage versions of applications being developed in distributed repositories, 
and will make it easy to use selected parts of this for different Java applications. For example, these packages 
will be used in various ways to provide NeuroML/LEMS support in [neuroConstruct](http://www.neuroConstruct.org) and for handling NeuroML on the [Open Source Brain website](http://www.OpenSourceBrain.org).

Prefer Python?
--------------

If you prefer using/installing/coding in Python, try out [pyNeuroML](https://github.com/NeuroML/pyNeuroML). Much of the functionality of jNeuroML is bundled inside pyNeuroML and can be accessed with a command line utility (*pynml*) with similar usage as *jnml*.

[![Build Status](https://travis-ci.org/NeuroML/jNeuroML.png?branch=master)](https://travis-ci.org/NeuroML/jNeuroML)

This code is distributed under the terms of the GNU Lesser General Public License.







