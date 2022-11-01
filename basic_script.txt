#!/bin/bash
whoami
date
pwd

#Enter flutter project name
PROJECT="Please enter the project name."
echo $PROJECT

#read project name input
read PROJECT_NAME


#Creating flutter project



#Define function to create flutter project
checkProjectNameValidToCreateProject ()
{
#check is space in project name
if [[ "$PROJECT_NAME" =~ \ |\' ]] 
then
   echo "Space not allowed in the project name"
   exit;
#check is capital letter in project name
else
   if [[ "$PROJECT_NAME" =~ [A-Z] ]]
   then
   	echo "Use only lowercase letters to create a flutter project."
	exit;
   else
   	echo "Creating flutter project........"
	#Creating flutter project Project create command
   	flutter create $PROJECT_NAME
	echo "Project created successfully!"
   fi
fi

}


#Creating flutter project
checkProjectNameValidToCreateProject


#Changing into created project directory
echo "Changing to created project directory...."
cd "$PROJECT_NAME"

# add provider package
echo "Adding provider package...." 
flutter pub add provider

#activate package "io_flutter_cli" for application
echo "activating "io_flutter_cli" for for application......" 
dart pub global activate --source git https://github.com/1avinashMairal/io_flutter_structure.git

#export path globaly
Echo "Exporting package path globaly......"
export PATH="$PATH":"$HOME/.pub-cache/bin"

#create structure for application
echo "Creating project structure for application......" 
io_flutter_cli create

echo "ALL IS DONE. YOU CAN START YOUR DEVELOPMENT. THANK YOU........"


