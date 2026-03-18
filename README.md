# Personal-budget-Tracker
# Personal Budget Tracker Program
# This program allows the user to enter expenses, categorize them,
# and view a summary of total spending and category totals.

# Create an empty list to store all expense entries
expenses = []

print("Welcome to the Personal Budget Tracker!")
print("Enter 'done' at any time to finish entering expenses.\n")

# Collect expenses from the user
while True:
    name = input("Enter the expense name (or type 'done'): ")
    if name.lower() == "done":
        break

    # Ask for cost and convert to float
    cost_input = input("Enter the cost of the expense: ")
    cost = float(cost_input)

    # Ask for category
    category = input("Enter the category (Food, Transportation, etc.): ")

    # Store the expense as a dictionary
    expense = {"name": name, "cost": cost, "category": category}
    expenses.append(expense)

# Calculate totals
total_spending = 0
category_totals = {}

# Loop through each expense to calculate totals
for expense in expenses:
    total_spending += expense["cost"]

    # Update category totals
    if expense["category"] not in category_totals:
        category_totals[expense["category"]] = expense["cost"]
    else:
        category_totals[expense["category"]] += expense["cost"]

# Display results
print("\n----- Spending Summary -----")
print("Total Spending: $", total_spending)

print("\nCategory Totals:")
for category, amount in category_totals.items():
    print(category + ": $", amount)
