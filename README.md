# python-taco-order-system
A Python-based taco ordering system using menus, dictionaries, functions, loops, and cart management.
print("Want some tacos? \nLets Taco'bout it!")
tab = []

def menu():
    print("\n==== FOOD MENU ====")
    print("1. Add Food to Cart")
    print("2. View Cart")
    print("3. Checkout")
    print("4. Exit")
    print("5. Remove Item from Cart")
    choice = int(input("Choose an option: "))
    return choice

def show_food_items():
    food_items = {
        1: ("Tacos de Fajita ", 2.25),
        2: ("Tacos de Lengua ", 2.25),
        3: ("Tacos de Barbacoa ", 2.75),
        4: ("Agua de Horchata", 1.99),
        5: ("Agua de Jamaica", 1.99)
    }

    print("\nAvailable Food Items:")
    for key, value in food_items.items():
        print(str(key) + ". " + value[0] + " - $" + format(value[1], ".2f"))

    return food_items

def add_to_tab():
    food_items = show_food_items()
    choice = int(input("Enter the number of the food item to add to cart: "))
    if choice in food_items:
        tab.append(food_items[choice])
        print(food_items[choice][0] + " added to cart!")
    else:
        print("Invalid choice.")

def view_tab():
    if not tab:
        print("\nYour tab is empty.")
    else:
        print("\nItems in your tab:")
        total = 0
        for index, item in enumerate(tab):
            print(str(index + 1) + ". " + item[0] + " - $" + format(item[1], ".2f"))
            total += item[1]
        print("Total: $" + format(total, ".2f"))

def remove_from_tab():
    if not tab:
        print("\nYour tab is empty. Nothing to remove.")
        return

    print("\nRemove Item from Cart:")
    for index, item in enumerate(tab):
        print(str(index + 1) + ". " + item[0] + " - $" + format(item[1], ".2f"))

    try:
        choice = int(input("Enter the number of the item to remove: "))
        if 1 <= choice <= len(tab):
            removed_item = tab.pop(choice - 1)
            print(removed_item[0] + " removed from cart.")
        else:
            print("Invalid selection.")
    except ValueError:
        print("Please enter a valid number.")

def checkout():
    if not tab:
        print("\nYou haven't ordered anything... Add items before checking out.")
    else:
        print("\nCheckout Summary:")
        view_tab()
        print("Que tengas buen día!")

def main():
    while True:
        choice = menu()
        if choice == 1:
            add_to_tab()
        elif choice == 2:
            view_tab()
        elif choice == 3:
            checkout()
            break
        elif choice == 4:
            print("We taco'd enough today \nQue tengas buen día!")
            break
        elif choice == 5:
            remove_from_tab()
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
