
##Pylthon Flask API Template-- Salaries for employees in City of Chicago. Please observe any Copyright changes.

#### Modified from Naren Arya's Flask tutorial:  https://impythonist.wordpress.com/2015/07/12/build-an-api-under-30-lines-of-code-with-python-and-flask/


#### 1. Create Project folder named 'Salaries' in home directory
#### 2. Download repo, unzip
#### 3. Extract 'app.py' 'employee_chicago.csv' and 'Instructions.txt' into the new folder "Salaries"
#### 4. Open Linux Terminal and set pwd using "$  cd ~/Salaries " -- sets as present working directory
#### 5. Run the code below ("$" for Linux Terminal User and ">" for sqlite3:


	#$ 
	mkdir rest-app
	cp app.py rest-app
	cp employee_chicago.csv rest-app
	cd rest-app   #Sets to 'app root directory'
	sqlite3 salaries.db

	#  #If 'salaries.db' is trusted and loaded into app root directory already
	#  #ATTACH DATABASE 'salaries.db' As 'salaries'; # as alt
	#  #DETACH DATABASE 'salaries.db' 
	
		#  #Create table named "salaries"
               ####  # Note 'primary key' deletes duplicates on import		
		# sqlite> 
		   create table salaries (
			 NAME text,
			 POSITION text,
			 DEPARTMENT text,
			 SALARY double
		);

		
	 # Load csv data into salaries table
	 # sqlite> 

		  .mode csv

		  .import employee_chicago.csv salaries
		
		# Should print out names 'last, first middle initial'
		# sqlite> 
		   
		  SELECT name FROM salaries;

		  ATTACH DATABASE 'salaries.db' As 'salaries'; 


	   # Next: 'Ctrl-D' quit out of sqlite3 from terminal
	

	# Make virtual environment with name "rest-api"
	# $ 
	  virtualenv rest-api
	  source rest-api/bin/activate     # Source into virtual environment for pip inst.


	# Note:  sudo aptitude install build-essential   # for C / C++ compiler 
	# For error free install (we use sudo after build-essential:)
	# (rest-api)$ 
		sudo pip install flask  
		sudo pip install flask-restful
	        sudo pip install sqlalchemy

	#(rest-api) ~/Salaries/rest-app$  
		sudo python app.py


#### 6. Navigate to browser:
        
	#http://localhost:5000/departments
	#http://localhost:5000/dept/police
	#http://localhost:5000/dept/family%20&%20support  # "%20&%20" denotes " & "


  # Note: To get out of virtualenv
	# (rest-api)
	deactivate 



#### Alternative: To Run App from Binary
#### 1. Unzip the repo into "Salaries" folder
#### 2. cd into "Salaries/rest-app"
#### 3. Run "source rest-api/bin/activate"
#### 4. Run "sudo python app.py" to launch from virtaulenv
#### 5. Open browser tab to "http://localhost:5000/departments"
