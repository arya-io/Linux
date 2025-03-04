#!/bin/bash

while true
do

        echo "Welcome to Menu"
        echo "------------------------"
        echo "1. Make a file"
        echo "2. Display contents"
        echo "3. Copy the file"
        echo "4. Rename the file"
        echo "5. Delete the file"
        echo "6. Exit"

        read -p "Enter your option: " option

	case $option in
		"1")

        		read -p "Enter file name: " file_name
        		if [[ -e "$file_name" ]];then
                		echo "Error: File already exists!"
        		else
                		echo "Enter some content. Please press Ctrl + D in order to save the file. "
                		cat > "${file_name}"
                		echo "${file_name} created successfully..!!"
        		fi
			;;
		"2")
			 
        		read -p "Enter file name: " file_name2
			if [[ -e "$file_name2" ]];then
                		echo "File exists!"
				cat "${file_name2}"
			else
				echo "Error: File does not exist."
			fi
			;;
		"3")
			read -p "Enter source file name: " srcfile
			if [[ -e "$srcfile" ]] && [[ -r "$srcfile" ]];then
				read -p "Enter target file name: " trgfile
			
				else
			echo "Error: Source file does not exist."
			fi
			
		if [[ ! -e "$trfgile" ]];then
		cp "$srcfile" "$trgfile"
		echo "Source file is copied to target file."
		else
		echo "Target file exist."
		fi
		;;

	"4")

			
			read -p "Enter source file name: " srcfile
			if [[ -e "$srcfile" ]] && [[ -r "$srcfile" ]];then
				read -p "Enter target file name: " trgfile
			
				else
			echo "Error: Source file does not exist."
			fi
			
		if [[ ! -e "$trfgile" ]];then
		mv "$srcfile" "$trgfile"
		echo "Source file is renamed with the name of target file."
		else
		echo "Target file exist."
		fi
		;;
	"5")
		read -p "Enter a file name: " file5
		if [[ -e "$file5" ]];then
			echo "File exists."
			if [[ -w "$file5" ]];then
				read -p "Do you want to delete the file? If so, press 9: " delt
				if [[ $delt == "9" ]];then
					rm "$file5"
					echo "File deleted successfully..!!"
				fi
			fi
		else
			echo "Error: File does not exist."
		fi
		;;
	"6")
		exit
		;;

	esac
done
