MENU = {
    "Coffee": {
        1: ("Espresso", 19000),
        2: ("Latte", 20000),
        3: ("Cappuccino", 22000)
    },
    "Tea": {
        4: ("Matcha Latte", 15000),
        5: ("Earl Grey", 15000),
        6: ("Lemon Tea", 15000)
    },
    "Smoothies": {
        7: ("Banana", 25000),
        8: ("Berries", 26000),
        9: ("Pineapple", 25000)
    }
}

print("˚༺☆༻*ੈ✩‧₊˚WELCOME TO OUR COFFEE SHOP☆༻*ੈ✩‧₊˚")
for VARIANT, MAIN_MENU in MENU.items():
    print(f"\n⋆.𐙚 ̊₊˚ ⋅ {VARIANT.upper()} ⋆.𐙚 ̊₊˚ ⋅")
    
    for no, detail in MAIN_MENU.items():
        print(f"{no}. {detail[0]:<15} | Rp {detail[1]:,}")
total = 0
orders = []

while True:
    try:
        choice = int(input("\n𐔌՞. .՞𐦯 What would you like to order? Choose number : "))
        
        found = False
        for VARIANT, MAIN_MENU in MENU.items():
            if choice in MAIN_MENU:
                name, price = MAIN_MENU[choice]
                found = True
                break
        
        if not found:
            print("𐔌՞. .՞𐦯 Sorry my dear, I think you wrong!")
            continue

        quantity = int(input(f"𐔌՞. .՞𐦯 How many {name} would you like? : "))
        if quantity <= 0:
            print("𐔌՞. .՞𐦯 You must at least buy 1, my dear")
            continue

        subtotal = price * quantity
        orders.append((name, price, quantity, subtotal))
        total += subtotal
        
        print(f"𐔌՞. .՞𐦯 Added: {name} x{quantity}")

    except ValueError:
        print("𐔌՞. .՞𐦯 Please enter other number, my dear!")
        continue

    again = input("𐔌՞. .՞𐦯 More order? (y = yes / n = no / c = cancel): ").lower()
        
    if again == 'y':
        continue
    elif again == 'n':
        break 
    elif again == 'c':
        print("\n𐔌՞. .՞𐦯 Order cancelled. Clearing your basket...")
        orders = [] 
        total = 0
        break
    else:
        print("𐔌՞. .՞𐦯 Error! Please type 'y', 'n', or 'c'.")

    if again == 'c':
        print("𐔌՞. .՞𐦯 Thank you. See you next time!")
        exit() 
    elif again == 'n':
        break

discount = total* 0.1 if total > 100000 else 0
final_price = total - discount

print(" ")
print(" ")
print("\n" + "="*35)
print(f"{'FINAL RECEIPT':^35}")
print("="*35)
for item in orders:
    print(f"{item[0]:<15} x{item[2]:<1} = Rp {item[3]:>10,}")

print("-" * 35)
print(f"{'Total Gross':<18} : Rp {total:>10,}")
print(f"{'Discount (10%)':<18} : Rp {int(discount):>10,}")
print(f"{'Total Pay':<18} : Rp {int(final_price):>10,}")
print("="*35)
print(" "*2 ,"Thank you for your order Dear!")
print(" "*10,"Enjoy ur time!")
print(" "*13, "𐔌՞. .՞𐦯")
