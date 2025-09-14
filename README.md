# Temperature-converter
This is a Temperature Converter web page built using only HTML and CSS. It focuses on designing a clean, responsive, and user-friendly interface for converting between Celsius, Fahrenheit, and Kelvin.  🔹 Built with semantic HTML for structure 🔹 Styled with modern CSS for layout and design 🔹 Responsive design for different screen sizes.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Temperature Converter</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f8ff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .converter {
      background: #ffffff;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.2);
      text-align: center;
      width: 300px;
    }
    input, select, button {
      padding: 10px;
      margin: 10px 0;
      width: 80%;
      border-radius: 5px;
      border: 1px solid #ccc;
      font-size: 16px;
    }
    button {
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
    .result {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
      color: #333;
    }
  </style>
</head>
<body>
  <div class="converter">
    <h2>Temperature Converter</h2>
    <input type="text" id="tempInput" placeholder="Enter temperature">
    <select id="unitSelect">
      <option value="celsius">Celsius</option>
      <option value="fahrenheit">Fahrenheit</option>
      <option value="kelvin">Kelvin</option>
    </select>
    <button onclick="convertTemp()">Convert</button>
    <div class="result" id="result"></div>
  </div>

  <script>
    function convertTemp() {
      let temp = document.getElementById("tempInput").value;
      let unit = document.getElementById("unitSelect").value;
      let resultDiv = document.getElementById("result");

      // Validate input
      if (isNaN(temp) || temp === "") {
        resultDiv.innerHTML = "Please enter a valid number!";
        return;
      }

      temp = parseFloat(temp);
      let celsius, fahrenheit, kelvin;

      switch(unit) {
        case "celsius":
          celsius = temp;
          fahrenheit = (temp * 9/5) + 32;
          kelvin = temp + 273.15;
          break;
        case "fahrenheit":
          celsius = (temp - 32) * 5/9;
          fahrenheit = temp;
          kelvin = celsius + 273.15;
          break;
        case "kelvin":
          celsius = temp - 273.15;
          fahrenheit = (celsius * 9/5) + 32;
          kelvin = temp;
          break;
      }

      resultDiv.innerHTML = `
        Celsius: ${celsius.toFixed(2)} °C <br>
        Fahrenheit: ${fahrenheit.toFixed(2)} °F <br>
        Kelvin: ${kelvin.toFixed(2)} K
      `;
    }
  </script>
</body>
</html>
