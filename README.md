# virtual-disk-lib

## Background

A few weeks ago I was working on some VHD and VHDX file format conversions (because Azure Disks can only be created from 'Fix VHD' format disks).
There were/are a few challenges to this, so I thought I'd write a library for it, and show how to work through the problems.

I'll document the process and thinking here (and mirror on my blog).
It'll be written in C# (at least initially, I may add Python, Golang, Rust too as I'd like to get a bit more familiar with those languages)

I'll take an iterative approach. Major steps will be:

- Document requirements / expectations
- Set up environment, CI/CD
- Parsing file/header information
- Reading data
  - Fixed VHD
  - Dynamic VHD
  - Differencing VHD
  - Dynamic VHDX
  - Differencing VHDX
## Requirements

The intention of this library is to provide access to Virtual Disks as though they were a large binary file, so things like reading from a particular location, as a stream, or into a buffer, and possiblly the write side of things too.
We will also need to parse and understand the footers and headers, and it would be useful to provide that data to a client (to check it is valid, maybe print it out etc)

The initial use case is to read bytes so they can be uploaded to Azure page blob (to create an Azure Disk), but we'll approach it in an iterative manner.

The specification for the VHD file format can be found [here](https://go.microsoft.com/fwlink/p/?linkid=137171).

The following documents will outline the goal of each sprint/iteration.
### Sprint 1:

The purpose of this sprint is to get the basic structure and operation set up, the .NET library project, the client sample project, and the unit tests.
By the end of this sprint we should be able to read and parse the 'footer' section of the VHD file

Sprint Tasks:

- Set up the .NET library project.
- Set up the .NET client/sample app project.
- Set up the unit tests project.
- Create a solution file with the above 3 projects added.
- Given a path and filename, read the last 512 bytes.
- Parse these 512 bytes as the 'footer' of a VHD format file (throw exception if values/checksum are incorrect)
- Update the client application/tool so that it calls the library with a provided filename, and displays the footer data (in the console)
  
