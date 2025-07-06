

### 1. **Choose a Public API**

Let’s use the **OpenWeatherMap API** (free & easy):

* Go to: [https://openweathermap.org/api](https://openweathermap.org/api)
* Sign up and get your **API key**.
* We'll use this endpoint:

  ```
  https://api.openweathermap.org/data/2.5/weather?q={city name}&appid={API key}&units=metric
  ```

---

### 2. **Project Folder Structure**

```
weather-app/
├── index.html
├── style.css
└── script.js
```

---

### 3. **index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Weather App</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>Weather Checker 🌤</h1>
    <input type="text" id="cityInput" placeholder="Enter city name" />
    <button onclick="getWeather()">Get Weather</button>
    <div id="weatherResult"></div>
  </div>
  <script src="script.js"></script>
</body>
</html>
```

---

### 4. **style.css**

```css
body {
  font-family: Arial, sans-serif;
  background: linear-gradient(to bottom right, #6dd5ed, #2193b0);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.container {
  text-align: center;
  background: white;
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

input {
  padding: 10px;
  font-size: 16px;
  width: 200px;
}

button {
  padding: 10px 20px;
  margin-left: 10px;
  font-size: 16px;
  cursor: pointer;
}

#weatherResult {
  margin-top: 20px;
  font-size: 18px;
}
```

---

### 5. **script.js**

```javascript
async function getWeather() {
  const city = document.getElementById("cityInput").value;
  const apiKey = "YOUR_API_KEY"; // Replace with your actual API key
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

  try {
    const response = await fetch(url);
    if (!response.ok) throw new Error("City not found");

    const data = await response.json();
    const temp = data.main.temp;
    const description = data.weather[0].description;
    const cityName = data.name;

    document.getElementById("weatherResult").innerHTML = `
      <h3>${cityName}</h3>
      <p>Temperature: ${temp} °C</p>
      <p>Condition: ${description}</p>
    `;
  } catch (error) {
    document.getElementById("weatherResult").innerHTML = `<p>Error: ${error.message}</p>`;
  }
}
```

---

### 6. **Deploy to GitHub Pages**

1. Push your `weather-app` folder to a GitHub repo.
2. Go to **Settings > Pages**.
3. Set:

   * Branch: `main`
   * Folder: `/ (root)`
4. Click **Save** and visit your live URL.




