# Hospital-management-using-python
Basic project for school using pyhton
# start
from tkinter import *
from tkinter import messagebox
import mysql.connector as sq
from tkinter import ttk

#conn=sq.connect(host="localhost",user="kaustab",passwd="kaustab7@21",database="hospital")
#cur=conn.cursor()
def bill():
    form=Tk()       # creating window
    form.title("Medicene Bill")
    form.geometry("1400x600")
    form.resizable(False,False)
    form.configure(bg = "red")
    Label(form,text="Bill for general Physician",font="bold 35 italic",bg="red",fg="white").place(x=40,y=50)
    Label(form,text="Optional for donation",font="bold 20 italic",bg="red",fg="white").place(x=40,y=110)
    Label(form,text="Rs100-Rs3000 variation",font="bold 10 italic",bg="red",fg="yellow").place(x=40,y=150)
    def Exit():
        form.destroy()
        
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=530)

def Medic():
    form=Tk()
    form.geometry("1000x500")
    form.title("bill management")
    form.resizable(False,False)

    def Reset():
        entry_paracetamol.delete(0,END)
        entry_crosine.delete(0,END)
        entry_azythromycin.delete(0,END)
        entry_babajika.delete(0,END)
        entry_dygine.delete(0,END)
        entry_hygene.delete(0,END)
        entry_jumbo.delete(0,END)

    def Total():
        try:a1=int(paracetamol.get())
        except: a1=0

        try:a2=int(crosine.get())
        except: a2=0

        try:a3=int(azythromycin.get())
        except: a3=0

        try:a4=int(babajika.get())
        except: a4=0

        try:a5=int(dygine.get())
        except: a5=0

        try:a6=int(hygene.get())
        except: a6=0

        try:a7=int(jumbo.get())
        except: a7=0

        #define cost per item
        c1=6*a1
        c2=10*a2
        c3=6*a3
        c4=100*a4
        c5=700*a5
        c6=5*a6
        c7=6*a7
            

        


        lbl_total=Label(f2,font=('aria',20,'bold'),text="Total",width=16,fg="lightyellow",bg="black")
        lbl_total.place(x=0,y=50)


        entry_total=Entry(f2,font=('aria',20,'bold'),textvariable=Total_bill,bd=6,width=15,bg="lightgreen")
        entry_total.place(x=20,y=100)

        totalcost=c1+c2+c3+c4+c5+c6+c7
        string_bill="Rs.",str('%.2f'  %totalcost)
        Total_bill.set(string_bill)
        


        

    Label(text="MEDICAL STORE",bg="black",fg="white",font=("calibri",33),width="300",height="2").pack()
#menucard
    f=Frame(form,bg="green",highlightbackground="black",highlightthickness=1,width=300,height=370)
    f.place(x=10,y=118)

    Label(f,font=("lucidia Calligraphy",15,'bold'),text="Paracetamol...Rs.6/1 Tablet",fg="black",bg="lightgreen").place(x=10,y=80)
    Label(f,font=("lucidia Calligraphy",15,'bold'),text="Crosine...Rs.10/1 Tablet",fg="black",bg="lightgreen").place(x=10,y=110)
    Label(f,font=("lucidia Calligraphy",15,'bold'),text="Azythromycin...Rs.6/1 Tablet",fg="black",bg="lightgreen").place(x=10,y=140)
    Label(f,font=("lucidia Calligraphy",15,'bold'),text="Baba ji ka..Rs.100/1 Tablet",fg="black",bg="lightgreen").place(x=10,y=170)
    Label(f,font=("lucidia Calligraphy",15,'bold'),text="Dygine...Rs.700/1 bottle",fg="black",bg="lightgreen").place(x=10,y=200)
    Label(f,font=("lucidia Calligraphy",15,'bold'),text="Hygene...Rs.5/1 Tablet",fg="black",bg="lightgreen").place(x=10,y=230)
    Label(f,font=("lucidia Calligraphy",15,'bold'),text="Jumbo...Rs.6/1 Tablet",fg="black",bg="lightgreen").place(x=10,y=260)
    #bill
    f2=Frame(form,bg="lightyellow",highlightbackground="black",highlightthickness=1,width=300,height=370)
    f2.place(x=690,y=118)

    Bill=Label(f2,text='BILL',font=('calibri',20),bg="lightyellow")
    Bill.place(x=120,y=10)

    


#entrywork
    f1=Frame(form,bd=5,height=370,width=300,relief=RAISED)
    f1.pack()


    Paracetamol=StringVar()
    Crosine=StringVar()
    Azythromycin=StringVar()
    Babajika=StringVar()
    Dygine=StringVar()
    Hygene=StringVar()
    Jumbo=StringVar()
#label
    lbl_paracetamol=Label(f1,font=("aria",20,"bold"),text="Paracetamol",width=12,fg="blue")
    lbl_crosine=Label(f1,font=("aria",20,"bold"),text="Crosine",width=12,fg="blue")
    lbl_azythromycin=Label(f1,font=("aria",20,"bold"),text="Azythromycin",width=12,fg="blue")
    lbl_babajika=Label(f1,font=("aria",20,"bold"),text="Babajika",width=12,fg="blue")
    lbl_dygine=Label(f1,font=("aria",20,"bold"),text="Dygine",width=12,fg="blue")
    lbl_hygene=Label(f1,font=("aria",20,"bold"),text="Hygene",width=12,fg="blue")
    lbl_jumbo=Label(f1,font=("aria",20,"bold"),text="Jumbo",width=12,fg="blue")
    
    lbl_paracetamol.grid(row=1,column=0)
    lbl_crosine.grid(row=2,column=0)
    lbl_azythromycin.grid(row=3,column=0)
    lbl_babajika.grid(row=4,column=0)
    lbl_dygine.grid(row=5,column=0)
    lbl_hygene.grid(row=6,column=0)
    lbl_jumbo.grid(row=7,column=0)
#entry
    entry_paracetamol=Entry(f1,font=("aria",20,'bold'),textvariable=Paracetamol,bd=6,width=8,bg="white")
    entry_crosine=Entry(f1,font=("aria",20,'bold'),textvariable=Crosine,bd=6,width=8,bg="white")
    entry_azythromycin=Entry(f1,font=("aria",20,'bold'),textvariable=Azythromycin,bd=6,width=8,bg="white")
    entry_jumbo=Entry(f1,font=("aria",20,'bold'),textvariable=Babajika,bd=6,width=8,bg="white")
    entry_babajika=Entry(f1,font=("aria",20,'bold'),textvariable=Dygine,bd=6,width=8,bg="white")
    entry_dygine=Entry(f1,font=("aria",20,'bold'),textvariable=Hygene,bd=6,width=8,bg="white")
    entry_hygene=Entry(f1,font=("aria",20,'bold'),textvariable=Jumbo,bd=6,width=8,bg="white")
    
      
    entry_paracetamol.grid(row=1,column=1)
    entry_crosine.grid(row=2,column=1)
    entry_azythromycin.grid(row=3,column=1)
    entry_babajika.grid(row=4,column=1)
    entry_dygine.grid(row=5,column=1)
    entry_hygene.grid(row=6,column=1)
    entry_jumbo.grid(row=7,column=1)
#buttons

    btn_reset=Button(f1,bd=5,fg="black",bg="lightblue",font=("ariel",16,"bold"),width=10,text="Reset",command=Reset)
    btn_reset.grid(row=8,column=0)

    btn_total=Button(f1,bd=5,fg="black",bg="lightblue",font=("ariel",16,"bold"),width=10,text="Total",command=Total)
    btn_total.grid(row=8,column=1)


    
    




def bill2():
    form=Tk()       # creating window
    form.title("Medicene Bill")
    form.geometry("1400x600")
    form.resizable(False,False)
    form.configure(bg = "red")
    Label(form,text="Bill for SURGERY",font="bold 35 italic",bg="red",fg="white").place(x=40,y=50)
    Label(form,text="Optional for donation",font="bold 20 italic",bg="red",fg="white").place(x=40,y=110)
    Label(form,text="Rs1000-Rs3000 variation",font="bold 10 italic",bg="red",fg="yellow").place(x=40,y=150)
    def Exit():
        form.destroy()
        
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=530)


def BMI():
   def reset_entry():
    age_tf.delete(0,'end')
    height_tf.delete(0,'end')
    weight_tf.delete(0,'end')
   def calculate_bmi():
    kg = int(weight_tf.get())
    m = int(height_tf.get())/100
    bmi = kg/(m*m)
    bmi = round(bmi, 1)
    bmi_index(bmi)

   def bmi_index(bmi):
       if bmi < 18.5:
           messagebox.showinfo('bmi-pythonguides', f'BMI = {bmi} is Underweight')
       elif (bmi > 18.5) and (bmi < 24.9):
           messagebox.showinfo('bmi-pythonguides', f'BMI = {bmi} is Normal')
       elif (bmi > 24.9) and (bmi < 29.9):
           messagebox.showinfo('bmi-pythonguides', f'BMI = {bmi} is Overweight')
       elif (bmi > 29.9):
           messagebox.showinfo('bmi-pythonguides', f'BMI = {bmi} is Obesity') 
       else:
           messagebox.showerror('bmi-pythonguides', 'something went wrong!')   

   ws = Tk()
   ws.title('PythonGuides')
   ws.geometry('400x300')
   ws.config(bg='#686e70')

   var = IntVar()
  
   frame = Frame(
       ws,
       padx=10, 
       pady=10
    )
   frame.pack(expand=True)


   age_lb = Label(
       frame,
       text="Enter Age (2 - 120)"
       )
   age_lb.grid(row=1, column=1)

   age_tf = Entry(
       frame,

       )
   age_tf.grid(row=1, column=2, pady=5)
   gen_lb = Label(
       frame,
       text='Select Gender'
       )
   gen_lb.grid(row=2, column=1)
   frame2 = Frame(
       frame
       )
   frame2.grid(row=2, column=2, pady=5)
   male_rb = Radiobutton(
       frame2,
       text = 'Male',
       variable = var,
       value = 1
       )
   male_rb.pack(side=LEFT)
   female_rb = Radiobutton(
       frame2,
       text = 'Female',
       variable = var,
       value = 2
       )
   female_rb.pack(side=RIGHT)
   height_lb = Label(
       frame,
       text="Enter Height (cm)  "
       )
   height_lb.grid(row=3, column=1)
   weight_lb = Label(
       frame,
       text="Enter Weight (kg)  ",
       )
   weight_lb.grid(row=4, column=1)
   height_tf = Entry(
       frame,
       )
   height_tf.grid(row=3, column=2, pady=5)
   weight_tf = Entry(
     frame,
     )
   weight_tf.grid(row=4, column=2, pady=5)
   frame3 = Frame(
       frame
       )
   frame3.grid(row=5, columnspan=3, pady=10)
   cal_btn = Button(
       frame3,
       text='Calculate',
       command=calculate_bmi
       )
   cal_btn.pack(side=LEFT)

   reset_btn = Button(
       frame3,
       text='Reset',
       command=reset_entry
       )
   reset_btn.pack(side=LEFT)

   exit_btn = Button(
       frame3,
       text='Exit',
       command=lambda:ws.destroy()
       )
   exit_btn.pack(side=RIGHT)
   ws.mainloop()

   def calculate_bmi():
       kg = int(weight_tf.get())
       m = int(height_tf.get())/100
       bmi = kg/(m*m)
       bmi = round(bmi, 1)
       bmi_index(bmi)
   def bmi_index(bmi):
       if bmi < 18.5:
           messagebox.showinfo('bmi-pythonguides', f'BMI = {bmi} is Underweight')
       elif (bmi > 18.5) and (bmi < 24.9):
           messagebox.showinfo('bmi-pythonguides', f'BMI = {bmi} is Normal')
       elif (bmi > 24.9) and (bmi < 29.9):
           messagebox.showinfo('bmi-pythonguides', f'BMI = {bmi} is Overweight')
       elif (bmi > 29.9):
           messagebox.showinfo('bmi-pythonguides', f'BMI = {bmi} is Obesity') 
       else:
           messagebox.showerror('bmi-pythonguides', 'something went wrong!')

    

def Prescription():
    form=Tk()       # creating window
    form.title("Medicene surgery system")
    form.geometry("700x700")
    form.resizable(False,False)
    form.configure(bg = "red")
    Label(form,text="Enter details",font="bold 35 italic",bg="red",fg="white").place(x=40,y=50)
    Label(form,text="For a Surgeon",font="bold 20 italic",bg="red",fg="white").place(x=40,y=100)
    v1 = StringVar()
    v2 = StringVar()
    v3 = StringVar()
    v4 = StringVar()
    v5 = StringVar()
    v6 = StringVar()
    v7 = StringVar()
    v8 = StringVar()
    Label(form,text="Enter your name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 140)
    T1 = Entry(form,textvariable=v1,width = 40,bg="white",fg="black",borderwidth=4).place(x = 200,y = 140)
    Label(form,text="No. of Units",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 180)
    T2 = Entry(form,textvariable=v2,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 180)
    Label(form,text="Enter Age",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 220)
    T3 = Entry(form,textvariable=v3,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 220)
    Label(form,text="Enter Date",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 260)
    T4 = Entry(form,textvariable=v4,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 260)
    Label(form,text="Enter Doctor Name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 300)
    T5 = Entry(form,textvariable=v5,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 300)
    Label(form,text="Enter procedure",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 340)
    T6 = Entry(form,textvariable=v6,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 340)
    Label(form,text="Enter no of prev.medical info",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 380)
    T7 = Entry(form,textvariable=v7,width = 40,bg="white",fg="black",borderwidth=5).place(x = 290,y = 380)
    Label(form,text="Enter Gender",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 420)
    T8 = Entry(form,textvariable=v8,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 420)
    def submit():
        nm=v1.get()
        qt=v2.get()
        aga=v3.get()
        data=v4.get()
        dn=v5.get()
        pp=v6.get()
        prev=v7.get()
        gen=v8.get()
        
        
        sql="Insert into pris2 Values(%s,%s,%s,%s,%s,%s,%s,%s);"
        data=(nm,qt,aga,data,dn,pp,prev,gen)
        cur.execute(sql,data)
        conn.commit()
        messagebox.showinfo("Done","submitted sucessfully")
    Button(form,text="Submit",border=3,command=submit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=480)
    def Exit():
        form.destroy()

        menu()
        
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=530)
    def B2():
       

        bill2()
        
    Button(form,text="Check",border=3,command=B2,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=590)
def age():
    form=Tk()       # creating window
    form.title("Age Calculator")
    form.geometry("700x600")
    form.resizable(False,False)
    form.configure(bg = "black")
    Label(form,text="Age Calculator!",font="bold 35 italic",bg="black",fg="red").place(x=40,y=50)
    Label(form,text="pitty on the one who opens it",font="bold 20 italic",bg="black",fg="orange").place(x=40,y=110)
    

    Label(text="Name",font="bold 23",bg='black',fg='white',borderwidth=3).place(x=200,y=250)
    Label(text="Year",font="bold 23",bg='black',fg='white',borderwidth=3).place(x=200,y=300)
    Label(text="Month",font="bold 23",bg='black',fg='white',borderwidth=3).place(x=200,y=350)
    Label(text="Day",font="bold 23",bg='black',fg='white',borderwidth=3).place(x=200,y=400)

    nameValue=StringVar()
    yearValue=StringVar()
    monthValue=StringVar()
    dayValue=StringVar()
    nameEntry=Entry(form,textvariable=nameValue,width=30,bg="white",fg="black",bd=3,font=20)
    nameEntry.place(x=300,y=250)
    yearEntry=Entry(form,textvariable=yearValue,width=30,bg="white",fg="black",bd=3,font=20)
    yearEntry.place(x=300,y=300)
    monthEntry=Entry(form,textvariable=monthValue,bg="white",fg="black",width=30,bd=3,font=20)
    monthEntry.place(x=300,y=350)
    dayEntry=Entry(form,textvariable=dayValue,width=30,bg="white",fg="black",bd=3,font=20)
    dayEntry.place(x=300,y=400)
    def submit():
        nm=v1.get()
        qt=v2.get()
        sql="Insert into T1 Values(%s,%s,%s,%s);"
        data=(nm,qt)
        cur.execute(sql,data)
        conn.commit()
        calculateAge()
    Button(form,text="Submit",border=3,command=submit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=480)

    def Exit():
        form.destroy()
        menu()
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=530)


def thankyou():
    main=Tk()
    main.title("exit")
    main.geometry("700x600")
    main.resizable(False,False)
    main.configure(bg="black")
    Label(main,text=" THANK YOU FROM EUPHORIA",font="georgia 30 bold",bg="black",fg="white").place(x=-7,y=50)
    Label(main,text="you will regret!",font="georgia 20 bold",bg="black",fg="yellow").place(x=30,y=100)
    

    
def menu():
    main=Tk()
    main.title("MedicalAid System")
    main.geometry("600x600")
    main.resizable(False,False)
    main.configure(bg="red")
    Label(main,text=" welcome to EUPHORIA",font="georgia 30 bold",bg="red",fg="white").place(x=10,y=50)
    Label(main,text=" Menu Page",font="georgia 20 bold",bg="black",fg="yellow").place(x=30,y=100)
    Label(main,text=" not for girls",font="arial 10 italic",bg="white",fg="black").place(x=130,y=280)
   
    def MP():
        main.destroy()
        Prescribed()
    Button(main,text="Medicine Prescribed",border=3,command=MP,font="arial 16 italic",bg="white",fg="black").place(x=80,y=140)
    
    def M():
        main.destroy()
        Medic()
    Button(main,text="Medicine bill",border=3,command=M,font="arial 16 italic",bg="white",fg="black").place(x=380,y=140)

    
    
    def Body():
        main.destroy()
        BMI()
    Button(main,text="Calculate BMI",border=3,command=Body,font="arial 15 italic",bg="white",fg="black").place(x=380,y=280)
    def aga():
        main.destroy()
        age()
    Button(main,text="AGE Calculator(danger)",border=3,command=aga,font="arial 15 italic",bg="white",fg="red").place(x=80,y=280)
    def PP():
        main.destroy()
        Prescription()
    Button(main,text="Surgery",border=3,command=PP,font="arial 15 italic",bg="white",fg="black").place(x=80,y=420)

    def Exit():
        main.destroy()
        login()
    Button(main,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=100,y=500)

def memb():
    memb=Tk()
    memb.title("MedicalAid System")
    memb.geometry("600x600")
    memb.resizable(False,False)
    memb.configure(bg="red")
    Label(memb,text=" welcome to EUPHORIA",font="georgia 30 bold",bg="red",fg="white").place(x=10,y=50)
    Label(memb,text=" Members Page",font="georgia 20 bold",bg="black",fg="yellow").place(x=30,y=100)
    Label(memb,text=" We Can And We Will ",font="arial 10 italic",bg="red",fg="black").place(x=30,y=140)
   
    def M1():
        memb.destroy()
        login2()
    Button(memb,text="Doctor",border=3,command=M1,font="arial 16 italic",bg="white",fg="black").place(x=80,y=170)
    
    def M():
        memb.destroy()
        Manager()
    Button(memb,text="Accounts",border=3,command=M,font="arial 16 italic",bg="white",fg="black").place(x=80,y=280)

    def m():
        memb.destroy()
        login2()
    Button(memb,text="Leave",border=3,command=m,font="arial 16 italic",bg="white",fg="black").place(x=80,y=420)



def Manager():
    memb=Tk()
    memb.title("Hospital Management - Login")
    memb.geometry("790x590")
    memb.configure(bg = "orange")
    v1 = StringVar()
    v2 = StringVar()
    Label(memb,text=" Welcome  ",font="bold 40 italic",bg="Orange",fg="red").place(x = 120,y =0)
    Label(memb,text="           Bringing Joy To Every Member           ",font="bold 19",bg="white",fg="red").place(x = 100,y = 60)
    Label(memb,text="Login",font="bold 25",bg="orange",fg="black").place(x = 20,y = 130)
    Label(memb,text="Enter User ID",font="bold 15 italic",bg="orange",fg="black").place(x = 20,y = 190)
    T1 = Entry(memb,textvariable=v1,width = 90,bg="orange",fg="black",borderwidth=3).place(x = 20,y = 220)
    Label(memb,text="Enter Password",font="bold 15 italic",bg="orange",fg="black").place(x = 20,y = 250)
    T2 = Entry(memb,textvariable=v2,width = 90,bg="orange",fg="black",show="*",borderwidth=3).place(x = 20,y = 280)
    def validate():
        if v1.get()=="kam" and v2.get()=="888":
            memb.destroy()
            Acck()
        else:
            messagebox.showinfo("Confirm","Invalid credentials")
    Button(memb,text="Login",border=2,command=validate,font=" arial 15 bold",bg="black",fg="white",padx=242).place(x=20,y=330)
    def Exit():
        memb.destroy()
        memb()
    Button(memb,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=20,y=400)
    
def mask():
    mask=Tk()
    mask.title("MedicalAid System")
    mask.geometry("800x700")
    mask.resizable(False,False)
    mask.configure(bg="red")
    Label(mask,text=" welcome to KHUSHI Foundation",font="georgia 30 bold",bg="red",fg="white").place(x=10,y=50)
    Label(mask,text=" Menu Page",font="georgia 20 bold",bg="black",fg="yellow").place(x=30,y=100)
    Label(mask,text=" Serivice To Humanity",font="arial 10 italic",bg="white",fg="black").place(x=130,y=140)
   
    def OG():
        mask.destroy()
        ORGAN()
    Button(mask,text="Organ Donation",border=3,command=OG,font="arial 16 italic",bg="white",fg="black").place(x=80,y=180)
    
    def CP():
        mask.destroy()
        Ask()
    Button(mask,text="Charity For Patients",border=3,command=CP,font="arial 16 italic",bg="white",fg="black").place(x=80,y=260)

def Ask():
    form=Tk()       # creating window
    form.title("Operation Details")
    form.geometry("700x700")
    form.resizable(False,False)
    form.configure(bg = "red")
    Label(form,text="Donation Details",font="bold 35 italic",bg="black",fg="white").place(x=40,y=50)
    Label(form,text="For Patients",font="bold 20 italic",bg="black",fg="white").place(x=40,y=100)
    v1 = StringVar()
    v2 = StringVar()
    v3 = StringVar()
    v4 = StringVar()
    v5 = StringVar()
    v6 = StringVar()
    v7 = StringVar()
    v8 = StringVar()
    Label(form,text="Enter your name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 140)
    T1 = Entry(form,textvariable=v1,width = 40,bg="white",fg="black",borderwidth=4).place(x = 200,y = 140)
    Label(form,text="Required Amount",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 180)
    T2 = Entry(form,textvariable=v2,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 180)
    Label(form,text="Enter Patient Name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 220)
    T3 = Entry(form,textvariable=v3,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 220)
    Label(form,text="Enter Your Amount",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 260)
    T4 = Entry(form,textvariable=v4,width = 40,bg="white",fg="black",borderwidth=5).place(x = 250,y = 260)
    Label(form,text="Patient ID",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 300)
    T5 = Entry(form,textvariable=v5,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 300)
    Label(form,text="Enter PH.Number",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 340)

    def submit():
        yn=v1.get()
        rn=v2.get()
        kn=v3.get()
        As=v4.get()
        phr=v5.get()
        
        sql="Insert into T1 Values(%s,%s,%s,%s,%s);"
        data=(yn,rn,kn,As,phr)
        cur.execute(sql,data)
        conn.commit()
        messagebox.showinfo("Done","submitted sucessfully")
    Button(form,text="Submit",border=3,command=submit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=480)
    def Exit():
        form.destroy()
        mask()
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=530)
    

    
    
    
     
def Acck():
    form=Tk()       # creating window
    form.title("Medicene Billing system")
    form.geometry("700x700")
    form.resizable(False,False)
    form.configure(bg = "red")
    Label(form,text="Enter Accout details",font="bold 35 italic",bg="black",fg="white").place(x=40,y=50)
    Label(form,text="For Doctors",font="bold 20 italic",bg="black",fg="white").place(x=40,y=100)
    v1 = StringVar()
    v2 = StringVar()
    v3 = StringVar()
    v4 = StringVar()
    v5 = StringVar()
    v6 = StringVar()
    v7 = StringVar()
    v8 = StringVar()
    Label(form,text="Enter your name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 140)
    T1 = Entry(form,textvariable=v1,width = 40,bg="white",fg="black",borderwidth=4).place(x = 200,y = 140)
    Label(form,text="Enter Doctor's Name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 180)
    T2 = Entry(form,textvariable=v2,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 180)
    Label(form,text="Enter Amount",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 220)
    T3 = Entry(form,textvariable=v3,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 220)
    Label(form,text="Enter GST",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 260)
    T4 = Entry(form,textvariable=v4,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 260)
    Label(form,text="Enter Tax Cutoff",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 300)
    T5 = Entry(form,textvariable=v5,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 300)
    Label(form,text="Enter ",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 340)
    T6 = Entry(form,textvariable=v6,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 340)
    Label(form,text="Enter no of prev.medical info",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 380)
    T7 = Entry(form,textvariable=v7,width = 40,bg="white",fg="black",borderwidth=5).place(x = 290,y = 380)
    Label(form,text="Enter sex",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 420)
    T8 = Entry(form,textvariable=v8,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 420)
    def submit():
        na=v1.get()
        un=v2.get()
        ag=v3.get()
        dat=v4.get()
        dd=v5.get()
        mn=v6.get()
        pm=v7.get()
        ges=v8.get()
        sql="Insert into pris1 Values(%s,%s,%s,%s,%s,%s,%s,%s);"
        data=(na,un,ag,dat,dd,mn,pm,ges)
        cur.execute(sql,data)
        conn.commit()
        messagebox.showinfo("Done","submitted sucessfully")
    Button(form,text="Submit",border=3,command=submit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=480)
    def Exit():
        form.destroy()
        menu()
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=530)
    

    
        

def DISPLAY():
    form=Tk()       # creating window
    form.title("Medicene Billing system")
    form.geometry("600x600")
    form.resizable(False,False)
    form.configure(bg = "white")
    Label(form,text="  Kan pharma ",font="bold 35 italic",bg="black",fg="white").place(x=40,y=50)
    style = ttk.Style()
    style.theme_use('clam')

    # Add a Treeview widget
    tree = ttk.Treeview(form, column=("Name", "Quantity"), show='headings', height=5)
    tree.column("# 1", anchor=CENTER)
    tree.heading("# 1", text="Name")
    tree.column("# 2", anchor=CENTER)
    tree.heading("# 2", text="Qty")

    # Insert the data in Treeview widget
    cur.execute("Select * from T1;")
    data=cur.fetchall()
    for row in data:
        tree.insert('', 'end', text="1", values=(row[0], row[1]))
    tree.place(x=100, y=150)
    form.mainloop()


def Prescribed():
    form=Tk()       # creating window
    form.title("Medicene Billing system")
    form.geometry("700x700")
    form.resizable(False,False)
    form.configure(bg = "red")
    Label(form,text="Enter Priscription details",font="bold 35 italic",bg="black",fg="white").place(x=40,y=50)
    Label(form,text="For general Physician",font="bold 20 italic",bg="black",fg="white").place(x=40,y=100)
    v1 = StringVar()
    v2 = StringVar()
    v3 = StringVar()
    v4 = StringVar()
    v5 = StringVar()
    v6 = StringVar()
    v7 = StringVar()
    v8 = StringVar()
    Label(form,text="Enter your name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 140)
    T1 = Entry(form,textvariable=v1,width = 40,bg="white",fg="black",borderwidth=4).place(x = 200,y = 140)
    Label(form,text="No. of Units",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 180)
    T2 = Entry(form,textvariable=v2,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 180)
    Label(form,text="Enter Age",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 220)
    T3 = Entry(form,textvariable=v3,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 220)
    Label(form,text="Enter Date",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 260)
    T4 = Entry(form,textvariable=v4,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 260)
    Label(form,text="Enter Doctor Name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 300)
    T5 = Entry(form,textvariable=v5,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 300)
    Label(form,text="Enter medicine",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 340)
    T6 = Entry(form,textvariable=v6,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 340)
    Label(form,text="Enter no of prev.medical info",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 380)
    T7 = Entry(form,textvariable=v7,width = 40,bg="white",fg="black",borderwidth=5).place(x = 290,y = 380)
    Label(form,text="Enter sex",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 420)
    T8 = Entry(form,textvariable=v8,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 420)
    def submit():
        na=v1.get()
        un=v2.get()
        ag=v3.get()
        dat=v4.get()
        dd=v5.get()
        mn=v6.get()
        pm=v7.get()
        ges=v8.get()
        sql="Insert into pris1 Values(%s,%s,%s,%s,%s,%s,%s,%s);"
        data=(na,un,ag,dat,dd,mn,pm,ges)
        cur.execute(sql,data)
        conn.commit()
        messagebox.showinfo("Done","submitted sucessfully")
    Button(form,text="Submit",border=3,command=submit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=480)
    def Exit():
        form.destroy()
        menu()
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=530)
    

def ORGAN():
    form=Tk()       # creating window
    form.title("Organ Donation")
    form.geometry("700x700")
    form.resizable(False,False)
    form.configure(bg = "white")
    Label(form,text="Enter Donor details",font="bold 35 italic",bg="white",fg="orange").place(x=40,y=50)
    Label(form,text="For Contract",font="bold 20 italic",bg="white",fg="brown").place(x=40,y=100)
    v1 = StringVar()
    v2 = StringVar()
    v3 = StringVar()
    v4 = StringVar()
    v5 = StringVar()
    v6 = StringVar()
    v7 = StringVar()
    v8 = StringVar()
    Label(form,text="Enter name of Donor",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 140)
    T1 = Entry(form,textvariable=v1,width = 40,bg="white",fg="black",borderwidth=4).place(x = 230,y = 140)
    Label(form,text="Enter Blood Group",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 180)
    T2 = Entry(form,textvariable=v2,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 180)
    Label(form,text="Enter Age",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 220)
    T3 = Entry(form,textvariable=v3,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 220)
    Label(form,text="Enter Date Of Birth",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 260)
    T4 = Entry(form,textvariable=v4,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 260)
    Label(form,text="Enter PH Number",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 300)
    T5 = Entry(form,textvariable=v5,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 300)
    Label(form,text="Enter Organ to be Donated",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 340)
    T6 = Entry(form,textvariable=v6,width = 40,bg="white",fg="black",borderwidth=5).place(x = 270,y = 340)
    Label(form,text="Pick Any One",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 380)
    Label(form,text="Heart",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 420)
    Label(form,text="Eye/Eyes",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 460)
    Label(form,text="Kidneys",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 500)
    Label(form,text="Liver",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 540)
    Label(form,text="Pancreas",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 580)
    Label(form,text="Small Bowel",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 620)
    def submit():
        dp=v1.get()
        kd=v2.get()
        asa=v3.get()
        ap=v4.get()
        ns=v5.get()
        apa=v6.get()
        sql="Insert into pris1 Values(%s,%s,%s,%s,%s,%s);"
        data=(dp,kd,asa,ap,ns,apa)
        cur.execute(sql,data)
        conn.commit()
        messagebox.showinfo("Done","submitted sucessfully")
    Button(form,text="Submit",border=3,command=submit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=150,y=480)
    def Exit():
        form.destroy()
        mask()
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=150,y=530)
   
    




def EMPLOYEE():
    form=Tk()       # creating window
    form.title("Operation Details")
    form.geometry("700x700")
    form.resizable(False,False)
    form.configure(bg = "red")
    Label(form,text="Surgery Details",font="bold 35 italic",bg="black",fg="white").place(x=40,y=50)
    Label(form,text="For Operation",font="bold 20 italic",bg="black",fg="white").place(x=40,y=100)
    v1 = StringVar()
    v2 = StringVar()
    v3 = StringVar()
    v4 = StringVar()
    v5 = StringVar()
    v6 = StringVar()
    v7 = StringVar()
    v8 = StringVar()
    Label(form,text="Enter your name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 140)
    T1 = Entry(form,textvariable=v1,width = 40,bg="white",fg="black",borderwidth=4).place(x = 200,y = 140)
    Label(form,text="Enter your ID No",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 180)
    T2 = Entry(form,textvariable=v2,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 180)
    Label(form,text="Enter Patient Name",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 220)
    T3 = Entry(form,textvariable=v3,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 220)
    Label(form,text="Enter Date Of Surgery",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 260)
    T4 = Entry(form,textvariable=v4,width = 40,bg="white",fg="black",borderwidth=5).place(x = 250,y = 260)
    Label(form,text="Enter Procedure",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 300)
    T5 = Entry(form,textvariable=v5,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 300)
    Label(form,text="Enter No Of Assistants Req.",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 340)
    T6 = Entry(form,textvariable=v6,width = 40,bg="white",fg="black",borderwidth=5).place(x = 290,y = 340)
    Label(form,text="Enter Patient's Address",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 380)
    T7 = Entry(form,textvariable=v7,width = 40,bg="white",fg="black",borderwidth=5).place(x = 250,y = 380)
    Label(form,text="Enter Ph-No",font="bold 15 italic",bg="white",fg="purple").place(x = 20,y = 420)
    T8 = Entry(form,textvariable=v8,width = 40,bg="white",fg="black",borderwidth=5).place(x = 200,y = 420)
    def submit():
        dm=v1.get()
        idn=v2.get()
        pn=v3.get()
        ds=v4.get()
        pr=v5.get()
        ar=v6.get()
        pa=v7.get()
        ph=v8.get()
        sql="Insert into T1 Values(%s,%s,%s,%s,%s,%s,%s,%s);"
        data=(dm,idn,pn,ds,pr,ar,pa,ph)
        cur.execute(sql,data)
        conn.commit()
        messagebox.showinfo("Done","submitted sucessfully")
    Button(form,text="Submit",border=3,command=submit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=480)
    def Exit():
        form.destroy()
        login2()
    Button(form,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=50,y=530)
    

  
def login():
    main=Tk()
    main.title("Hospital Management - Login")
    main.geometry("790x590")
    main.configure(bg = "white")
    v1 = StringVar()
    v2 = StringVar()
    Label(main,text="  Hospital Management  ",font="bold 40 italic",bg="white",fg="red").place(x = 120,y =0)
    Label(main,text="            yanha bawasir ki dawa nhi milti           ",font="bold 19",bg="white",fg="red").place(x = 100,y = 60)
    Label(main,text="Login",font="bold 25",bg="white",fg="black").place(x = 20,y = 130)
    Label(main,text="Enter User ID",font="bold 15 italic",bg="white",fg="black").place(x = 20,y = 190)
    T1 = Entry(main,textvariable=v1,width = 90,bg="white",fg="black",borderwidth=3).place(x = 20,y = 220)
    Label(main,text="Enter Password",font="bold 15 italic",bg="white",fg="black").place(x = 20,y = 250)
    T2 = Entry(main,textvariable=v2,width = 90,bg="white",fg="black",show="*",borderwidth=3).place(x = 20,y = 280)
    def validate():
        if v1.get()=="kan" and v2.get()=="777":
            main.destroy()
            menu()
        else:
            messagebox.showinfo("Confirm","Invalid credentials")
    Button(main,text="Login",border=2,command=validate,font=" arial 15 bold",bg="black",fg="white",padx=242).place(x=20,y=330)
    def Exit():
        main.destroy()
        HOME()
    Button(main,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=20,y=400)
    def ps1():
        main.destroy()
        memb()


    Button(main,text="Login as an Member",border=3,command=ps1,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=20,y=460)


def login2():
    main=Tk()
    main.title("Hospital Doctor - Login")
    main.geometry("790x590")
    main.configure(bg = "Orange")
    v1 = StringVar()
    v2 = StringVar()
    Label(main,text=" Welcome  ",font="bold 40 italic",bg="Orange",fg="red").place(x = 120,y =0)
    Label(main,text="            An Apple A Day Keeps A Doctor Away(Ban Apples)           ",font="bold 19",bg="white",fg="red").place(x = 100,y = 60)
    Label(main,text="Login",font="bold 25",bg="orange",fg="black").place(x = 20,y = 130)
    Label(main,text="Enter User ID",font="bold 15 italic",bg="orange",fg="black").place(x = 20,y = 190)
    T1 = Entry(main,textvariable=v1,width = 90,bg="orange",fg="black",borderwidth=3).place(x = 20,y = 220)
    Label(main,text="Enter Password",font="bold 15 italic",bg="orange",fg="black").place(x = 20,y = 250)
    T2 = Entry(main,textvariable=v2,width = 90,bg="orange",fg="black",show="*",borderwidth=3).place(x = 20,y = 280)
    def validate():
        if v1.get()=="kam" and v2.get()=="666":
            main.destroy()
            EMPLOYEE()
        else:
            messagebox.showinfo("Confirm","Invalid credentials")
    Button(main,text="Login",border=2,command=validate,font=" arial 15 bold",bg="black",fg="white",padx=242).place(x=20,y=330)
    def Exit():
        main.destroy()
        login()
    Button(main,text="back",border=3,command=Exit,font=" arial 15 italic",bg="blue",fg="white",padx=150).place(x=20,y=400)
    
    

def HOME():
    main=Tk()       # creating window
    main.title("HOSPITAL MANAGEMENT SYSTEM")
    main.geometry("650x500")
    #main.resizable(False,False)
    main.configure(bg = "orange")
    Label(main,text="EUPHORIA",font="georgia 50 bold",bg="orange",fg="white").place(x=140,y=50)
    Label(main,text="  HOSPITAL MANAGEMENT SYSTEM ",font="georgia 15 bold",bg="orange",fg="red").place(x=130,y=120)
    def check():
        main.destroy()
        login()
        #messagebox.showinfo("Confirm","Checking the button")
    Button(main,text="Click here to continue",border=3,command=check,font=" arial 25 bold",bg="black",fg="white").place(x=150,y=330)
    def Exit():
        main.destroy()
        thankyou()
    Button(main,text="exit",border=3,command=Exit,font=" arial 15 italic",bg="black",fg="white",padx=150).place(x=150,y=400)
    def sm():
        main.destroy()
        mask()
    Button(main,text="KHUSHI (smile we pass on others)",border=3,command=sm,font=" roman 15 italic",bg="black",fg="white",padx=150).place(x=30,y=450)

#login()
HOME()
#Prescription()
#Prescribed()
#BMI()
#menu()
#DISPLAY()
#age()
#BMI()
#ORGAN()
