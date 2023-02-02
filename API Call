#import required modules
#import requests

class MyClass(GeneratedClass):
    def __init__(self):
        GeneratedClass.__init__(self)

    def onLoad(self):
        #put initialization code here
        pass

    def onUnload(self):
        #put clean-up code here
        pass

    def onInput_onStart(self):
        #self.onStopped() #activate the output of the box


        self.logger.fatal("API call activated")

        #import required modules
        #import json

        import json
        import os
        import sys
        import urllib
        import requests
        
        #insert path to folder here
        sys.path.append(os.path.join(self.behaviorAbsolutePath(), 'PATH'))

        #api_key to save API key
        api_key = "API KEY"

        #base_url variable to store URL
        base_url = "http://api.openweathermap.org/data/2.5/weather?"

        #get city name
        city_name = "CITY NAME"

        #complete_url variable to store
        #complete URL address
        complete_url = base_url + "appid=" + api_key + "&q=" + city_name

        #get methond of requests module
        #return responce object
        responce = requests.get(complete_url)

        #json method of responce object
        #convert json format data into python format data
        x = responce.json()

        #now x contains list of nested dictionaries
        #check the value of the "cod" key is equal to "404", means the city is found, otherwise city is not found

        if x["cod"] != "404" :
            #store the value of "main" key in variable y
            y = x["main"]
            self.logger.info(y)
            
            #store the temp value to the "temp" key of y
            currentTemperature = y["temp"]
            currentTemperature = currentTemperature - 273.15
            currentTemperature = round(currentTemperature)
            self.logger.info(currentTemperature)
            
            #store the pressure value to the "pressure" key of y
            currentPressure = y["pressure"]
            self.logger.info(currentPressure)
            
            #store the humididy value to the "humidity" key of y
            currentHumidity = y["humidity"]
            self.logger.info(currentHumidity)
            
            #store the weather value to the "weather" key of z
            z = x["weather"]
            #store the weather description value to the "description" key at the 0th index of z
            currentWeather = z[0]["description"]
            testStr = currentWeather
            #self.logger.fatal(testStr)            
            
            self.logger.fatal("API data collected")
            
            #write script
            script = ("The current weather is " + currentWeather + " and the temperature is " + str(currentTemperature) + " celcius. The humidity is " + str(currentHumidity) + " percent, and the pressure is " + str(currentPressure) + " hPa.") 
            self.script(script)

        pass

    def onInput_onStop(self):
        self.onUnload() #it is recommended to reuse the clean-up as the box is stopped
        self.onStopped() #activate the output of the box
