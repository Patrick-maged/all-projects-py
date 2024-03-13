class Flight:
    def __init__(self,origin:str,destination:str,departure_time:int,arrival_time:int):
        self.FlightNo=[]
        self.Origin=origin
        self.destination=destination
        self.departure_time=departure_time
        self.arrival_time=arrival_time

    def Flight_no(self,Number):
        if Number not in self.FlightNo :
            self.FlightNo.append(Number)
        else:
            Number=int(input("enter another Number:"))
            if Number not in self.FlightNo:
                self.FlightNo.append(Number)

        return self.FlightNo
class Passenger:
    def __init__(self,id,name,seat_no):
        self.id = id
        self.name = name
        self.seat_no = seat_no
    def __str__(self):
        return f"ID:{self.id},Name:{self.name},seat_no{self.seat_no}"


class PassengersFlights(Flight):
    def __init__(self,origin:str,destination:str,departure_time:int,arrival_time:int,capacity,passengers):
        super().__init__(origin,destination,departure_time,arrival_time)
        self.capacity=capacity
        self.passengers=[passengers]

    def book_seat(self,id,name,seat_no):
        if len(self.passengers) < self.capacity:
            passenger=Passenger(id,name,seat_no)
            self.passengers.append(passenger)
        else:
            print('no available places')
        return self.passengers

class Cargo:
    def __init__(self,id:int,description:str,weight:int):
        self.id=id
        self.description=description
        self.weight=weight
    def __str__(self):
        return f'The cargo id{self.id},the discription{self.description},the weight{self.weight}'

class Cargo_flight(Flight):
    def __init__(self, origin: str, destination: str, departure_time: int, arrival_time: int, maxweight,weight):
        super().__init__(origin, destination, departure_time, arrival_time)
        self.Max_Weight=maxweight
        self.weight=weight
        self.cargo_weight=[]
    def add_cargo(self,id:int,description:str,weight:int):
        if self.Max_Weight > self.weight :
            cargo=Cargo(id,description,weight)
            self.cargo_weight.append(cargo)
            self.Max_Weight-=self.weight
        else:
            print('the weight above Maximum weight')

class Private_jet:
    def __init__(self,id,owner,Max_Nunber):
        self.id=id
        self.owner=owner
        self.Max_number=Max_Nunber

    def __str__(self):
        return f'id owner{self.id},owner name{self.owner},Maximum passengers{self.Max_number}'

class Private_jet_flight(Flight):
    def __init__(self,origin:str,destination:str,departure_time:int,arrival_time:int,Max_Passenger):
        super().__init__(origin,destination,departure_time,arrival_time)
        self.Max_passenger=Max_Passenger
        self.passengers=[]

    def book_flight(self,Passenger_NO,id,owner,Max_Nunber):
        if self.Max_passenger > Passenger_NO :
            private=Private_jet(id,owner,Max_Nunber)
            self.passengers.append(private)

class Manage_System_flight(Flight):
    def __init__(self):
        self.flight=[]

    def add_flight(self,flight):
        self.flight.append(flight)

    def search_flight(self,flight_no,index):
        if index >= len(self.flight):
            return None
        if self.flight[index].FlightNo==flight_no:
            return flight_no
