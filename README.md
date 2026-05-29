#python-file-management-system

from pathlib import Path
import os

def readfileandfolder():
    path = Path('') 
    items = list(path.rglob('*')) 
    for i, items in enumerate(items):
        print(f"{i+1} : {items}")


def createfile():
    try:     
        readfileandfolder()
        name = input("Please tell your file name:- ")
        p =Path(name)
        if not p.exists():
            with open(p,'w') as fs:
                data = input("What you want write")
                fs.write(data)
            
            print("FILE CREATED SUCCESSFULLY")
        else:
            print("this file already exist")
    
    except Exception as err:
        print(f"An error occured as {err}")

def readfile():
    try: 
        
        readfileandfolder()
        name = input("Which file you want to read:- ")
        p = Path(name)
        
        if p.exists() and p.is_file():

            with open(p,'r') as fs:
                data = fs.read()
                print(data)

            print("Readed successfully")
        else:
            print("this file doesnot exist")
    
    except Exception as err:
        print("An Error occur as",err)

def updatefile():
    try:
        readfileandfolder()
        name = input("tell which file you want to update :- ")
        p = Path(name)
        if p.exists() and p.is_file():
            print("press 1 for changing the name:- ")
            print("press 2 for overwrting the data of your file:- ")
            print("press 3 for appending some content in your file:- ")

            res = int(input("tell your response :- "))
            if res == 1:
                name2 = input("tell your new file name :- ")
                p2 = Path(name2)
                p.rename(p2)

            if res == 2:
                with open(p,'w') as fs:
                    data = input("Tell what you want to write this is overwrite the file :-")
                    fs.write(data)
            
            if res == 3:
                with open(p,'w') as fs:
                    data = input("Tell what you want to append :- ")
                    fs.write(""+data)
            
            print("FILE UPDATE SUCCESSFULLY")

    except Exception as err:
        print(f"An Error occur {err}")

def deletefile():
    try:
        readfileandfolder()
        name = input("which file you want to Delete :- ")
        p =  Path(name)
        if p.exists() and p.is_file():
            os.remove(name)
            print("file remove successfully")
        else:
            print("No such File Exist")
    except Exception as err:
        print(f"An Error ocurrs {err} ")




print("press 1 for creating a file")
print("press 2 for Read a file")
print("press 3 for Updatig a file")
print("press 4 for Deletion a file")

check = int(input("Please tell your Response:- "))
if check == 1:
    createfile()

if check == 2:
    readfile()

if check == 3:
    updatefile()

if check == 4:
    deletefile()
