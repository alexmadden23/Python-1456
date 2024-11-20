def get_recommendation(day, temperature, condition):
    recommendation = f"Recommendations for {day}:\n"
    if temperature > 25:
        recommendation += "- It's warm, consider wearing light clothing.\n"
    elif temperature < 15:
        recommendation += "- It's cold, consider wearing a jacket.\n"
    else:
        recommendation += "- Mild weather, dress comfortably.\n"

    if condition.lower() == "sunny":
        recommendation += "- It's sunny, wear sunglasses and enjoy outdoor activities.\n"
    elif condition.lower() == "rainy":
        recommendation += "- It's rainy, consider staying indoors or carrying an umbrella.\n"
    elif condition.lower() == "cloudy":
        recommendation += "- It's cloudy, a neutral day for activities.\n"
    else:
        recommendation += "- Unknown weather condition, plan accordingly.\n"

    return recommendation


def weather_planner():
    recommendations = []
    total_temperature = 0
    days_count = 0

    while True:
        day = input("Enter the day of the week: ")
        temperature = float(input("Enter the temperature (°C): "))
        condition = input("Enter the weather condition (Sunny, Rainy, Cloudy): ")
        recommendation = get_recommendation(day, temperature, condition)
        print(recommendation)
        recommendations.append(recommendation)
        total_temperature += temperature
        days_count += 1

        more_days = input("Do you want to input weather for another day? (yes/no): ").strip().lower()
        if more_days != 'yes':
            break

    if days_count > 0:
        average_temp = total_temperature / days_count
        print("\n--- Summary ---")
        print(f"Average Temperature: {average_temp:.2f}°C")
        print("Recommendations Summary:")
        for rec in recommendations:
            print(rec)


weather_planner()

