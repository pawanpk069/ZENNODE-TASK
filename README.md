# ZENNODE-TASK - 1:
# Completion of Zennode task.
class ShoppingCart:
    def __init__(self):
        self.products = {"Product A": {"price": 20, "quantity": 0},
                         "Product B": {"price": 40, "quantity": 0},
                         "Product C": {"price": 50, "quantity": 0}}

    def ask_quantity_and_gift_wrap(self, product_name):
        quantity = int(input(f"Enter the quantity of {product_name}: "))
        gift_wrap = input(f"Is {product_name} wrapped as a gift? (yes/no): ").lower() == "yes"
        return quantity, gift_wrap

    def calculate_total_price(self):
        return sum(item["price"] * item["quantity"] for item in self.products.values())

    def apply_discount_rules(self):
        total_quantity = sum(item["quantity"] for item in self.products.values())
        max_quantity_per_product = max((item["quantity"] for item in self.products.values()), default=0)

        # Apply the most beneficial discount rule
        if total_quantity > 30 and max_quantity_per_product > 15:
            return "tiered_50_discount", self.calculate_total_price() * 0.5
        elif total_quantity > 20:
            return "bulk_10_discount", self.calculate_total_price() * 0.1
        elif any(item["quantity"] > 10 for item in self.products.values()):
            return "bulk_5_discount", sum(item["price"] * item["quantity"] * 0.05 for item in self.products.values())
        elif self.calculate_total_price() > 200:
            return "flat_10_discount", 10
        else:
            return None, 0

    def apply_fees(self):
        gift_wrap_fee = sum(item["quantity"] for item in self.products.values())
        shipping_fee = (sum(item["quantity"] for item in self.products.values()) // 10) * 5
        return gift_wrap_fee, shipping_fee

    def display_cart(self):
        print("\nShopping Cart:")
        for product_name, item in self.products.items():
            print(f"{product_name}: Quantity: {item['quantity']}, Total Amount: ${item['price'] * item['quantity']}")
        print("\nSubtotal:", self.calculate_total_price())

        discount_name, discount_amount = self.apply_discount_rules()
        if discount_name:
            print(f"Discount Applied - {discount_name}: ${discount_amount}")

        gift_wrap_fee, shipping_fee = self.apply_fees()
        print(f"Gift Wrap Fee: ${gift_wrap_fee}, Shipping Fee: ${shipping_fee}")

        total_amount = self.calculate_total_price() - discount_amount + gift_wrap_fee + shipping_fee
        print("\nTotal:", total_amount)


# Main program
cart = ShoppingCart()

for product_name in cart.products.keys():
    quantity, gift_wrap = cart.ask_quantity_and_gift_wrap(product_name)
    cart.products[product_name]["quantity"] = quantity
    if gift_wrap:
        cart.products[product_name]["price"] += quantity  # Gift wrap fee: $1 per unit

cart.display_cart()


# ZENNODE-TASK - 2:

# Why do you like to join as a Software developer?
# ANS: since childhood i like computers playing games on it. It always made me curious how they are made and that is the reason i want to become software developer.

# List top 3 softwares / tools that inspire you. Why do these tools inspire you?
# ANS: 1. mySQL: SQL is fundamental for interacting with relational databases. Its syntax allows for efficient querying, updating, and managing of database #records, making it an essential tool for anyone working with structured data.
     # 2. JAVASCRIPT: we can as interactive langugae it is easy to learn and very compatible.
     # 3. JAVA: java is versatile and object oriented langugae. it xcan be use to develop wide range of applications.
# List top 3 organisations you like to join in your career & why you like these organisations.
# ANS: 1. Google: Because of the innovative culture and new skills i can learn from there.
     # 2. KPIT Technologies: I like automotive industires and they are really innovative these dates.
     # 3. Tesla: Tesla is led by Elon Musk. he's innovative ideas inspires me. he is my inspiration. Maybe that is the reason i like to work there.

# How you position yourself in this industry after 2 years.
# ANS: I see myself as a highly skilled professional in tech industry. My primary focus will be continuous skill development.

# List 3 projects / products you have built or have planned to build in the upcoming year, also explain your role in the same.
# Ans: I have developed small projects such as Realtime Chat Application, Amazon Website clone and by using SQL analytics Zomato Application


