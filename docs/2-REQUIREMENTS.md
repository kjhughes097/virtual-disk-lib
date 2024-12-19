## Requirements

The intention of this library is to provide access to Virtual Disks as though they were a large binary file, so things like reading from a particular location, as a stream, or into a buffer, and possiblly the write side of things too.
We will also need to parse and understand the footers and headers, and it would be useful to provide that data to a client (to check it is valid, maybe print it out etc)

The initial use case is to read bytes so they can be uploaded to Azure page blob (to create an Azure Disk), but we'll approach it in an iterative manner.

The specification for the VHD file format can be found [here](https://go.microsoft.com/fwlink/p/?linkid=137171).

The following documents will outline the goal of each sprint/iteration.
