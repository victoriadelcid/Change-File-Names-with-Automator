# Change-File-Names-with-Automator
When downloading files on certain macs, the computer will automatically add another file extension on top of what you already downloaded. For example when downloading a ".gff" file, the mac will add ".txt" at the end, making it ".gff.txt". When handling multiple files it becomes tedious to change, automator does it for you.

Instructions on how to use:
1. All macs should have Automator already installed, it should be located in the launchpad.
2. When opening Automator, there is a search bar in the top left-hand corner. Type "Rename Finder Items" and select.
3. On the right-hand side a workflow should appear. NOTE: a warning should pop up prompting you the choice of saving a copy of the original file, select don't add. 
4. At the top of the workflow there should be an option to select the location at which Automator will receive and change these files. Select the location of preference. I recommend selecting the location in which files automatically download in your computer. If files automatically go to multiple locations, you would have to repeat steps 5-12 for each location you would like Automator to change your files in.
5. On the first action of the workflow, replace the "Add Date or Time" drop-down to "Replace Text".
6. In the "Find:" textbox, type what your file is originally. For example if I downloaded a .gff file, but it downloaded as ".gff.txt", I would type ".gff.txt".
7. Right next to the find box is a drop down, enusre that it is selected to "full name", and also make sure that "ignore case" is checked.
8. In the replace section, you will type the intended file name, which in my case is ".gff". If you wanted to completely change a file extension to another automatically you could change it to whatever you would like in this box.
9. To add another workflow to change a name of another file extension, you would just double-click on "Rename Finder Items" again and repeat the process of setting the action up again.
11. Some macs will not allow this newly renamed file to open for risk of malware, to bypass this issue: In the search bar of Automator search "Run Shell Script", double-click to add. In the "shell:" drop-down select "/bin/bash" , and for the "Pass input" select "as arguments". In the text box below input the following script (NOTE: This was made from Chat GPT):
    
for f in "$@"
do
    xattr -d com.apple.quarantine "$f" 2>/dev/null
done

12. Once the workflow is complete, navigate to the apple menu, click "File" and select "Save" (or just use (command-s)), it will prompt you to name the file, name accordingly so you don't forget the workflow you have.
Finally, click the "Run" button on the top right hand corner. You can test this workflow by downloading the file provided in this repository. NOTE: will only work if a workflow was made for a ".gff.txt" file. 

Automator works even when you quit the application, note that it may take up to 5 seconds for the File to change its name. If you quit automator and would like to access your previous workflow you can, open automator, navigate to your apple menu, select "File" and select the "Open Recent" menu, and your workflow should be there. It is also accessible in your Automator folder or any location you put it when you saved the workflow on Finder.

Thank you!

