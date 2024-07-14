class node:
    def __init__(self):
        self.data=None
        self.next=None
        self.prev=None
class ddl:
    def __init__(self):
        self.head=None
        self.tail=None
    def insert(self,x):
        a=node()
        a.data=x
        if self.head==None:
            self.head=a
            self.tail=a
        else:
            a.prev=self.tail
            self.tail.next=a
            self.tail=a
    def infirst(self,x):
        a=node()
        a.data=x
        if self.head==None:
            self.head=a
            self.tail=a
        else:
            self.head.prev=a
            a.next=self.head
            self.head=a
    def length(self):
        if self.head==None:
            return 0
        else:
            t=self.head
            c=0
            while t!=None:
                c+=1
                t=t.next
            return c
    def inpos(self,x,pos):
        l1=self.length()
        if pos>l1:
            print("invalid")
        else:
            a=node()
            a.data=x
            i=1
            n1=self.head
            n2=self.head
            while i<pos:
                n1=n2
                n2=n2.next
                i+=1
            n2.prev=a
            a.next=n2
            a.prev=n1
            n1.next=a
    def dellast(self):
        if self.head==None:
            print("No elements")
        elif self.head==self.tail:
            self.head=None
            self.tail=None
        else:
            n=self.tail.prev
            self.tail.prev=None
            n.next=None
            self.tail=n
    def delfirst(self):
        if self.head==None:
            print("No elements")
        elif self.head==self.tail:
            self.head=None
            self.tail=None
        else:
            n=self.head.next
            self.head.next=None
            n.prev=None
            self.head=n
    def delinpos(self,pos):
        l2=self.length()
        if pos>l2:
            print("invalid")
        else:
            n1=self.head
            n2=self.head
            i=1
            while i<pos:
                n1=n2
                n2=n2.next
                i+=1
            n=n2.next
            n2.prev=None
            n1.next=n   
            n2.next=None
            n2.prev=n          
    def display(self):
        t=self.head
        while t!=None:
            print(t.data)
            t=t.next
d=ddl()
while(True):
    print("Enter your choice")
    print("1.Insert at last")
    print("2.Insert at first")
    print("3.Insert at position")
    print("4.delete in first")
    print("5.delete in last")
    print("6.delete in position position")
    print("7.Display")
    print("8.Exit")
    ch=int(input(""))
    if(ch==1):
        x=int(input("Enter to insert at last"))
        d.insert(x)
        print("Value inserted at last")
    elif(ch==2):
        x=int(input("Enter to insert at first"))
        d.infirst(x)
        print("Value inserted at first")
    elif(ch==3):
        pos=int(input("Enter the position"))
        d.inpos(x,pos)
    elif(ch==4):
        d.delfirst()
    elif(ch==5):
        d.dellast()
    elif(ch==6):
        pos=int(input("Enter the position"))
        d.delinpos(pos)
    elif(ch==7):
        d.display()
    elif(ch==8):
        print("exit")
        break
    else:
        print("Invalid Choice")
