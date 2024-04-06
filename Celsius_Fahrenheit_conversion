#Create a Python program for temperature conversion between Celsius and Fahrenheit scales. 
#The program should prompt users to select the direction of conversion, accept input for the temperature value, 
#and accurately perform the conversion (use IF and/or ELSE). 
#Output should be displayed with formatted strings showing both the original and converted temperatures.

try:
  print("Temperature Conversion Program")
  print("1. Celsius to Fahrenheit")
  print("2. Fahrenheit to Celsius")
  choice = int(input("Enter your choice (1 or 2): "))
  if choice == 1:
    celsius = float(input("Enter the temperature in Celsius: "))
    fahrenheit = (celsius * 9/5) + 32
    print(f"{celsius} degrees Celsius is equal to {fahrenheit:.2f} degrees Fahrenheit.")
  elif choice == 2:
    fahrenheit = float(input("Enter the temperature in Fahrenheit: "))
    celsius = (fahrenheit - 32) * 5/9
    print(f"{fahrenheit} degrees Fahrenheit is equal to {celsius:.2f} degrees Celsius.")
  else:
    print("Invalid choice. Please enter 1 or 2.")
except Exception as m:
  print(f'Wrong input, exseption: {m}')
