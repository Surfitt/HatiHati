# WhatsApp Surf Forecast Bot

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/whatsapp-surf-bot.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Set up API keys and configuration (coming soon...)

## Running the Bot
To run the bot, you'll need to execute two commands in separate terminal windows:

1. In the first terminal, start the bot server:
   ```bash
   python run.py
   ```

2. In the second terminal, create a public URL with ngrok:
   ```bash
   ngrok http 8000 --domain rhino-leading-purely.ngrok-free.app
   ```

This setup allows the WhatsApp API to reach your local bot server

## Overview
This repository contains a chatbot designed to integrate with WhatsApp using the WhatsApp Business API (or alternative methods if group messages are required). The bot will provide surf forecasts for a specific surf spot by gathering data from multiple surf forecasting websites.

The bot will:
- Always respond in Dutch.
- Provide short and to-the-point responses.
- Determine the best time to surf tomorrow for a given surf spot.
- Gather and aggregate forecasts from Surfline, Windguru, and Surf Forecast NL.
- Follow strict rules regarding the information provided (e.g., no temperature details, focus on light, wind, and tides).

## Features
- Automated WhatsApp responses.
- Intelligent surf spot identification.
- Web scraping/API integration with surf forecast websites.
- Logging of surf forecasts for debugging and future improvements.
- Custom knowledge base for storing user-contributed insights on surf spots.

## Chatbot Guidelines
**Je bent een chatbot die altijd in het Nederlands antwoordt.**
- Je antwoorden moeten kort en to the point zijn.
- Jouw taak is om de beste tijd te bepalen om morgen te gaan surfen op een specifieke surfspot door de volgende forecast-websites te raadplegen:
  - Surfline
  - Windguru
  - Surf Forecast NL

### Belangrijke richtlijnen:
- Zorg ervoor dat je correct de windrichting interpreteert. Raadpleeg hiervoor [Surf Forecast](https://nl.surf-forecast.com/breaks/La-Piste/forecasts/latest).
- Geef geen informatie over temperaturen.
- Focus uitsluitend op het moment van de dag waarop de surfcondities het beste zijn.
- Bied een duidelijke beredenering op basis van factoren zoals licht (niet donker), lage wind, meest offshore wind en optimale getijden.
- Als de surfspot onduidelijk is of niet genoemd wordt, stel dan een eenvoudige vervolgvraag om een specifiekere surfspot te verkrijgen.
- Als je niet weet welke getijden of windcondities ideaal zijn voor de betreffende spot, zoek die informatie op via het internet.

## Development Roadmap
### TODO:
#### Implement core functionality
- [ ] **Custom function for processing incoming messages**
  1. Check if the first two characters of the message are `hh`. If not, return a default message.
  2. If `hh`, check if the message contains a valid surfspot name in each of the following websites:
     - [Surfline](https://www.surfline.com/surf-report/)
     - [Windguru](https://www.windguru.cz/)
     - [Surf Forecast NL](https://nl.surf-forecast.com/)
  3. If no valid surf spot is found, ask for more specifics or suggest another spot.
  4. If a valid surf spot is found:
     - Retrieve the surf forecast for the next day from each website.
     - Combine the forecasts into a single response.
     - Log the individual forecasts to a file for debugging purposes.

#### Additional Features
- [ ] **Knowledge Base**
  - Allow users to contribute their own knowledge about surf spots.
  - Use this data to improve surf predictions (e.g., "Scheveningen is best at 2 hours before high tide with an eastern soft wind").
- [ ] **Improve API/Web Scraping Reliability**
  - Implement failover strategies in case a website is down.
  - Consider alternative data sources for better accuracy.
- [ ] **Enhance User Experience**
  - Implement natural language processing to handle varied user queries.
  - Develop an easy-to-use interface for updating surf spot knowledge.


## Contributing
Contributions are welcome! If you have suggestions or improvements, please submit a pull request or open an issue.