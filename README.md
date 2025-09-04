# eco-calculator

Creating a complete Python program for an "eco-calculator" can be a complex task, depending on the functionalities you want to incorporate. Below is a simplified version that can serve as a starting point. This program will allow users to input their daily activities and calculate the approximate carbon footprint based on some common factors like electricity usage, travel, and waste production. 

```python
import sys

class EcoCalculator:
    def __init__(self):
        # Constants for CO2 emissions in kg CO2 per unit
        # These values are illustrative examples, not accurate measurements
        self.electricity_per_kwh = 0.233  # Kg CO2 per kWh
        self.gasoline_per_liter = 2.31    # Kg CO2 per liter
        self.waste_per_kg = 1.44          # Kg CO2 per kg of waste

    def calculate_electricity_footprint(self, kwh):
        """Calculate the CO2 footprint for electricity usage."""
        try:
            return kwh * self.electricity_per_kwh
        except Exception as e:
            print(f"Error calculating electricity footprint: {e}")
            return 0

    def calculate_travel_footprint(self, liters):
        """Calculate the CO2 footprint based on gasoline consumption."""
        try:
            return liters * self.gasoline_per_liter
        except Exception as e:
            print(f"Error calculating travel footprint: {e}")
            return 0

    def calculate_waste_footprint(self, kg):
        """Calculate the CO2 footprint for waste production."""
        try:
            return kg * self.waste_per_kg
        except Exception as e:
            print(f"Error calculating waste footprint: {e}")
            return 0

    def calculate_total_footprint(self, kwh, liters, waste_kg):
        """Calculate total carbon footprint from all activities."""
        try:
            total_footprint = (
                self.calculate_electricity_footprint(kwh) +
                self.calculate_travel_footprint(liters) +
                self.calculate_waste_footprint(waste_kg)
            )
            return total_footprint
        except Exception as e:
            print(f"Error calculating total footprint: {e}")
            return 0

def get_float_input(prompt):
    """Utility function to safely get a float input from the user."""
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Invalid input. Please enter a numeric value.")

def main():
    print("Welcome to the Eco-Calculator!")
    calculator = EcoCalculator()

    # Get user inputs
    kwh = get_float_input("Enter the amount of electricity used in kWh: ")
    liters = get_float_input("Enter the amount of gasoline used in liters: ")
    waste_kg = get_float_input("Enter the amount of waste produced in kg: ")

    # Calculate the total carbon footprint
    total_footprint = calculator.calculate_total_footprint(kwh, liters, waste_kg)

    print(f"\nEstimated carbon footprint for your activities:")
    print(f"Electricity usage: {calculator.calculate_electricity_footprint(kwh):.2f} kg CO2")
    print(f"Travel: {calculator.calculate_travel_footprint(liters):.2f} kg CO2")
    print(f"Waste production: {calculator.calculate_waste_footprint(waste_kg):.2f} kg CO2")
    print(f"Total footprint: {total_footprint:.2f} kg CO2")

if __name__ == "__main__":
    try:
        main()
    except Exception as e:
        print(f"An unexpected error occurred: {e}")
        sys.exit(1)
```

### Key Features of the Program:
- **Structure with Classes**: The program uses a class `EcoCalculator` to encapsulate the calculation logic.
- **Error Handling**: Various `try-except` blocks handle possible errors such as invalid input and calculation errors.
- **User Inputs**: The program prompts the user for inputs related to activity data and validates them.
- **Flexibility**: The structure can be easily expanded to include more categories or more complex calculations.
- **Command-line Execution**: Ready to be used as a script with standard input/output.

This program provides a framework that can be expanded upon with additional features such as data storage, enhanced accuracy with real-world emission data, or a graphical user interface.