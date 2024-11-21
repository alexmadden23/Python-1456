def get_recommendation(day, temperature, condition):
    recommendation = f"Recommendations for {day}:\n"
    
    if temperature > 77: 
        recommendation += "- It's warm, consider wearing light, breathable clothing. Stay hydrated!\n"
    elif temperature < 59: 
        recommendation += "- It's cold, wear layers or a warm jacket. Consider gloves and a scarf if it's windy.\n"
    else:
        recommendation += "- Mild weather, dress comfortably with layers you can adjust.\n"
    
    condition_lower = condition.lower()
    if condition_lower == "sunny":
        recommendation += "- It's sunny, wear sunglasses and sunscreen. Great day for outdoor activities!\n"
    elif condition_lower == "rainy":
        recommendation += "- It's rainy, carry an umbrella or raincoat. Watch out for slippery roads.\n"
    elif condition_lower == "cloudy":
        recommendation += "- It's cloudy, a good day for relaxed indoor or outdoor activities.\n"
    elif condition_lower == "snowy":
        recommendation += "- It's snowy, wear insulated clothing and boots. Be cautious on the roads.\n"
    else:
        recommendation += "- Weather condition is unclear, plan your activities with flexibility.\n"
    
    return recommendation


def weather_planner():
    recommendations = []
    total_temperature = 0
    days_count = 0

    while True:
        day = input("Enter the day of the week: ")
        temperature = float(input("Enter the temperature (°F): "))
        condition = input("Enter the weather condition (Sunny, Rainy, Cloudy, Snowy): ")

        recommendation = get_recommendation(day, temperature, condition)
        print("\n" + recommendation)
        recommendations.append(recommendation)

        total_temperature += temperature
        days_count += 1

        more_days = input("Do you want to input weather for another day? (yes/no): ").strip().lower()
        if more_days != 'yes':
            break

    if days_count > 0:
        average_temp = total_temperature / days_count
        print("\n--- Weekly Weather Summary ---")
        print(f"Average Temperature: {average_temp:.2f}°F")
        print("\nDetailed Recommendations:")
        for rec in recommendations:
            print(rec)


weather_planner()
