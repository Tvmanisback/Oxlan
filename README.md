Oxlan AI Website

A responsive AI chat website powered by a Groq API backend deployed on Vercel.

Features

* Responsive desktop and mobile interface.
* Purple-themed Oxlan AI design.
* Chat with an AI through the Groq API.
* Conversation history stored in the browser.
* Create and switch between conversations.
* Suggested prompts for coding, learning, debugging, and game development.
* Typing indicator while the AI responds.
* Markdown-style formatting for AI responses.
* Single-file frontend using index.html.
* No frontend API key required.

Project Structure

oxlan-ai-website/
├── index.html
└── README.md

Backend

The website sends chat requests to the Vercel backend:

https://oxlan-backend-9twiu9te3-elijahpauley186-3015s-projects.vercel.app/api/chat

The backend is expected to accept a JSON request containing a messages array:

{
  "messages": [
    {
      "role": "user",
      "content": "Hello, Oxlan AI!"
    }
  ]
}

The expected successful response is:

{
  "reply": "Hello! How can I help you?"
}

The backend must handle Groq API requests using a server-side environment variable named GROQ_API_KEY.

Never place the Groq API key in index.html, JavaScript delivered to the browser, or any public repository file.

Deployment With GitHub Pages

1. Open the website repository on GitHub.
2. Add index.html to the repository root.
3. Add this README.md.
4. Commit the files to your default branch.
5. Open the repository’s Settings.
6. Select Pages.
7. Under the build and deployment section, select Deploy from a branch.
8. Choose your default branch and the / (root) folder.
9. Save the settings.
10. Wait for GitHub Pages to publish the website.

Your site will be available at the GitHub Pages address displayed in the repository’s Pages settings.

Backend Configuration

The Vercel backend must be deployed and configured with:

GROQ_API_KEY=your_actual_groq_api_key

Add the value through Vercel’s Environment Variables settings. Do not commit it to GitHub.

After changing environment variables, redeploy the backend if required.

CORS

The backend must allow requests from the website’s exact published origin.

For example, a GitHub Pages site commonly uses an origin like:

https://your-username.github.io

If the website is published from a project repository, the page URL includes the repository name, but the origin is still the scheme and hostname.

Configure the backend’s CORS allowlist using the actual website origin. Do not allow arbitrary origins unnecessarily.

Troubleshooting

The website loads, but AI responses fail

* Confirm the Vercel deployment is successful.
* Verify the /api/chat endpoint is correct.
* Confirm GROQ_API_KEY is configured in Vercel.
* Redeploy after changing environment variables.
* Inspect the browser console for network or JavaScript errors.

CORS error

Configure the backend to allow the website’s published origin and the required POST and OPTIONS requests.

HTTP 404

Verify that the backend has an API route at /api/chat.

HTTP 500

Inspect the Vercel function logs for backend errors, missing environment variables, or Groq API failures.

Related Project

Oxlan AI’s plugin and skill instructions are maintained separately from this website.

Repository: https://github.com/Tvmanisback/oxlan-ai

Security

* Keep API credentials on the backend.
* Never publish secrets in source code.
* Validate requests on the backend.
* Apply appropriate rate limiting to prevent abuse.
* Avoid storing sensitive conversations on shared devices.

License

Add a license file if you intend to grant specific reuse or redistribution permissions.
