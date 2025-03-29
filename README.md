# Still-Travelling-AI-intern
import streamlit as st
import random

def gather_user_preferences():
    st.title("AI Travel Planner")
    st.write("Welcome! Let's plan your perfect trip.")

    starting_location = st.text_input("Enter your starting location:")
    destination = st.text_input("Enter your destination:")
    budget = st.selectbox("Select your budget range:", ["Budget", "Mid-Range", "Luxury"])
    duration = st.slider("How many days will your trip be?", 1, 14, 5)
    purpose = st.selectbox("Purpose of your trip:", ["Leisure", "Adventure", "Business", "Cultural", "Relaxation"])
    preferences = st.multiselect("Select your interests:", ["Nature", "Food", "Museums", "Shopping", "Beaches", "Nightlife", "History"])

    if st.button("Generate Itinerary"):
        itinerary = generate_itinerary(destination, budget, duration, purpose, preferences)
        display_itinerary(itinerary)

def generate_itinerary(destination, budget, duration, purpose, preferences):
    activities = {
        "Nature": ["National Park Visit", "Hiking Trail", "Boat Ride"],
        "Food": ["Local Cuisine Tour", "Fine Dining", "Street Food Market"],
        "Museums": ["Art Museum", "History Museum", "Science Center"],
        "Shopping": ["Local Market", "Shopping Mall", "Boutique Stores"],
        "Beaches": ["Beach Relaxation", "Water Sports", "Sunset Viewing"],
        "Nightlife": ["Bar Hopping", "Live Music", "Night Club"],
        "History": ["City Tour", "Historical Monument", "Cultural Show"]
    }

    itinerary = []
    for day in range(1, duration+1):
        day_plan = []
        for pref in preferences:
            if pref in activities:
                day_plan.append(random.choice(activities[pref]))
        if not day_plan:
            day_plan.append("Explore local surroundings")
        itinerary.append(f"Day {day}: {', '.join(day_plan)}")
    return itinerary

def display_itinerary(itinerary):
    st.subheader("Your Personalized Itinerary")
    for day_plan in itinerary:
        st.write(day_plan)

def main():
    gather_user_preferences()

if __name__ == "__main__":
    main()

    ![image](https://github.com/user-attachments/assets/c92e856d-0b8b-445d-9c16-e95bc758484d)

