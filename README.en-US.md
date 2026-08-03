

# Minimalist Short URL Generator

A short URL generation service built with Cloudflare Workers and KV storage.
Due to the limitations of [Cloudflare](https://www.cloudflare.com)'s free plan, no preview URL is provided. Please deploy it yourself via [Cloudflare Workers](https://dash.cloudflare.com).  
The free plan is fully sufficient for personal use. For high-volume needs, you can upgrade to a paid plan.

## Features

- 🔗 Generate short URLs
- 🔒 Supports password protection
- ⏰ Supports setting expiration dates for links
- 🔢 Supports visit count limits
- 🤖 Integrated Cloudflare Turnstile bot protection
- 🎨 Clean and beautiful user interface
- ✨ Supports custom short URLs

## Deployment Steps

### 1. Prerequisites

- Register for a [Cloudflare](https://dash.cloudflare.com) account
-------
- Create a namespace in Workers KV
![image](https://github.com/user-attachments/assets/eb761e5d-bdfa-4ef6-8c8f-d347bd27daed)

- Bind the KV namespace in the Worker settings tab

- Set the variable name to `URL_SHORT_KV`, and the KV namespace to the one you just created

![image](https://github.com/user-attachments/assets/68db428a-c3af-42f7-90fc-43ba91f9cc7b)

Copy the code from [index.js](/index.js) in this project into your Cloudflare Worker, then click Save and Deploy.

### 2. Configure Turnstile

To enable bot protection:

1. Create a new Turnstile site key in the [Cloudflare Dashboard](https://dash.cloudflare.com/?to=/:account/turnstile)
2. Obtain the site key and secret key
3. Add the following environment variables in the Worker settings:
   - `TURNSTILE_SITE_KEY`: Your site key
   - `TURNSTILE_SECRET`: Your secret key

## Preview

![image](https://github.com/user-attachments/assets/25d3c304-3b25-485a-b158-29d795439cbd)

## Usage Instructions

1. Visit your Worker URL (e.g., `https://url-shortener.your-username.workers.dev`)
2. Enter the URL you want to shorten
3. (Optional) Set:
   - Custom short URL
   - Expiration date
   - Access password
   - Maximum visit count
4. Click the generate button to get the short URL

## Notes
#### Workers  
Each request is limited to 10 ms of CPU time  
Low latency after the first request  
Maximum of 100,000 requests per day (UTC+0)  
#### KV  
Global low-latency key-value edge storage  
Maximum of 100,000 read operations per day  
Maximum of 1,000 write, delete, and list operations per day  
  
## License

MIT License

## Acknowledgments
Thanks to [Cloudflare](https://www.cloudflare.com) for providing the platform and services.
