# mdt-surrogates
DHARMA Surrogates metadata

CSV folder = stored the csv files for surrogates of the projects downloaded from googleSheets. 
output = temporary files for each surrogate, to check if necessary. Splitted by xslt stored in project-documentatation/Stylesheets/mdt_inscriptions/mdtSurrrogate_splitting.xsl
temporary=  1 xml file containing all surrogates description used to render the html display. Made with xslt stored in project-documentatation/Stylesheets/mdt_inscriptions/mdtSurrogate_start.xsl

build_to_xml.xml = launch the transformation for splitting the output file into several files sotred into temporary.
clone-projectDoc.xml = clone project-documentation for github action

.github/workflows
1- run csvtoxml.yml on push on java line launching project-documentation/stylesheets/mdt_inscriptions/mdtSurrogate_start.xsl, source folder github api and destination: temporary folder. 
2- run commacleaning.yml on finishingcsvtoxml.yml .yml task, one java line launching project-documentation/stylesheets/mdt_inscriptions/mdt_CommaCleaning.xsl, source temporary folder, destination temporary folder. 
3- run xmltodisplay.yml on finishing commacleaning.yml task,  launch the two ant tasks clone-projectDoc.xml then build_to_display.xm, source folder temporary, destination folder output
