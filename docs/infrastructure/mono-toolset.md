Building a new Mono toolset
====
This document describes building a new Mono toolset for use in our Mac or Linux Jenkins jobs.  

### Building
The new *toolset name* will be chosen as one of the following:

- Linux: mono.linux.`<version number>`
- Mac: mono.mac.`<version number>`

The value of *version number* will simply be the one number higher than the current version number of the toolset.  

To build the toolset execute the following:

- Set `$PREFIX` to `/tmp/<toolset name>`
- Follow the remainder of the [Compiling Mono](http://www.mono-project.com/docs/compiling-mono/) instructions.  
- Install the PCL references: `<roslyn dir>/build/linux/setup-pcl.sh /tmp/<toolset name>`
- Bzip the resulting directory.  `tar -jcvf <toolset name>.tar.bz2 /tmp/<toolset name>`
- Upload the file to the Azure in the dotnetci storage account in the roslyn container.  
- Send a PR to change [cibuild.sh](https://github.com/dotnet/roslyn/blob/master/cibuild.sh) to use the new toolset.  

Note: This process needs to be repeated for both Mac and Linux.  

### Existing toolsets
This table describes the existing Mono toolsets and the commit they were built from.  

| Version | Linux | Mac |
| --- | --- | --- |
| 1 | [43af8d475d853c8408ddaddbed4cfd61d2919780](https://github.com/jaredpar/mono/commit/43af8d475d853c8408ddaddbed4cfd61d2919780) | [43af8d475d853c8408ddaddbed4cfd61d2919780](https://github.com/jaredpar/mono/commit/43af8d475d853c8408ddaddbed4cfd61d2919780) |
