# Linux Basics

## Directory Operation: 
```
    pwd --> displays present working directory
	mkdir mydir  --> create a directory 
	cd mydir --> change directory
	ls --> lists contents of current directory
	ls -l --> list contents of current directory with detailed output
	ll --> list contents of current directory with detailed output
	cd <folder> 
	cd .. --> to come out of a directory 
    rm -r testdir --> to remove a directory
	`~` --> Home directory
	mkdir -p folder/subfolder/subfolder2 --> create parent and child directory
```
## File operations: 

	touch test.txt --> creates a empty file 
    ls -l --> lists the contents in current directory
	echo "Print Output"
	echo "This is a text" > test.txt
	cat test.txt --> writes the content of file into terminal & exits 
	more test.txt --> writes the content of file on terminal page by page ( to move to next page need to hit space bar on keyboard )
	less test.txt --> open the file on terminal & can be read line by line (use arrows to scroll up & down) 		  
					  To comeout need to press 'q' on the key board	
	vi test.txt --> Visual Editor 
					This opens the file in read only mode
					To edit the file, press 'i' on keyboard for INSERT mode & then you can write anything
					once the text is entered, press 'ESC' on keyboard to return back on readonly mode
					press ':wq' on keyboard -- to save & come out of the file
					press ':q' on keyboard -- to come out of the file without saving
					press ':wq!' on keyboard -- to save forcefully & come out of the file
					press ':q!' on keyboard -- to come out of the file forcefully without saving
	rm test.txt --> To remove a file 			

## copy/rename/move operations: 

	While performing these operations, we can always use absolute paths or relative paths accrodingly. 
	These commands expects source & dest values 
	
	cp A.txt B.txt  -- makes a copy of A.txt names it to B.txt in current directory
	cp /home/A.txt /tmp/A.txt -- make a copy of A.txt to /tmp 
	cp -r testdir/ newdir/ -- makes a copy of testdir & names it to newdir in current dirctory 
	cp -r /home/testdir /tmp/testdir -- makes a copy of testdir to /tmp
	
	mv A.txt new.txt --- renames A.txt to new.txt in current path
	mv A.txt /tmp --- moves to A.txt to /tmp
	mv testdir newdir -- renames testdir to newdir in crrent path 
	mv newdir /tmp --- moves newdir to /tmp path


## File/Directory permissions:
	Observe the output of ls:
	drwxrwxr-x 2 gursimran2407 gursimran2407 4096 Nov  7 23:38 testdir
	-rw-rw-r-- 1 gursimran2407 gursimran2407 126 Nov  7 23:37 abc.txt
	-rw-rw-r-- 1 gursimran2407 gursimran2407 126 Nov  7 23:38 one.txt

	drwxrwxr-x or -rw-rw-r--   --> Read/Write/Execute Permission for a file or a directory in linux
	(1st value)gursimran2407 - owner of the file/directory
	(2nd value)gursimran2407 - group who owns file/directory 
	how to update the owner & group for a file/dir 

	chown ( change owner ) is the command to update the owners of dir/file 
	note: note that you need to have previliges to update the permissions for a file/directory
		
	Syntax: chown owner:group filename/dirname
	chown murthy:development filename/dirname --> updates the owner & group of the file/directory to murthy & development
	
##	how to update the read,write & execute permissions for a file/dir
	
		How to decode the Read/Write/Execute Permission terminology: 
		-/d    ---> denotes if it is a file or directory ( - means file / d means directory ) 
		rwx    ---> means read,write & execute permissions for super user ( root )
		rw-    ---> means read,write permissions for the owner of the file ( ex: gursimran2407 as above )  
		r--    ---> means read only permissions for others ( whoever login to the machine ) 
   
   
		r  -- Permission to read the file.
		w  -- Permission to write (or delete) the file.
		x  -- Permission to execute the file, or, in the case of a directory, search it.
	
		chmod ( change mode ) is the command to update the read/write/execute permissions for a file/directory
		r = 4, w = 2, x = 1
		
		- | rwx  | rwx  | rwx
		- | 421  | 421  | 421
		
		to update the permissions we can sum 421 
		if super user needs to have read,write & exeute give 7 
		if the owner need to read & write give 6 
		if other need to have only read give 4  
			   

		chmod 777 file/dir -- rwx for root, rwx for owner, rwx for others 
		chmod 764 file/dir -- rwx for root, rw for owner, r for others 
		chmod 755 fire/dir -- rwx for root, rw for owner, rw for others
		chmod 400 firl/dir -- r for root, for owner/other no permissions # common reason u would see while ec2 ssh keys
