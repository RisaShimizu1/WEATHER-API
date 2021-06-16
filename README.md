# WEATHER-API
# App to Get Temperature Data from "Open Weather Map" Service
import pyowm

#Define global variable to store OWM weather-query object
owm = pyowm.OWM('cf0c12dead95afcd1097473802bdadaa')
wman = owm.weather_manager()

#Function that gets weather info from API - DO NOT EDIT
#  Returns results in dictionary with
#  keys 'temp', 'temp_max', 'temp_min'
#  and values that are floats4
#  DO NOT EDIT THIS FUNCTION
def getWeather(city, country):
    location = city+','+country
    observation = wman.weather_at_place(location).weather
    return observation.temperature('fahrenheit')

def main():
    flag = True
    while(True):
        if (flag==False):
            break

        print("Check temperature in cities worldwide")

        city = input("City:")

        country = input("Country: ")

        wt = getWeather(city, country)

        tmax = wt['temp_max']
        temp = wt['temp']
        tmin = wt['temp_min']

        cel1 = (tmax - 32) / 1.8
        cel2 = (temp - 32) / 1.8
        cel3 = (tmin - 32) / 1.8

        print("Max temperature:", tmax, "F", cel1, "C")
        print("Current temperature:", temp, "F", cel2, "C")
        print("Minimum temperature:", tmin, "F", cel3, "C")

        while(True):
            user_answer = input("Check the weather in another city?(Y or N):")

            if(user_answer == 'Y'):
                break

            elif(user_answer == 'N'):
                flag = False
                break
main()
