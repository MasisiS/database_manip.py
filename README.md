# Importing library
import sqlite3 
  
# Creating a file
db = sqlite3.connect('database_manip')
  
# Get a cursor object
cursor = db.cursor()
  
# Creating table 
table = '''
               CREATE TABLE python_programming(id n(5), name char(30), grade char(2))
               '''
cursor.execute(table) 
  
# Queries to INSERT records. 
cursor.execute('''INSERT INTO python_programming VALUES (55, 'Carl Davis', 61)''') 
cursor.execute('''INSERT INTO python_programming VALUES (66, 'Dennis Fredrickson', 88)''') 
cursor.execute('''INSERT INTO python_programming VALUES (77, 'Jane Richards', 78)''') 
cursor.execute('''INSERT INTO python_programming VALUES (12, 'Peyton Sawyer', 45)''') 
cursor.execute('''INSERT INTO python_programming VALUES (2, 'Lucas Brooke', 99)''') 
  
# Display data inserted 
print("Students_grades: ") 
data=cursor.execute('''SELECT * FROM python_programming''') 
for row in data: 
    print(row) 
  
# Commit your changes in the database     
db.commit() 
  
# Closing the connection 
print(" ")
# Selecting rows with grade between 60 and 80
cursor.execute('''SELECT * FROM python_programming
               WHERE grade BETWEEN 60 AND 80;
               ''')
student = cursor.fetchall()
print(student)
db.commit() 
print(" ")
# Change Carl Davis’s grade to 65.
cursor.execute('''UPDATE python_programming SET grade = 65
                           WHERE name = 'Carl Davis' ''')
new_table = data=cursor.execute('''SELECT * FROM python_programming''') 
for row in new_table: 
    print(row)
    
db.commit()

print(" ")
cursor.execute('''DELETE FROM python_programming WHERE name = 'Dennis Fredrickson' ''') 

# Deleting Dennis Fredrickson’s row.
deleted_row =cursor.execute('''SELECT * FROM python_programming''') 
for row in deleted_row: 
    print(row) 
db.commit()  
print(" ")
    
# Updating a row to change the grade of all students with an id greater
#than 55 to a grade of 80.
cursor.execute('''UPDATE python_programming SET grade = 80
                   WHERE id >= 55 ''')

updated_tab = cursor.execute('''SELECT * FROM python_programming''') 
for row in updated_tab: 
    print(row)
    
db.commit()
