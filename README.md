# SRE-LAB-BOTH-ASSIGNMENTS-

____________________PYTHON CODE ________________
class Customer:
    customer_counter = 1
    def __init__(self, name, email):
        self.customerID = Customer.customer_counter
        Customer.customer_counter += 1
        self.name = name
        self.email = email
        self.orders = []

    def register(self):
        print(f"{self.name} registered with ID {self.customerID}")

    def login(self):
        print(f"{self.name} logged in successfully")

    def placeOrder(self, order):
        self.orders.append(order)
        print(f"Order {order.orderID} placed by {self.name}")

class Order:
    order_counter = 1
    def __init__(self, customerID, items):
        self.orderID = Order.order_counter
        Order.order_counter += 1
        self.customerID = customerID
        self.items = items
        self.status = "Pending"

    def updateStatus(self, status):
        self.status = status
        print(f"Order {self.orderID} status updated to {self.status}")

    def calculateTotal(self):
        total = sum(item.price for item in self.items)
        print(f"Total for Order {self.orderID} is ${total}")
        return total

class Restaurant:
    restaurant_counter = 1
    def __init__(self, name):
        self.restaurantID = Restaurant.restaurant_counter
        Restaurant.restaurant_counter += 1
        self.name = name
        self.menuList = []

    def addMenuItem(self, menu):
        self.menuList.append(menu)
        print(f"{menu.name} added to {self.name}'s menu")

    def processOrder(self, order):
        order.updateStatus("Processing")
        print(f"{self.name} is processing Order {order.orderID}")

class Menu:
    item_counter = 1
    def __init__(self, name, price):
        self.itemID = Menu.item_counter
        Menu.item_counter += 1
        self.name = name
        self.price = price

    def updatePrice(self, price):
        self.price = price
        print(f"{self.name} price updated to ${self.price}")

    def removeItem(self):
        print(f"{self.name} removed from menu")

class Delivery:
    delivery_counter = 1
    def __init__(self, order):
        self.deliveryID = Delivery.delivery_counter
        Delivery.delivery_counter += 1
        self.orderID = order.orderID
        self.order = order
        self.status = "Not Assigned"

    def assignOrder(self):
        self.status = "Assigned"
        print(f"Delivery {self.deliveryID} assigned to Order {self.orderID}")

    def updateStatus(self, status):
        self.status = status
        self.order.updateStatus(status)
        print(f"Delivery {self.deliveryID} status updated to {self.status}")
