# Bank Project Explaination

## Libaries
```py
import os
import time
from colorama import Fore,Back,Style
```
Here is os library for run commands in terminal, time packet to waiting the code and last one is colorama packet for make output colorfull.

## Information (username,password) Classes
```py
class creditcard:
    username = "username" # username
    password = "password" # password 
    code     = "xxx-xxx-xxx " # xxx-xxx-xxx 

class admin:
    username = "error"
    password = "12345"
    
```
Here is users username password and credit card code. Its like data base. There is also admin's username and password. 

## Users Money Information

```py
class info_error:
    money = 1500
    debt  = 250 
```
This means error user have 1500 $ and also have 250 $ debt.


## Menu Function
```py
def menu(login):
    if login == True:
        print(Fore.GREEN+f"""
        ----------{creditcard.username}----------
        [+] Options : 
        [M] My Information
        [1] Withdraw Money
        [2] Add Money
        [3] Change Username
        [4] Change Password
        [5] Pay All Debt
        [Q] Log Out
        """)
```
Menu function for print menu easly.


## Users Money INFO Printer Function
```py
def info(login,info):
    if login == True:
        print(Fore.BLUE+f"""
        [{creditcard.username}] You Have : 
        [{creditcard.username}] Money : {info.money} $
        [{creditcard.username}] Debt : {info.debt}   $
        """)
        menu(True)
```

## And The Main  Function
```py


def main(logincnt):
    os.system("clear") # if you use windows put "cls" instead of "clear"
    print(Fore.BLACK+f"""
    Error Bank (Safest Bank)
    """)
    if logincnt == False:
        lusername = input(Fore.BLUE+"[+] Please enter your username : ")
        lpassword = input(Fore.BLUE+"[+] Please enter your password : ")
    else:
        lusername = creditcard.username
        lpassword = creditcard.password
        lcode = creditcard.code
    print(Fore.GREEN+f"[+] Controlling username and password..")
    time.sleep(2)
    if lusername == creditcard.username and lpassword == creditcard.password:
        info(True,info_error)
        c = input(Fore.BLUE+f"[{creditcard.username}] Please Choice : ")

        if c == "1":
            ch = int(input(Fore.BLUE+f"[{creditcard.username}] How much money you want to withdraw : "))
            info_error.money = info_error.money - ch 
            print(Fore.GREEN+f"[INFO] You withdrawed : {ch} $ .")
            print(Fore.GREEN+f"[INFO] Your current money is : {info_error.money} $")
            time.sleep(5)
            logincnt = True
            main(True)
        if c == "2":
            ch = int(input(Fore.BLUE+f"[{creditcard.username}] How much money you want to add : "))
            info_error.money = info_error.money + ch 
            print(Fore.BLUE+f"[INFO] Loading...")
            time.sleep(2)
            print(Fore.GREEN+f"[INFO] You added : {ch} $ .")
            print(Fore.GREEN+f"[INFO] Your current money is : {info_error.money} $")
            time.sleep(5)
            logincnt = True
            main(True)
        if c == "3":
            ch = input(Fore.BLUE+f"[{creditcard.username}] Please enter your new username : ")
            creditcard.username = ch 
            print(Fore.BLUE+f"[INFO] Loading...")
            time.sleep(2)
            print(Fore.GREEN+f"[INFO] Your new username : {creditcard.username}")
            time.sleep(5)
            logincnt = True
            main(True)
        if c == "4":
            ch = input(Fore.BLUE+f"[{creditcard.username}] Please enter your new password : ")
            creditcard.password = ch 
            print(Fore.BLUE+f"[INFO] Loading...")
            time.sleep(2)
            print(Fore.GREEN+f"[INFO] Your new password : {creditcard.password}")
            time.sleep(5)
            logincnt = True
            main(True)
        if c == "5":
            print(Fore.BLUE+f"[INFO] Loading...")
            info_error.debt = 0
            info_error.money = info_error.money-info_error.debt
            time.sleep(2)
            print(Fore.GREEN+f"[INFO] Your Money    : {info_error.money}")
            print(Fore.GREEN+f"[INFO] Your Debt     : {info_error.debt}")
            time.sleep(5)
            logincnt = True
            main(True)
        if c == "M" or c == "m":
            print(Fore.BLUE+f"[INFO] Loading...")
            time.sleep(2)
            print(Fore.GREEN+f"[INFO] Your Username : {creditcard.username}")
            print(Fore.GREEN+f"[INFO] Your Password : {creditcard.password}")
            print(Fore.GREEN+f"[INFO] Your C.Code   : {creditcard.code}")
            print(Fore.GREEN+f"[INFO] Your Money    : {info_error.money}")
            print(Fore.GREEN+f"[INFO] Your Debt     : {info_error.debt}")
            time.sleep(12)
            logincnt = True
            main(True)
        if c == "Q" or c == "q":
            print(Fore.BLUE+f"[INFO] Exitting...")
            time.sleep(1)
            logincnt = False
            main(False)
    elif lusername == admin.username and lpassword == admin.password:
        print(Fore.BLACK+f"[+] Hello Admin {admin.username} You Are Welcome...")
        print(Fore.BLACK+f"[+] Print users information...")
        time.sleep(1)
        print(Fore.BLUE+f"[INFO] ---------------{creditcard.username}--------------- : ")
        print(Fore.BLUE+f"[{creditcard.username}] Username : {creditcard.username}")
        print(Fore.BLUE+f"[{creditcard.username}] Password : {creditcard.password}")
        print(Fore.BLUE+f"[{creditcard.username}] C.Code   : {creditcard.code}")
        print(Fore.BLUE+f"[{creditcard.username}] Money    : {info_error.money}")
        print(Fore.BLUE+f"[{creditcard.username}] Debt     : {info_error.debt}")
        print(" ")

    else:
        print(Fore.RED+f"[-] error 404! Your login username and password is not correct. Please try again...")
        time.sleep(5)
        main(False)
```
This is main function that which one is important one. And main function written by simple if else statrments.

## And Command For Run Main
```py
main(False)
```
In main function  there is login count. If you entered username and password correctly for one time , you dont need to enter them again. 
It will automaticly login to system. You can write Q or q for log out. And login count will be false.
