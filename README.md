# Hotelbooking
class HotelBooking:
    def __init__(self, name, check_in_date, total_days, total_persons):
        self.name = name
        self.check_in_date = check_in_date
        self.total_days = total_days
        self.total_persons = total_persons
        self.room_type = ""
        self.amenities = []
        self.advance_amount = 0

    def capture_customer_info(self):
        self.name = input("Enter customer name: ")
        self.check_in_date = input("Enter check-in date (YYYY-MM-DD): ")
        self.total_days = int(input("Enter total days: "))
        self.total_persons = int(input("Enter total persons: "))

    def select_room_info(self):
        self.room_type = input("Select room type (Delux or Suite): ")
        amenities_input = input("Select amenities (AC, Locker) separated by comma: ")
        self.amenities = amenities_input.split(", ")

    def set_room_rates(self, deluxe_room_rate, suite_room_rate, ac_rate, locker_rate):
        self.deluxe_room_rate = deluxe_room_rate
        self.suite_room_rate = suite_room_rate
        self.ac_rate = ac_rate
        self.locker_rate = locker_rate

    def calculate_total_cost(self):
        room_cost = 0
        if self.room_type.lower() == "delux":
            room_cost += self.deluxe_room_rate
        elif self.room_type.lower() == "suite":
            room_cost += self.suite_room_rate

        amenities_cost = 0
        for amenity in self.amenities:
            if amenity.lower() == "ac":
                amenities_cost += self.ac_rate
            elif amenity.lower() == "locker":
                amenities_cost += self.locker_rate

        total_cost = (room_cost + amenities_cost) * self.total_days
        return total_cost

    def collect_advance_payment(self):
        self.advance_amount = float(input("Enter advance payment amount: "))

    def calculate_balance(self, total_cost):
        balance = total_cost - self.advance_amount
        return balance

    def display_booking_info(self, total_cost, balance):
        print("\nBooking Details:")
        print("Customer Name:", self.name)
        print("Check-in Date:", self.check_in_date)
        print("Total Days:", self.total_days)
        print("Total Persons:", self.total_persons)
        print("Room Type:", self.room_type)
        print("Amenities:", ", ".join(self.amenities))
        print("Total Cost:", total_cost)
        print("Advance Amount:", self.advance_amount)
        print("Balance:", balance)


if __name__ == "__main__":
    booking = HotelBooking("", "", 0, 0)
    booking.capture_customer_info()
    booking.select_room_info()
    booking.set_room_rates(100, 200, 50, 20)
    total_cost = booking.calculate_total_cost()
    booking.collect_advance_payment()
    balance = booking.calculate_balance(total_cost)
    booking.display_booking_info(total_cost, balance)
    
