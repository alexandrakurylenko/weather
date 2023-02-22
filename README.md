# weather
Api for weather

from flask import Flask, request 
import requests 
 
app = Flask(__name__) 
 
@app.route('/weather', methods=['GET']) 
def get_weather(): 
    api_key = 'YOUR-API-KEY' # Replace with your OpenWeatherMap API key 
    place = request.args.get('place') 
    url = f"http://api.openweathermap.org/data/2.5/weather?q={place}&appid={api_key}&units=metric" 
    response = requests.get(url) 
    if response.status_code == 200: 
        return response.json() 
    else: 
        return 'Error fetching weather data', 500 
 
if name == '__main__': 
    app.run(debug=True)
