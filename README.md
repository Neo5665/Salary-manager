# Salary-manager
#My collection






    class Employee(object):
    def __init__(self,empid,name,age,email,contact,job_post,addr,doj):
        self.__name=name
        self.__age=age
        self.__email=email
        self.__contact=contact
        self.__job_post=job_post
        self.__addr=addr
        self.empid=empid
        self.__doj=doj
        
        
    @property
    def email(self):
        return self.__email
    @email.setter
    def email(self,email):
          if (email!=None) and ((email.index("@"))<(email.index("."))) and(email.count("@"))==1:
            self.__email=email
          else:
            print "invalid email"



    @property
    def name(self):
        return self.__name
    @name.setter
    def name(self,name):
        if name==None:
            raise "invalid name"
        else:
           self.__name=name



    @property
    def age(self):
        return self.__age
    @age.setter
    def age(self,age):
        if age!=None:
            self.__age=age
        else:
            raise "invalid name"



    @property
    def contact(self):
        return self.__contact
    @contact.setter
    def contact(self,contact):
        if len(contact)==10:
            self.__contact=contact
        else:
            print"invalid contact"


    @property
    def addr(self):
        return self.__addr
    @addr.setter
    def addr(self,addr):
        if len(addr)==12:
            self.__addr=addr
        else:
            print"invalid account no"
    @property
    def job_post(self):
        return self.__job_post
    @job_post.setter
    def job_post(self,job_post):
        if job_post!=None:
            self.job_post=job_post

    @property
    def doj(self):
        return self.__doj
    @doj.setter
    def doj(self,doj):
        if doj!=None:
            self.__doj=doj
        else:
            raise "invalid doj"





    emp_list={}
    empid=0


    @staticmethod
    def addemp():
        name=str(raw_input("enter name of employee: "))
        age=input("enter age: ")
        email=str(raw_input("enter email: "))
        contact=input("Enter Contact no: ")
        print ("Select the Job Post  1:CEO 2:HR 3:Employee")
        job_post=input("Enter Job Post: ")
        if job_post==1:
            job_post="CEO"
        elif job_post==2:
            job_post="HR"
        elif job_post==3:
            job_post="Employee"
        else:
            print "Invalid Job Post"
        addr=str(raw_input("adress of employee: "))
        print "enter in DD/MM/YY format"
        doj=str(raw_input("Enter Date of Joining: "))


        try:
            f=open("salary.txt","r")
        except IOError:
            print ("file not found")
        else:
            p=f.read()
            Employee.emp_list=eval(p)
            f.close()

        for i in Employee.emp_list:
            Employee.empid=i
        Employee.empid+=1


        k=Employee(Employee.empid,name,age,email,contact,job_post,addr,doj)
        Employee.emp_list[k.empid]=list([k.name,k.age,k.email,k.contact,k.job_post,k.addr,k.doj])


        try:
            f=open("salary.txt","w")
        except IOError:
            print ("file not found")
        else:
            f.write(str(Employee.emp_list))
            f.close()

    @staticmethod
    def totl():
        try:
            f=open("salary.txt","r")
        except IOError:
            print ("file not found")
        else:
            p=f.read()
            Employee.emp_list=eval(p)
            f.close()

        for i in Employee.emp_list:
            pass
        print "Total Number Of Employees Are: ",i


    @staticmethod
    def display():
        try:
            f=open("salary.txt","r")
        except IOError:
            print ("file not found")
        else:
            k=f.read()
            Employee.emp_list=eval(k)
            f.close()
        print "empid\t  name\t  age\t\t email\t\t     contact\t jobpost\t Address\t date of joining"
        for i in Employee.emp_list:
              print i,"\t\t" ,Employee.emp_list[i][0] ,"\t\t",Employee.emp_list[i][1], "\t\t",Employee.emp_list[i][2],  Employee.emp_list[i][3],"\t" ,Employee.emp_list[i][4],"\t", Employee.emp_list[i][5] ,"\t",Employee.emp_list[i][6]



    @staticmethod
    def update():

        try:
            f=open("salary.txt","r")
        except IOError:
            print ("file not found")
        else:
            k=f.read()
            Employee.emp_list=eval(k)
            f.close()

        u=input("enter the Employee ID to update")
        Employee.emp_list[u][0]=raw_input("Enter the name of Employee: ")
        Employee.emp_list[u][1]=input("enter age: ")
        Employee.emp_list[u][2]=str(raw_input("enter email: "))
        Employee.emp_list[u][3]=input("Enter Contact no: ")
        Employee.emp_list[u][4]=str(raw_input("Enter Job Post: "))
        Employee.emp_list[u][5]=str(raw_input("Address of employee: "))
        Employee.emp_list[u][6]=str(raw_input("Enter Date of Joining: "))

        try:
            f=open("salary.txt","w")
        except IOError:
            print ("file not found")
        else:
            f.write(str(Employee.emp_list))
            f.close()

    @staticmethod
    def Delete():
        try:
            f=open("salary.txt","r")
        except IOError:
            print ("file not found")
        else:
            k=f.read()
            Employee.emp_list=eval(k)
            f.close()

        emp=input("Enter Employee ID to delete the employee")
        del Employee.emp_list[emp]
        print "employee is deleted"


        try:
            f=open("salary.txt","w")
        except IOError:
            print ("file not found")
        else:
            f.write(str(Employee.emp_list))
            f.close()



    @staticmethod
    def search():


        try:
            f=open("salary.txt","r")
        except IOError:
            print ("file not found")
        else:
            k=f.read()
            Employee.emp_list=eval(k)
            f.close()


            search = input("Enter the Employee ID")
            for i in Employee.emp_list:
                if(search == i):
                    print "empid: ",i
                    print "name: ",Employee.emp_list[i][0]
                    print"age: ",Employee.emp_list[i][1]
                    print"email: ",Employee.emp_list[i][2]
                    print"contact: ",Employee.emp_list[i][3]
                    print"jobpost: ",Employee.emp_list[i][4]
                    print"Address: ",Employee.emp_list[i][5]
                    print"date of joining: ",Employee.emp_list[i][6]





    class Salary(Employee):

    @staticmethod
    def Total_salary():
        try:
                 f=open("salary.txt","r")
        except IOError:
                print ("file not found")
        else:
                k=f.read()

                Employee.emp_list=eval(k)


                f.close()


        p = input("Enter the Employee ID")
        for i in (Employee.emp_list):
            if(p==i):
                print "Enter the Month: \n1:Jan \n2:Feb \n3:Mar \n4:Apr \n5:MAy \n6:June \n7:Jul \n8:Aug \n9:Sep \n10:Oct \n11:Nov \n12:Dec"
                mo=input("Enter Your Choice")
                if mo==1:
                    mo="January"
                elif mo==2:
                    mo="February"
                elif mo==2:
                    mo="March"
                elif mo==2:
                    mo="April"
                elif mo==2:
                    mo="May"
                elif mo==2:
                    mo="June"
                elif mo==2:
                    mo="July"
                elif mo==2:
                    mo="August"
                elif mo==2:
                    mo="September"
                elif mo==2:
                    mo="October"
                elif mo==2:
                    mo="November"
                elif mo==2:
                    mo="December"


                basic_pay=input("Enter Basic Salary")

                #Dearness Allowance-----------------------------------------------------------
                DA=basic_pay*0.09
                print"DA: ", DA


                print "House Type \n 1.Rented \n 2.Non-Rented"
                u=input("Enter Your Choice")
                if u==1:
                    HRA=12000
                    print "HRA: ",HRA
                elif u==2:
                    HRA=0
                    print "HRA: ",HRA
                else:
                    print "Invalid Choice"




                #Conveyance Allowance----------------------------------------------------------
                print "what do you prefer for travelling \n 1.By Company Bus \n 2.Private Vehicle"
                k=input("enter your choice")
                if k==1:
                    CA=0
                    print"CA", CA
                elif k==2:
                    km=input("Enter Total No. of KM travelled per day")
                    avg=40.0
                    CA=(km/avg)*84*30
                    if CA>1600:
                        CA=1600
                        print" CA",CA

                    else:
                        CA=CA
                    print "CA",CA
                else:
                    print "Invalid Choice"
                #Medical Allowance---------------------------------------------------------------------
                MA=1000
                print "MA:",MA


                #Other Perquisites------------------------------------------------------
                print"Add Other Perquisites? \n1:YES \n 2:NO "
                m=input("enter your Choice")
                if m==1:
                    print "Enter Other Perquisites "

                    bonus=input("Enter Bonus Amount")
                    hours=input("Enter Extra Hours")
                    wages_extra_work=hours*100
                    print"Bonus", bonus,"\n","Wages: ",wages_extra_work


                elif m==2:
                    print "Other Perquisites=0"
                    bonus=wages_extra_work=0


                Gross_Salary=basic_pay+DA+HRA+CA+MA+bonus+wages_extra_work
                print"Gross Salary: ", Gross_Salary

                #Deductions

                #Income Tax---------------------------------------------------------
                if basic_pay>0 and basic_pay<=21000:
                    income_tax=0
                    print"Income Tax",income_tax
                elif basic_pay>21000 and basic_pay<=42000:
                    income_tax=(basic_pay-21000)*0.05
                    print"Income Tax",income_tax
                elif basic_pay>42000:
                    income_tax=(basic_pay-21000)*0.2
                    print"Income Tax",income_tax
                else:
                    print "Incorrect Input"
                DA_tax=DA*0.07
                print"DA Tax: ", DA_tax


                rent=input("Enter Monthly rent")
                second=rent-(0.1*(basic_pay+DA))
                third=0.5*(basic_pay+DA)
                list=[HRA,second,third]
                list.sort()
                if HRA>=list[0]:
                    HRA_tax=(HRA-list[0])*0.2
                elif HRA<=list[0]:
                    HRA_tax=(list[0]-HRA)*0.2
                    print"HRA Tax: ", HRA_tax

                #Professional Tax-----------------------------------------------------
                print "Select Gender of Employee\n 1:Male\n 2:Female"
                g=input("Enter Choice")
                if g==1:
                    if basic_pay>0 and basic_pay<=7500:
                        prof_tax=0
                        print "Professional Tax: ",prof_tax
                    elif basic_pay>=7501 and basic_pay<=10000:
                        prof_tax=175
                        print "Professional Tax: ",prof_tax
                    elif basic_pay>=10001:
                        prof_tax=200
                        print "Professional Tax: ",prof_tax
                    else:
                        print"Incorrect Input"
                elif g==2:
                    if basic_pay>0 and basic_pay<=10000:
                        prof_tax=0
                        print "Professional Tax: ",prof_tax
                    elif basic_pay>=10001:
                        prof_tax=200
                        print "Professional Tax: ",prof_tax
                    else:
                        print "Incorrect Input"
                MA_tax=MA*0.3
                print "MA_Tax: ",MA_tax


                pf=basic_pay*0.12


                Deductions=prof_tax + MA_tax + HRA_tax + DA_tax + income_tax + pf
                print "Deductions: ",Deductions


                Total_Salary= Gross_Salary - Deductions
                print "Total Salary is: ",Total_Salary





                Employee.emp_list[p].append(basic_pay)
                Employee.emp_list[p].append(HRA)
                Employee.emp_list[p].append(DA)
                Employee.emp_list[p].append(CA)
                Employee.emp_list[p].append(MA)
                Employee.emp_list[p].append(bonus)
                Employee.emp_list[p].append(wages_extra_work)
                Employee.emp_list[p].append(Gross_Salary)
                Employee.emp_list[p].append(income_tax)
                Employee.emp_list[p].append(DA_tax)
                Employee.emp_list[p].append(HRA_tax)
                Employee.emp_list[p].append(prof_tax)
                Employee.emp_list[p].append(MA_tax)
                Employee.emp_list[p].append(pf)
                Employee.emp_list[p].append(Deductions)
                Employee.emp_list[p].append(Total_Salary)
                Employee.emp_list[p].append(mo)

            try:
                f=open("salary.txt","w")
            except IOError:
                print ("file not found")
            else:
                f.write(str(Employee.emp_list))

                f.close()

    @staticmethod
    def display():
        try:
            f=open("salary.txt","r")
        except IOError:
            print ("file not found")
        else:
            k=f.read()
            Employee.emp_list=eval(k)
            f.close()
        print "empid\t  name\t  age\t\t email\t\t     contact\t jobpost\t Address\t date of joining\t\tMonth of Salary  \tGross Salary  \tTotal Deductions  \tTotal Salary"
        for i in Employee.emp_list:
              print i,"\t\t" ,Employee.emp_list[i][0] ,"\t\t",Employee.emp_list[i][1], "\t\t",Employee.emp_list[i][2],  Employee.emp_list[i][3],"\t" ,Employee.emp_list[i][4],"\t", Employee.emp_list[i][5] ,"\t",Employee.emp_list[i][6],"\t\t\t\t\t",Employee.emp_list[i][23],"\t\t\t",Employee.emp_list[i][14],"\t\t\t",Employee.emp_list[i][21],  "\t\t\t",Employee.emp_list[i][22]
    @staticmethod
    def display1():
            try:
                 f=open("salary.txt","r")
            except IOError:
                print ("file not found")
            else:
                k=f.read()

                Employee.emp_list=eval(k)


                f.close()
            search = raw_input("Enter the Employee ID")
            for i in Employee.emp_list:
                if(search == str(i)):

                    print"-"*94
                    print"| \t\t\t\t\t\t\t\t\t\t      Rs        \t\t\t\t\t\t\t\t\t |"
                    print"| \t\t\t\t\t\t\t      Payroll Management System        \t\t\t\t\t\t     |"
                    print "| Employee Name   : ",Employee.emp_list[i][0],"\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t     |"
                    print"| Employee Age    : ",Employee.emp_list[i][1], "\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t     |"
                    print"| Employee Email  : ",Employee.emp_list[i][2], "\t\t\t\t\t\t\t\t\t\t\t\t\t\t |"
                    print"| Employee Contact: ",Employee.emp_list[i][3], "\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t |"
                    print"| Employee Jobpost: ",Employee.emp_list[i][4], "\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t     |"
                    print"| Employee Address: ",Employee.emp_list[i][5], "\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t |"
                    print"| Employee DateOfJoining : ",Employee.emp_list[i][6], "\t\t\t\t\t\t\t\t\t\t\t\t\t\t |"
                    print"| \t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t |"
                    print"| \t Gross Salary \t\t\t\t\t\t\t Deductions \t\t\t\t\t\t\t\t     |"
                    print"| Basic Pay : ",Employee.emp_list[i][7], "\t\t\t\t\t""  Income Tax: ",Employee.emp_list[i][15],"\t\t\t\t\t\t\t\t |"
                    print"| HRA : ",Employee.emp_list[i][8], "\t\t\t\t\t\t\t  Tax on HRA :",Employee.emp_list[i][17],"\t\t\t\t\t\t\t     |"
                    print"| DA :  ",Employee.emp_list[i][9], "\t\t\t\t\t\t  Tax on DA:  ",Employee.emp_list[i][16],"\t\t\t\t\t\t\t\t |"
                    print"| CA  :  ",Employee.emp_list[i][10],"\t\t\t\t\t\t  Professional Tax :  ",Employee.emp_list[i][18],"\t\t\t\t\t\t\t |"
                    print"| MA : ",Employee.emp_list[i][11],"\t\t\t\t\t\t\t  Tax on MA : ",Employee.emp_list[i][19],"\t\t\t\t\t\t\t     |"
                    print"| Bonus paid :",Employee.emp_list[i][12],"\t\t\t\t\t  Provident Fund Tax : ",Employee.emp_list[i][20],"\t\t\t\t\t\t |"
                    print"| Wages for extra hours :",Employee.emp_list[i][13], "\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t |"
                    print"|","-"*90, "|"
                    print"| Gross - ",Employee.emp_list[i][14],"\t\t\t\t\t\t ","Total Deductions - ",Employee.emp_list[i][21], "\t\t\t\t\t\t |"
                    print"| \t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t |"
                    print"| \t\t\t\t\t\t\t\t\t Net Salary is : ",Employee.emp_list[i][22], "\t\t\t\t\t\t\t\t |"
                    print"| _________________________ \t\t\t\t\t\t\t\t\t ___________________________ |"
                    print"|    Employee's Signature      ""\t\t\t\t\t\t\t\t\t\t"      "Director's Signatue      |"
                    print"-"*94



    s=Salary
    while True:
        print "enter your choice\n 1:Add Employee  \n 2:Search Employee \n 3:Update Employee \n 4:Delete Employee \n 5:Display Employee \n 6:Total Salary \n 7:Total No of Employees\n 8:Print Salary Slip \n 9:Exit from the Process"
        choice=input("enter your choice:  ")
        if choice==1:
            s.addemp()
        elif choice==2:
            s.search()
        elif choice==3:
            s.update()
        elif choice==4:
            s.Delete()
        elif choice==6:
            s.Total_salary()
        elif choice==7:
            s.totl()
        elif choice==5:
            s.display()
        elif choice==8:
            s.display1()
        elif choice==9:
            break
        else:
            print "invalid choice!!!"
