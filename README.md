# About

SlicerRadiomics is an extension for [3D Slicer](http://slicer.org) that
encapsulates [pyradiomics](https://github.com/radiomics/pyradiomics) library,
which in turn implements calculation of a variety of
[radiomics](http://radiomics.github.io) features.

# Install instructions

SlicerRadiomics is currently distributed as an extension via the 3D Slicer ExtensionManager.
Follow these steps to install the extension:
1. Download the latest **nightly** release for your platform from http://download.slicer.org.
**Do NOT use installers tagged as "Stable Release"!**
If you use Mac, make sure you move the Slicer application to the Applications folder on your computer before launching it!
2. Once installed, open Extension Manager by clicking the icon as shown below.
![](https://qiicr.gitbooks.io/quantitativereporting-guide/content/docs/screenshots/extension_manager.png)
3. Search for `Radiomics` and install the extension by clicking the INSTALL
   button.
4. Once installation of `Radiomics` and dependencies is completed,
   you will need to restart Slicer application to access the module.
   If installation was successful, you should be able to see
   `Radiomics` module in the Slicer module list.
   
# Known issues

At the moment, the extension is not available on Linux, due to a known issue (https://github.com/Radiomics/SlicerRadiomics/issues/16).

The extension will also not work on Windows, due to a known issue (https://github.com/Radiomics/SlicerRadiomics/issues/23). However, you can use the following workaround to fix the problem manually, while we are working on a proper resolution.

You will need to change the following file (replacing `USER_NAME` with your user name on your system):

`C:/Users/USER_NAME/AppData/Roaming/NA-MIC/Extensions-revision/SlicerRadiomics/lib/site-packages/radiomics/featureextractor.py`

Where revision is something like 26083 depending on the nightly version of Slicer.

Line 9 should be changed from:

`import pykwalify.core`

to:

`# import pykwalify.core`

# Building `SlicerRadiomics` from source

In order to build this extension, you need to have a version of Slicer built from source.
You can build Slicer following [the
instructions](https://www.slicer.org/wiki/Documentation/Nightly/Developers/Build_Instructions).
Once you have done that, all you need to do are the following steps:

* Clone the source code of the repository.
```
$ git clone https://github.com/radiomics/SlicerRadiomics.git
```

* Create an empty directory for building the extension
```
$ mkdir SlicerRadiomics-build
```

* Configure the build using cmake (you will have it installed as one of the
   prerequisites for building 3D Slicer)
```
$ cd SlicerRadiomics-build; ccmake ../SlicerRadiomics
```

* Build the extension
```
$ make
```

* Package the extension
```
$ cd inner-build
$ make package
```

Once completed, you can install the [extension from file](https://www.slicer.org/wiki/Documentation/Nightly/SlicerApplication/ExtensionsManager#Installing_an_extension_without_network_connection).

# Support

If you found a bug, or to report a reproducible problem, [submit an
issue](https://github.com/Radiomics/SlicerRadiomics/issues/new).

If you have a question about using the extension, please ask on the [mailing
list](https://groups.google.com/forum/#!forum/pyradiomics).

# Acknowledgments

This project is supported in part by the National Institutes of Health, National
Cancer Institute [Informatics Technology for Cancer Research (ITCR)
program](https://itcr.nci.nih.gov) via
grant U24 CA194354 (PI Hugo Aerts).
