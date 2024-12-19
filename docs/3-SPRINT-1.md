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
  
