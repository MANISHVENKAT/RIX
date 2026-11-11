# RIX
The Spending Analyzer 
Understand your money. Control your spending.
RIX is a personal finance web app that tracks transactions, budgets and savings goals, and uses AI plus matrix-based spending analysis to explain where your money goes.
Live app: https://rix.base44.app
Features
Transaction tracking — log and review income and expenses.
Budgets — set spending limits per category and watch progress.
Savings goals — create goals and fund them over time.
Matrix-based spending intelligence — a category-by-time view that makes spending patterns easy to compare.
AI categorization — transactions are labelled automatically.
AI spending insights — plain-language summaries and suggestions based on your budgets and goals.
AI chat assistant — ask questions about your own spending.
Forecasts and anomaly detection — AI-assisted projection of upcoming spend and flags for unusual activity.
PayPal sandbox payments — PayPal Checkout powers the payment flow, tested end to end in the free PayPal sandbox.
How RIX uses PayPal and AI
The hackathon requirement is to integrate the PayPal developer platform (free sandbox) together with an AI tool. RIX does both.
PayPal developer platform (sandbox)
Tool
What it does in RIX
PayPal Checkout — Orders API v2 and the PayPal JavaScript SDK
Creates and captures payment orders so users can complete payments inside RIX
PayPal Sandbox accounts (business and personal)
Lets every payment be tested with fake money, with no real funds moved
All PayPal calls use the sandbox environment (https://api-m.sandbox.paypal.com). No live credentials are used anywhere.
AI
Tool
What it does in RIX
Base44 built-in AI (LLM integration, InvokeLLM)
Categorizes transactions, writes spending insights, answers questions in the chat assistant, and produces forecasts and anomaly flags
The AI receives the user's transaction, budget and goal data as context and returns structured results (categories, insights, flags) that the app displays.
Other tools and platforms
Base44 — app builder and hosting: front end, data entities, authentication and backend functions.
No optional sponsor tools (APIMatic, Postman/Astro, Render) are used.
Setup instructions
Prerequisites
A Base44 account
A free PayPal Developer account
1. Get the code
git clone https://github.com/<your-username>/rix-spending-analyzer.git
cd rix-spending-analyzer
2. Create PayPal sandbox credentials
Sign in at https://developer.paypal.com and open Apps & Credentials.
Switch to Sandbox, then choose Create App.
Copy the Client ID and Secret.
Open Testing Tools → Sandbox Accounts and note the generated personal (buyer) account. You will use it to test payments.
3. Configure environment variables
Copy the example file and fill in your sandbox values:
cp .env.example .env
PAYPAL_ENV=sandbox
PAYPAL_CLIENT_ID=your-sandbox-client-id
PAYPAL_CLIENT_SECRET=your-sandbox-client-secret
In Base44, add the same three values as environment variables or secrets in your app's settings so backend functions can read them. Never commit .env.
4. Run the app
Import or recreate the project in Base44 and publish it.
The Base44 AI integration is built in, so no AI API key is needed.
Open the app and sign in.
5. Test the PayPal flow
Start a payment in the app.
When the PayPal window opens, sign in with the sandbox personal account from step 2.
Approve the payment. You should see a successful capture, and the sandbox business account balance changes in the PayPal developer dashboard.
Security notes
Sandbox credentials only. Do not use live PayPal credentials with this project.
Secrets live in environment variables, never in source control.
Payment capture happens on the backend, so the client secret is never exposed in the browser.
License
Released under the MIT License, an OSI-approved open source license.