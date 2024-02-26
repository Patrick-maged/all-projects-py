

class pizza:


    def __init__(self):
        self.size=''
        self.no_cheese=0
        self.no_pepro=0
        self.cost=0

    def Calc_cost(self,size,no_cheese,no_pepro):
        if self.size== 's' or self.size=="small":
            self.cost= 70
        elif self.size == "m" or self.size=="medium":
            self.cost=120
        elif self.size == "l" or self.size=="large":
            self.cost=160
        if self.no_pepro > 0:
            for i in range(self.no_pepro):
                self.cost+=15
        if self.no_cheese > 0:
            for i in range(self.no_cheese):
                self.cost+=15
        return self.cost
pizza1=pizza()
pizza1.size=input("Enter size (small, medium, large):")
while pizza1.size !='s' and pizza1.size !="small" and pizza1.size !='m' and pizza1.size !="medium" and pizza1.size !='l' and pizza1.size !="large":
    print("wrong size")
    pizza1.size = input("Enter size (small, medium, large):")
pizza1.no_cheese=int(input("enter number of cheese topings: "))
while pizza1.no_cheese < 0 :
    print("wrong number")
    pizza1.no_cheese=int(input("enter number of cheese topings: "))
pizza1.no_pepro=int(input("enter number of bebroni topings: "))
while pizza1.no_pepro < 0 :
    print("wrong number")
    pizza1.no_pepro=int(input("enter number of bebroni topings: "))
print(pizza1.Calc_cost(pizza1.size,pizza1.no_cheese,pizza1.no_pepro))
