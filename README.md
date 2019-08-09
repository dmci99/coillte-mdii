# coillte-mdii
MapMint services used to import data coming from a specific tool used to record tree informations.

How-to use
===========

The main service is the mailCheck service, it is responsible to:
1. fetch all received emails that have a zip file attached (by invoking the getLastEmails service) and publish the corresponding zip file and inform that the zip file from the user has been properly imported (by invoking publishZipFiles service)
3. refresh the datastore used as MapMint database (by invoking datastores.directories.cleanup then datastores.mmVectorInfo2MapJs service)
4. then, update the extent of every layers that depends on this datastore (by invoking the mapfile.updateAllExtentForMainDB service)

To invoke the mailCheck service simply use the following URL by replacing <YOUR_HOST> with the hostname used to access your MapMint instance:

https://<YOUR_HOST>/cgi-bin/mm/zoo_loader.cgi?request=Execute&service=WPS&version=1.0.0&Identifier=cmd2.mailCheck&DataInputs=a=toto
