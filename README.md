# Description
Implemented database connection from Python GUI to MySQL.  Therapy Game and asking questions to patients. Save patient and therapist's personal informations to database.  Save patient's answers and therapist's questions to database.  Load questions and therapist's questions to Python GUI. 

## Registration Window
-----------------------------------------
<img width="202" alt="loginpage" src="https://user-images.githubusercontent.com/37283117/147423137-c44d86b5-8988-4f8f-8b5b-998e974797dd.png">
- Valid? button checks whether there is a duplicate ID in MySQL database table. 
```
def CheckDuplicateID(self):
        # checks if there are duplicate ID in mysql db and length <= 15
        # if there is no duplicate, make self.idCheck = True
        # else False
        print(self.conn)
        if self.idInput.text() == "" or len(self.idInput.text()) < 3:
            self.explanation.setText("Registration form: " + "ID should be longer than 2 letters")
            self.duplicateID.setText("Not Valid!")
            self.duplicateID.setStyleSheet("background-color: red; color: white;")
            return
        self.explanation.setText("Registration form: ")

        try:
            cur = self.conn.cursor()
            sql_dup_check = "select duplicate_check(%s)"
            cur.execute(sql_dup_check, self.idInput.text())
            num = cur.fetchone()[0]
            
            if num == 0:
                #if == 0, 
                # it means there is no duplicate id
                self.idCheck = True
                self.duplicateID.setText("Valid ID!")
                self.duplicateID.setStyleSheet("background-color: lightblue; color: white;")
                print("there is no id:", self.idInput.text())
            else:
                self.idCheck = False
                self.duplicateID.setText("Not Valid!")
                self.duplicateID.setStyleSheet("background-color: red; color: white;")
        except:
            print("Error in check duplicate id ")
```
# Youtube Link
https://www.youtube.com/watch?v=ffAy89lf0MY
