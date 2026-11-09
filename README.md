print("Welcome to CATUC Super Market")

sum_items = int(input("\nEnter number of items bought: "))
items_SN = []
items_name = []
items_quantity = []
items_cost = []

for item in range(1, sum_items + 1):
    SN = int(input(f"\nEnter Serial Number of item {item}: "))
    items_SN.append(SN)
    name = input(f"\nEnter item name {item}: ")
    items_name.append(name)
    quantity = int(input(f"\nEnter quantity of item {item}: "))
    items_quantity.append(quantity)
    cost = float(input(f"\nInput the cost of item {item}: "))
    items_cost.append(cost)

print("\n--- RECEIPT ---")
print(f"{'S/N':<5}{'Description':<15}{'Quantity':<10}{'Unit Price':<12}{'Total Price':<12}")

total_calculated_cost = 0
total_quantity = 0

for i in range(sum_items):
    item_total = items_quantity[i] * items_cost[i]
    total_calculated_cost += item_total
    total_quantity += items_quantity[i]
    print(f"{items_SN[i]:<5}{items_name[i]:<15}{items_quantity[i]:<10}{items_cost[i]:<12.2f}{item_total:<12.2f}")

# Find the discount rate from the conditions
discount_rate = 0

if total_calculated_cost > 5000:
    discount_rate = max(discount_rate, 0.10)

if total_quantity > 5 and total_calculated_cost > 4000:
    discount_rate = max(discount_rate, 0.15)

if total_calculated_cost >= 10000:
    discount_rate = max(discount_rate, 0.80)

if discount_rate > 0:
    discount = discount_rate * total_calculated_cost
    total_cost = total_calculated_cost - discount
    print(f"\nDiscount ({discount_rate * 100:.0f}%): {discount:.2f}")
    print(f"Total purchase: {total_cost:.2f}\nThanks for your patronage")
else:
    print(f"\nTotal purchase: {total_calculated_cost:.2f}\nThanks for your patronage")

