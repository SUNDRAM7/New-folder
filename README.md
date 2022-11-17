# New-folder
def createbankaccount():
      global dob
      global ad
      global pn
      global pas
      dob=int(input("Enter Your date of birth(ddmmyyyy) : "))
      ad=int(input("Enter your AADHAR NUMBER : "))
      pn=input("Enter Your PAN NUMBER : ")
      aacount_ifsc()
      pas=input("Enter an alphanumeric password (include special character too) : ")
      print("Now you can use your password,",pas,"and account number to login")
      print("WELCOME TO BANKING SYSTEM  !!!!!!!!!!!  :)  ")
      login_sysyem ()
      
                  
def aacount_ifsc():
      global nam
      global c
      global cif
      global bal
      import random
      nam=input("Enter Your name : ")
      namfl=['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z']
      ram=1
      for i in range(0,25,1):
            if nam[0] == namfl[i]:
                  ram=i
                  break
      if ram<=10:
            c=random.randint(11111111111, 38666666666)# as an average data suggest that 31% names starts with a to k
      elif ram<=18 and ram>10:
            c=random.randint(38666666667,75111111111)# 41% (r has better share)
      else:
            c=random.randint(75111111111,99999999999)# 28% (s has better share)
      state=input("Enter Your State name : ")
      dist=input("Enter Your District name : ")
      #check for same district and state in dtabase for its ifsc code if not available then execute the below code
      stfl=['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z']
      ram=1
      for i in range(0,25,1):
            if nam[0] == stfl[i]:
                  ram=i
                  break

      if ram<=10:
            fc=random.randint(1111,4111)
      elif ram<=18 and ram>10:
            fc=random.randint(4111,7511)
      else:
            fc=random.randint(7511,9999)
      banm="SBIN"#input("Enter the four letter of name of Bank : ")
      cif=banm+"000"+str(fc)
      bal=0
      print("your account number is ", c)
      print("your cif number is ", cif)
      print("Your balance is : ",bal)
      print("please note the account number and cif number for future reference !!!!!!!!")
      

def login_sysyem ():
      
      #dbac=int(input("Enter account number : ")) 
      lsac=int(input("Enter your A/C : "))
      if lsac==c:
            passadhrlogin()
      else:
            ch=input("wrong a/c!!  WOULD YOU LIKE TO TRY AGAIN (y/n) : ")
            if ch=="y" or ch=="Y":
                  login_sysyem()
                  
            else:
                print("OUT OF LOGIN SYSTEM")
def passadhrlogin():
            #dbpas=input("Enter your password : ")
            #dbad=int(input("Enter your addharcard no. : "))
            lsad=int(input("Enter your addharcard no. : "))
            lsps=input("Enter your password : ")
            if lsps==pas and lsad==ad:
                  print("WELCOME TO SBI")
                  login_window()
            else:
                  ch=input("wrong password or addhar number!!  WOULD YOU LIKE TO TRY AGAIN (y/n) : ")
                  if ch=='y' or ch=="Y":
                        passadhrlogin()
                  else:
                        print("OUT OF LOGIN WINDOW")

def account_deletion():
      dac=input("PLEASE ENTRE YOUR ACCOUNT NUMBER ")
      #dcif=input
      #dad=input
      #dcif=input
      print('YOUR ACCOUNT DETAILS ARE 1. NAME ' ,nam,"2. Account Number : ",c,"3. Aadhar number : ",ad)
      #print(ac,cif,nam,dob,pn,ad)
      con=input("Are you sure to delete your account (y/n) : ")
      if con=="y" or con=="Y":
            print('YOURS DETAILS  HAVE BEEN DELETED :(')
      else:
            login_window()

            

def money_transfer():
      global bal
      mtac=int(input("Enter your account number : "))
      mtcif=input("Enter your cif number : ")
      #check the bank balance of owner bank account and its details for the same and if it is good then else ask to enter the account detailsagain or exit
      print( "balance of  account IS : ",bal)
      mtm=float(input("Enter the amount you want to transfer : "))
      if bal>=mtm:
            mtbac=int(input("Enter beneficary account number : "))
            mtcif=input("Enter the cif of b account : ")
            #check for details of benificary
            if mtac==c and mtcif==cif:
                  mtpas=input("Enter your password : ")
                  #check for passwords
                  if mtpas==pas :
                        print("You have transferred" ,mtm, "to account no.",mtbac,mtcif )
                        print("Thankyou for using money transfer")
                        bal=bal-mtm
                        #add the given amount to the benificary account in through insertinto database command and generate a transction no. using random finc and print it
      else:
            print("NoT enough balance")
      login_window()

def deposit_sys():
      global bal
      #for cashier
      #dbac=int(input("Enter account number : ")) FROM DATA BASE
      #dbcif=(input("Enter account cif : ")) FROM DATABASE
      #dbab=int(input("Enter account balance : ")) FROM DATABASE
      dsac=int(input("Enter account number : "))
      dscif=input("Enter the IFSC CODE : ")
      if dsac==c and dscif==cif:
               DA=float(input("ENTER THE AMOUNT TO BE DEPOSITED"))
               ch=input("ARE YoU SURE!!!!!  (Y/N) and to exit press any key : ")
               if ch=="y" or ch=="Y":
                     print ("deposited amount is", DA ," account balance is ", bal+DA ,"and your transaction reference number is","#number generated by randomfunc")
                     bal=bal+DA
               elif ch=="n" or ch=="N":
                     deposit_sys()
               else:
                ech=input("DO YOUWANT TOO EXIT(Y?N) :")
                if ech=="y" or ech=="Y":
                    print( "exited from ds")
                else:
                    deposit_sys()
      else:
        print("Entery doesnt match")
      login_window()            
def withdraw_sys():
      global bal
      #FROM DATABASE          dbac=int(input("Enter account number : "))
      #FROM DATABASE          dbcif=input("Enter account cif : ")
      #FROM DATABASE          blow=float(input("Enter account balance : "))
      #FROM DATABASE          dbpas=input("Enter password : ")
      wsac=int(input("Enter account number : "))
      wscif=input("Enter the IFSC CODE : ")
      if wsac==c and wscif==cif:
            WA=float(input("ENTER THE AMOUNT TO BE withdrawn"))
            if bal>=WA:
                  ch="y"
                  while ch=="y":
                        wspas=input("Enter your password : ")
                        #check for passwords makkhan
                        if wspas == pas :
                              print("You have withdrawn", WA , "and the remaning balance is ",bal-WA)
                              bal=bal-WA
                              print("thankyou for using money withdrawing system")
                              ch="n"
                        else:
                              ch=input("wrong password !!  WOULD YOU LIKE TO TRY AGAIN (y/n) : ")
                              if ch=='y' or ch=="Y":
                                    ch='y'
                              else :
                                    print("Exited from withdrawnsys")
                                    ch="n"#makkahan
            else:
                print("insufficient balnce")
      else:
        ch=input("Wrong details entered!!!!  WOULD YOU LIKE TO TRY AGAIN(Y/N)")
        if ch=='y' or ch=="Y":
            withdraw_sys()
        else:
            print("Exited from withdrawing system")
      login_window()
def login_window():
      print(
                  '''
                  ENTER YOUR CHOICE\n
                  1. FOR CHECKING BALANCE\n
                  2. WITHDRAWL WINDOW\n
                  3. DEPOSIT WINDOW\n
                  4. ACCOUNT DELETION\n
                  5. MONEY TRANFER\n
                  6. TO EXIT\n
                  ''')
      ch=int(input("ENTER YOUR CHOICE, ACCORDING TO REQUIREMENT : "))
      if ch==1:
            bal_check()
      elif ch==2:
            withdraw_sys()
      elif ch==3:
            deposit_sys()
      elif ch==4:
            account_deletion()
      elif ch==5:
            money_transfer()
      elif ch==6:
            print("Thankyou for using banking window  :) ")
      else:
            print('Wrong choice entered')
            login_window()
def bal_check():
      global bal
      bcac=int(input("Enter account number : "))
      bccif=input("Enter the IFSC CODE : ")
      if bcac==c and bccif==cif:
            print("Your balance is",bal)
      else:
            print("Wrong input")
            bal_check()
      login_window()
      
print('Welcome to Banking System')
print('''
      1. TO LOGIN INTO YOUR BANKING ACCOUNT
      2. TO CREATE A NEW BANK ACCOUNT''')
ch=int(input("ENTER YOUR CHOICE, ACCORDING TO REQUIREMENT"))
if ch==1:
      login_sysyem ()
elif ch==2:
      createbankaccount()
else:
      print('wrong choice entered')

