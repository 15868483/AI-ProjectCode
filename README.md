from tkinter import *
import json
from logpy import Relation, facts, run, conde, var, eq
import numpy as py
from tkinter import *
from tkinter.scrolledtext import ScrolledText
#.................................................................
root=Tk()
root.geometry("1650x700+0+0")

#.........................................Relation.....................................
#rand1,rand2 needed here they contain input string
def reset():
    rand1.set("")
    rand2.set("")
def destroy():
    root.destroy()

def cal_relation():
    txt.delete(0.0,'end');
    name=e1.get();
    name2=e2.get();
    if __name__=='__main__':
        Root = Relation()
    with open('project.json') as f:
        d = json.loads(f.read())

    for item in d['Root']:
        facts(Root, (list(item.keys())[0], list(item.values())[0]))

    x = var()

    # Depository
    if(name == 'Depository' or name2 == 'Depository' ):
        if(name=='Depository'):
            output = run(0, x, Root(name, x))
        else:
            output = run(0, x, Root(name2, x))
            
        ##print("\nList of " + name + "'s children:")
        for item in output:
            if((name2=="Stock Exchange" and name=="Depository") or (name=="Stock Exchange" and name2=="Depository")):
                txt.insert(END,"It is regulator of Shares where all the Share of Stock exchange are strored")
                break;
            if((name2=="Customer" and name=="Depository") or (name=="Customer" and name2=="Depository")):
                txt.insert(END,"Individual Shares of Each Person are Contained by depository")
                break;
            if((name2=="Broker" and name=="Depository") or (name=="Broker" and name2=="Depository")):
                txt.insert(END,"A stock broker connects the buyers and sellers of stocks,While a depository participant is described as an agent of the depository");
                break;
            if((name2=="Divident" and name=="Depository") or (name== "Divident" and name2=="Depository")):
                txt.insert(END,"Globally, distribution of dividends is by depositories")
                break;
            else:
                txt.insert(END,"This relationship is Not Defined Directly or may be some Alphabeticall Error");
                break;
            
    #Customer
    elif(name == 'Customer' or name2 == 'Customer' ):
        if(name=='Customer'):
            output = run(0, x, Root(name, x))
        else:
            output = run(0, x, Root(name2, x))
            
        ##print("\nList of " + name + "'s children:")
        for item in output:
            if((name2=="Stock Exchange" and name=="Customer") or (name=="Stock Exchange" and name2=="Customer")):
                txt.insert(END,"Stock exchange is a place where the trading is executed and from here Customer get the idea to buy any share or not")
                break;
            if((name2=="Seller" and name=="Customer") or (name=="Seller" and name2=="Customer")):
                txt.insert(END,"Seller who sells and Customer who are ready to buy the shares")
                break;
            if((name2=="Divident" and name=="Customer") or (name=="Divident" and name2=="Customer")):
                txt.insert(END,"After Earning From the shares as a profit we get a divident as we get a interest in Banks");
                break;
            if((name2=="DEMAT ACC." and name=="Customer") or (name== "DEMAT ACC." and name2=="Customer")):
                txt.insert(END,"Where Customer Can go through the detail of the personal invested shares through Demat Account")
                break;
            if((name2=="Broker" and name=="Customer") or (name== "Broker" and name2=="Customer")):
                txt.insert(END,"Who acts as a intermediate between Customer and Stock market and helps him to invest in shares")
                break;
            if((name2=="Registrar" and name=="Customer") or (name=="Registrar" and name2=="Customer")):
                txt.insert(END,"A registrar is a bank or a similar company that is responsible for recordkeeping of bondholders and shareholders. ");
                break;
            else:
                txt.insert(END,"This relationship is Not Defined Directly or may be some Alphabeticall Error");
                break;

    #Demat Acc.
    elif(name == "DEMAT ACC." or name2 == "DEMAT ACC." ):
        if(name=="DEMAT ACC."):
            output = run(0, x, Root(name, x))
        else:
            output = run(0, x, Root(name2, x))
            
        ##print("\nList of " + name + "'s children:")
        for item in output:
            if((name2=="Seller" and name=="DEMAT ACC.") or (name=="Seller" and name2=="DEMAT ACC.")):
                txt.insert(END,"Seller sells their share after it collect the remaining shares informtion from DEMAT Account")
                break;
            if((name2=="Divident" and name=="DEMAT ACC.") or (name=="Divident" and name2=="DEMAT ACC.")):
                txt.insert(END,"Divident is Generated only u have Demat acc. becoz it contain all your information")
                break;
            if((name2=="Broker" and name=="DEMAT ACC.") or (name=="Broker" and name2=="DEMAT ACC.")):
                txt.insert(END,"Broker Provide you the Demat Account Where u get the information of all Shares");
                break;
            if((name2=="Stock Exchange" and name=="DEMAT ACC.") or (name== "Stock Exchange" and name2=="DEMAT ACC.")):
                txt.insert(END,"After invested in Shares with the help of Stock exchange we are ready to update our Demat Account")
                break;
            else:
                txt.insert(END,"This relationship is Not Defined Directly or may be some Alphabeticall Error");
                break;

    #Clearing House
    elif(name == "Clearing House" or name2 == "Clearing House" ):
        if(name=="Clearing House"):
            output = run(0, x, Root(name, x))
        else:
            output = run(0, x, Root(name2, x))
            
        ##print("\nList of " + name + "'s children:")
        for item in output:
            if((name2=="Stock Exchange" and name=="Clearing House") or (name=="Stock Exchange" and name2=="Clearing House")):
                txt.insert(END,"A clearing house acts as an intermediary between a buyer and seller and seeks to ensure that the process from trade inception to settlement is smooth.")
                break;
            else:
                txt.insert(END,"This relationship is Not Defined Directly or may be some Alphabeticall Error");
                break
    #Divident
    elif(name == "Divident" or name2 == "Divident" ):
        if(name=="Divident"):
            output = run(0, x, Root(name, x))
        else:
            output = run(0, x, Root(name2, x))
            
        ##print("\nList of " + name + "'s children:")
        for item in output:
            if((name2=="Registrar" and name=="Divident") or (name=="Registrar" and name2=="Divident")):
                txt.insert(END,"The registrar determines which shareholders are paid a cash or stock dividend.")
                break;
            else:
                txt.insert(END,"This relationship is Not Defined Directly or may be some Alphabeticall Error");
                break
    else:
        txt.insert(END,"This relationship is Not Defined Directly or may be some Alphabeticall Error");
      

#.....................Function For Text................
def show_data():
    txt.delete(0.0,"end")
    t1=e1.get()
    t2=e2.get()
    sentence=str(t1)+str(t2)
    txt.insert(END,sentence)
#..........................................
    
root.title("Relationship Management System")
mainframe=Frame(root,width=1500,height=1700,bg="darkcyan")
mainframe.pack(side=TOP,fill=X)
head=Frame(mainframe,width=1600,height=10,bg="khaki",relief=SUNKEN)
head.pack(side=TOP)
New=Frame(mainframe,width=1500,height=200,bg="darkcyan")
New.pack(side=BOTTOM)

f1=Frame(mainframe,width=450,height=1300,bd=12,relief=SUNKEN)
f1.pack(side=LEFT,anchor='nw',pady=(80,30),padx=(10,5))

f2=Frame(mainframe,width=380,height=800,bd=12,relief=SUNKEN)
f2.pack(side=LEFT,padx=2,pady=(80,0))

f3=Frame(mainframe,width=500,height=800,bd=12,relief=SUNKEN)
f3.pack(side=LEFT,padx=(5,15),pady=(80,30))
     
head1=Label(head,font=('algerian',28,'bold'),text='Stock Exchange Relationship Model',fg='darkslategray')
head1.grid(row=0,column=0,pady=10)
#................................Last One..........................................
rand0=StringVar()

L0=Label(f3,font=('arial',16,'bold'),text="Relationship",bd=16)
L0.grid(row=0,column=0,padx=(0,10));

txt=Text(f3,font=('arial',18,'bold'),width=26,height=11,wrap=WORD)
txt.grid(row=2,column=0)
txt.insert(END,"While giving the Input From the Ist Box  Make Sure u have Checked Spelling Properly(It's a Case Sensitive)")

'''e1=Entry(f3,font=('arial',140,'bold'),textvariable=rand0,width=3,bd=10,insertwidth=0,bg="salmon",justify='right')
e1.grid(row=1,column=0,padx=(10,10),pady=(0,20))
e1=ScrolledText(f3,font=('arial',14,'bold'),width=28,height=18,bd=10,bg="salmon").grid(row=1,column=0,pady=(0,25))
e1=Entry(f3,font=('arial',100,'bold'),textvariable=rand0,width=3,bd=10,insertwidth=0,bg="salmon",justify='right')
e1.grid(row=1,column=0,padx=(10,10),pady=(0,20))'''

#................................MIddle One........................................
rand1=StringVar()
rand2=StringVar()

L1=Label(f2,font=('arial',16,'bold'),text="Enter 1st Factor",bd=16)
L1.grid(row=0,column=0,padx=(0,10));
e1=Entry(f2,font=('arial',36,'bold'),textvariable=rand1,width=15,bd=10,insertwidth=1,bg="salmon",justify='right')
e1.grid(row=1,column=0,padx=(10,10),pady=(0,10))
# how to add space in between them
L2=Label(f2,font=('arial',16,'bold'),text="Enter 2nd Factor",bd=16)
L2.grid(row=2,column=0,pady=(20,0));
e2=Entry(f2,font=('arial',36,'bold'),textvariable=rand2,width=15,bd=10,insertwidth=1,bg="salmon",justify='right')
e2.grid(row=3,column=0,padx=(10,10),pady=(0,10))
#......................First One......................................

l3=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='Entities Contributing In \nStock Exchange',fg='black')
l3.grid(columnspan=4,pady=(10,10))

l4=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='1. Registrar',fg='black')
l4.grid(row=1,column=0,padx=(0,10))

l5=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='2. Depository',fg='black')
l5.grid(row=1,column=1,padx=(0,60))

l6=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='3. Customer',fg='black')
l6.grid(row=2,column=0)

l7=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='4. DEMAT ACC.',fg='black')
l7.grid(row=2,column=1,padx=(0,40))

l8=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='5. Broker',fg='black')
l8.grid(row=3,column=0,padx=(0,40))

l9=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='6. Stock Exchange',fg='black')
l9.grid(row=3,column=1)

l10=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='7. Seller',fg='black')
l10.grid(row=4,column=0,padx=(0,50))

l11=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='8.Clearing House',fg='black')
l11.grid(row=4,column=1,padx=(0,20))

l12=Label(f1,font=('comicsansms',20,'bold'),bd=12,text='9. Divident',fg='black')
l12.grid(row=5,column=0,pady=(0,10))
#..................................Button.............................................

b1=Button(New,fg='black',font=('arial',17,'bold'),width=10,text="CLEAR",bg="goldenrod",command=reset)#,
b1.grid(row=0,column=3,padx=3,pady=(30,20))

b2=Button(New,fg='black',font=('arial',17,'bold'),width=20,text="Show Relationship",bg="goldenrod",command=cal_relation)#,command=graph1 
b2.grid(row=0,column=4,padx=3,pady=(30,20))

b3=Button(New,fg='black',font=('arial',17,'bold'),width=18,text="Show Image",bg="goldenrod")#,command=graph2
b3.grid(row=0,column=5,padx=3,pady=(30,20))

b4=Button(New,fg='black',font=('arial',17,'bold'),width=10,text="EXIT",bg="goldenrod",command=destroy)#
b4.grid(row=0,column=6,padx=3,pady=(30,20))


root.mainloop()
