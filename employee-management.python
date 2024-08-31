import mysql.connector as msc
conn=msc.connect(user=’root’,host=’localhost’,passwd=’nimish2006’,database=’office’)
cur=conn.cursor()
cur.execute("create table EMPLOYEES(empid int,name varchar(20),position varchar(20),gender char(1),age int,city varchar(20),salary int);")
 
def AdminMenu():
    print("1: Add an employee")
    print("2: Delete all employees' records")
    print("3: Delete employees in same column")
    print("4: Change employee's details")
    print("5: Display details of a particular employee")
    print("6: Dispaly details of all the employees in sorted or unsorted manner")
    print("7: Search for a particular employee on basis of empid")
    print("8: Search employees on the basis of some other column ")
    print("9: Run Query of your choice on employee table")
    print("10: Exit")


def UserMenu():
    print("1: Display details of a particular employee")
    print("2: Dispaly details of all the employees in sorted or unsorted manner")
    print("3: Search for a particular employee on empid basis") 
    print("4: Search employees on the basis of some other column ") 
    print("5: Run Query of your choice on employee table") 
    print("6: Exit")

def Addemployee():
    r=int(input("enter employee id:"))
    nm=input("enter name:")
    f=input("enter position:")
    g=input("enter gender(F or M):")
    a=int(input("enter age:"))
    c=input("enter city:")
    s=int(input("enter salary:"))
    cur.execute("insert into EMPLOYEES values(%s,'%s','%s','%s',%s,'%s',%s)" %(r,nm,f,g,a,c,s))
    conn.commit()
    print("employee added successfully")
 


def Updateemployee():
    r=int(input("enter empid of the employee to be modified:"))
    nm=input("enter column name whose value you want to change:")
    v=input("enter the new value")
    if nm in ['empid','age','salary']:
        s="update EMPLOYEES set %s = %s where empid = %s" %(nm,eval(v),r)
    else:
        s="update EMPLOYEES set %s = '%s' where empid = %s" %(nm,v,r)
    cur.execute(s)
    conn.commit()
    print("updation successful")





def Verifyempid(x):
    cur.execute("select * from EMPLOYEES where empid= %s" %(x,))
    d=cur.fetchone()
    if d==None:
        return "wrong"
    else:
        return "right"
 


def RemoveAllemployees():
    cur.execute("delete from EMPLOYEES")
    conn.commit()
    print("All employees removed successfully")
 


def RemoveemployeeColumn():
    nm=input("enter a column name on the basis of which you want to delete the employee(s):")
    v=input("enter its value:")
    if nm in ['empid','age','salary']:
        cur.execute("delete from EMPLOYEES where %s = %s" %(nm,eval(v)))
    else:
        cur.execute("delete from EMPLOYEES where %s = '%s'" %(nm,v))
        conn.commit()
    print("employees removed successfully")




def DisplayAllemployees():
    print("In which order you want to display the employees details:")
    x=int(input("1: ascending order \n2: descending order \n3: As present in table\n"))
    if x==1:
        col=input("enter column name with respect to which you want to order the records")
        cur.execute("select * from EMPLOYEES order by %s asc" %(col,))
    elif x==2:
        col=input("enter column name with respect to which you want to order the records")
        cur.execute("select * from EMPLOYEES order by %s desc" %(col,))
    else:
        cur.execute("select * from EMPLOYEES")
    for x in cur:
        for j in x:
            print(j,end='\t')
        print()
 


def Searchemployee():
    t=int(input("enter empid of the employee to be searched:"))
    cur.execute("select * from EMPLOYEES where empid = %s" %(t,))
    d=cur.fetchone()
    if d==None:
        print("no such employee present")
    else:
        for i in d:
            print(i,end="\t")
        print()
 

def SearchemployeeColumn():
    nm=input("enter a column name on the basis of which you want to search the employee:")
    v=input("enter its value:")
    if nm in ['empid','age','salary']:
        cur.execute("select * from EMPLOYEES where %s = %s" %(nm,eval(v)))
    else:
        d=cur.fetchall()
        if d==[]:
            print("no such employees present")
        else:
            for i in d:
                for x in i:
                    print(x,end="\t")
                print()
 



def AdminChoiceQuery_employee():
    print("which type of query you want to execute ?")
    ch=int(input("Press 1 : For Select query\nPress 2 : For Non-Select query\n"))
    if ch==1:
        s=input("enter your Select command Query\n")
        cur.execute(s)
        d=cur.fetchall()
        if d==[]:
            print("No such record found")
        else:
            for m in d:
                for n in m:
                    print(n,end="\t")
                print()
    elif ch==2:
        s=input("enter your non-select query:\n")
        cur.execute(s)
        conn.commit()
        print("Query executed")
        print("Check out the records")
        cur.execute("select * from EMPLOYEES")
        p=cur.fetchall()
        for m in p:
            for n in m:
                print(n,end="\t")
            print()
    else:
        print("invalid choice")
 

def UserChoiceQuery():
    print("Only execute select query")
    s=input("enter your select command query\n")
    s=s.lower()
    if "select" not in s:
        print("Invalid query.....Give Select query only")
    else:
        cur.execute(s)
        d=cur.fetchall()
        if d==[]:
            print("No such query found ")
        else:
            for m in d:
                for n in m:
                    print(n,end="\t")
                print()



print("\n\n\t\t WELCOME TO COMPANY DATABASE\n\n")
ch=int(input("Press 1: To login as ADMIN\nPress 2: To login as USER\n\n"))
if ch==1:
    x=input("Enter Admin Password:")
    if x=="COMPANY20":
        print("\n\n\t\tWELCOME ADMIN : HERE IS THE MENU \n\n")
        while True:
            print("\n")
            AdminMenu()
            print("\n")
            n=int(input("enter your choice:"))
            if n==1:
                Addemployee()

            elif n==2:
                RemoveAllemployees()     
      
            elif n==3:
                RemoveemployeeColumn()    
     
            elif n==4:
                Updateemployee()  
        
            elif n==5:
                Searchemployee()   

                        
            elif n==6:
                DisplayAllemployees()

            elif n==7:
                Verifyempid()      
      
            elif n==8:
                SearchemployeeColumn()

         
            elif n==9:
                AdminChoiceQuery_employee()    
        
            elif n==10:
                break

            else:
                 print("Invalid Choice")

      else:
             print("Invalid password")

elif ch==2:
    nm=input("Enter Username:")
    print("\n\n\t\tWELCOME USER"+nm+" : HERE IS THE MENU \n\n")
    while True:
        print("\n")
        UserMenu()
        print("\n")
        n=int(input("enter your choice: "))
        if n==1:
            Searchemployee()      
 
        elif n==2:
            DisplayAllemployees()     
   
        elif n==3 or n==4:
            SearchemployeeColumn() 
       
        elif n==5:
            UserChoiceQuery()

        elif n==6:
            break

        else:
            print("Invalid Choice")
