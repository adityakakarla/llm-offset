# [CallToChange](https://calltochange.vercel.app/) 🌍

## Description

CallToChange is a carbon emissions calculator for AI apps. This tool analyzes and calculates the carbon emissions generated by a company's LLM (Large Language Model) calls.

This project won first place in the environmental track at LA Hacks (hundreds of participants)

---

## What it does

CallToChange seamlessly integrates with our custom Python library (call-to-change) to log LLM call emissions. It utilizes academic research and information from the Department of Energy to accurately determine the carbon footprint of each LLM call.

Our visually engaging dashboards provide clear insights into emissions data, aiding companies in making informed decisions to addresss their environmental impact.

---

This repo is for call-to-change, the Python library that works with our web app to log LLM calls.

---

## How to use the Python library

Use the command pip install call-to-change to download our library. Ensure the downloaded version is >= 0.8.6.

Here is a sample script utilizing call-to-change.

~~~
from openai import OpenAI
from call_to_change import log

client = OpenAI()

log(client, 'test@test.com')

response = client.chat.completions.create(
  model="gpt-3.5-turbo",
  messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Who won the world series in 2020?"},
  ]
)

print(response.choices[0].message.content)
~~~
---
## How to use the log function

The log function takes in two parameters, an OpenAI client and an email address.

It modifies the client to log any text generation or image generation calls you made. These calls will be tied to the email address you input into the log function.

If you have an account with _[our web app](https://calltochange.vercel.app)_, your logged calls can be seen through your dashboard. From there, you can view the carbon emissions tied to your OpenAI calls and the cost to offset these emissions.

If not, your text generation and image generation calls will still be saved. To access your data, create an account with us _[here](https://calltochange.vercel.app/auth/sign-up)_ and go to the Dashboard page.

---

## Under the hood

We developed CallToChange using Next.js and Python.

Our Python library logs LLM calls in MongoDB. Under the hood, our library does this by sending a POST request to API routes in our web app. These API routes securely handle data updates in MongoDB.

In our web app, we use Next.js and MongoDB to fetch user information (such as the number of times a user has used text generation). To create an interactive interface, we utilized Tailwind CSS. For user authentication, we used Clerk to manage user accounts.

