

# OopsBot - Slack Bot

A simple Slack bot to alert channels when a user deletes a message and send a screenshot of that message.

# Table of Contents

	•	Introduction
	•	Features
	•	Installation
	•	Configuration
	•	Usage
	•	Deployment
	•	License

# Introduction

OopsBot is a Slack bot that keeps an eye on deleted messages in Slack channels and immediately sends a screenshot of the deleted message to alert everyone in the channel. This bot helps you keep track of the deleted content and adds some transparency to the communication within your workspace.

# Features

	•	Greeting Messages: Responds with a personalized greeting when someone says “hello”, “hi”, or “hey”.
	•	Deleted Message Alerts: Notifies a Slack channel when a message is deleted and shares a screenshot of the   
        deleted message.
	•	Customizable User Info: Fetches user details like display name, avatar, and timezone for more personalized 
        notifications.
	•	Screenshot Generation: Uses a custom API (NIGEN_URI) to capture and send a screenshot of the deleted message.

# Installation

1. Clone the repository:

git clone https://github.com/Gilugali/OopsBot.git
cd OopsBot

2. Install dependencies:

Make sure you have Node.js and npm installed on your system. Then run the following command:

npm install

3. Create .env file:

In the root directory, create a .env file to store your environment variables. The file should contain:

SLACK_BOT_TOKEN=your-slack-bot-token
SLACK_SIGNING_SECRET=your-signing-secret
SLACK_APP_TOKEN=your-app-token
NIGEN_URI=your-screenshot-api-uri
PORT=3000

	•	SLACK_BOT_TOKEN: The token for your Slack bot (found in Slack App settings).
	•	SLACK_SIGNING_SECRET: Signing secret for validating requests (found in Slack App settings).
	•	SLACK_APP_TOKEN: The app token required for socket mode (Slack App settings).
	•	NIGEN_URI: The URL of the service that generates screenshots of deleted messages.
	•	PORT: The port on which your app will run (default is 3000).

# Configuration

	1.	Slack App Setup:
	•	Go to Slack API Apps and create a new app.
	•	Enable Socket Mode to listen for events in real-time.
	•	Add necessary bot permissions like chat:write, users:read, and channels:history.
	•	Install the app in your workspace to get the required tokens.
	2.	Set Up the Screenshot API:
	•	The bot sends a screenshot of the deleted message using the NIGEN_URI API. Ensure that the API is active and capable of generating screenshots from the passed parameters.

# Usage

	1.	Start the Bot:
Once everything is set up, run the following command to start the bot:

node app.js


	2.	Greeting Messages:
The bot listens for messages containing “hello”, “hi”, or “hey”. It responds with a personalized message like:

Wassup, @username


	3.	Message Deletion Alerts:
When a user deletes a message, the bot will:
	•	Notify the channel with the message: <!channel>, @username deleted their message!.
	•	Attach a screenshot of the deleted message using the NIGEN_URI.
	4.	Sending a Screenshot:
The screenshot URL will look something like this:

${NIGEN_URI}?message=deleted_message&username=username&time=message_time&avatar=avatar_url

# Deployment

To deploy your bot, you can use cloud platforms like Heroku, AWS Lambda, or Vercel.

Example: Deploying to Heroku

	1.	Install Heroku CLI if you don’t have it installed.
	2.	Run the following commands to deploy:

git init
heroku create your-app-name
git push heroku master

	3.	Set environment variables in the Heroku dashboard or via CLI:

heroku config:set SLACK_BOT_TOKEN=your-slack-bot-token
heroku config:set SLACK_SIGNING_SECRET=your-signing-secret
heroku config:set SLACK_APP_TOKEN=your-app-token
heroku config:set NIGEN_URI=your-screenshot-api-uri

	4.	The bot should now be live!

License

This project is licensed under the MIT License - see the LICENSE file for details.

Contributing

Feel free to fork and submit pull requests for any improvements. If you encounter any issues, open an issue in the repository.

Support

If you need help or have questions, feel free to reach out via email or open an issue on the GitHub repository.
