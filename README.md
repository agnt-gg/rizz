# RIZZ: RSS Information Zone Zapper

Because consuming content with AI shouldn't be complicated

> Codename: RSS 3.0, Make America RSS Again.

## 🎯 WHAT RIZZ IS:

- A pattern for AI bots to consume RSS feeds
- Standard XML-based feeds with AI-specific metadata
- A simple way for AI to access machine-readable content
- Based on RSS 2.0: Use XML and HTTP for delivery

## 🚫 WHAT RIZZ IS NOT:

- A framework or library you install
- A new technology or language
- A specific company's product
- An additional abstraction in any way

> 💡 RIZZ simply says: "AI bots should access content through plain RSS feeds using patterns we've used for decades, with AI tweaks via namespaces."

That's it. Just a pattern. ✨

## 🔑 CORE BELIEFS

- Every update is an AI-ready `<item>`
- Every feed is a single XML file
- Every AI bot is welcome
- Every publisher is open to extend

## 🏗️ MINIMUM VIABLE STRUCTURE

### Base RSS 2.0 Elements (Required):

- `<rss>`: Root with version="2.0"
- `<channel>`: Feed metadata (title, link, description)
- `<item>`: Content updates (title, link, description, pubDate)

### AI-Specific Extensions (Optional, Namespaced):

Use the `ai:` namespace (`xmlns:ai="http://xai.org/RIZZ-namespace"`) for AI metadata:

- `<ai:model>`: Compatible AI models (e.g., `<ai:model>Grok, GPT</ai:model>`)
- `<ai:context>`: AI prompt or context (e.g., `<ai:context>Summarize for AI developers</ai:context>`)
- `<ai:dataQuality>`: Data quality score (e.g., `<ai:dataQuality>85</ai:dataQuality>`, 0-100)

## 🤝 THE RIZZ PROMISE:

### OPEN

- Free to use
- Open source (MIT license)
- No vendor lock
- Community driven
- Any AI model supported

### SIMPLE

- XML-based
- Standard HTTP
- Zero dependencies
- No new tech needed

### FLEXIBLE

- Any AI bot
- Any content type
- Any platform

## 🔗 CONNECTION TYPES

### Standard HTTP/XML Interface for Most Things:

- Simple HTTP GET requests to fetch `/RIZZ.xml`
- XML payloads with standard RSS 2.0 structure
- Works with any XML parser or HTTP client
- No special endpoints or authentication required (optional HTTP auth)

### Polling or WebSub for Real-Time Updates:

- AI bots poll the feed URL periodically
- Optional WebSub (Pubsubhubbub) for push notifications
- Low overhead, no vendor lock-in

## 🤖 AI BOT CAPABILITIES

### Process AI-Optimized Content Based on Metadata:

- Use `<ai:model>` to filter compatible models (e.g., only process if "Grok" is listed)
- Use `<ai:context>` to guide actions (e.g., summarize, analyze, or train)
- Use `<ai:dataQuality>` to prioritize high-quality data (e.g., >80 for training)

### Works for Simple to Complex Use Cases:

- Real-time news analysis for AI assistants
- Training data collection for machine learning models
- Contextual prompts for conversational bots

## 🛠️ BASIC OPERATIONS (v0.0.1)

### Consuming an RIZZ Feed:

- Fetch Feed: `GET /RIZZ.xml`
- Parse XML with standard RSS 2.0 elements
- Check `<ai:model>`, `<ai:context>`, and `<ai:dataQuality>` for AI-specific actions

#### Example AI Bot Flow (Pseudo-Code):

```python
import requests
from xml.etree import ElementTree as ET

# Fetch RIZZ feed
response = requests.get("https://example.com/RIZZ.xml")
root = ET.fromstring(response.content)

# Process each item
for item in root.findall('.//item'):
    title = item.find('title').text
    ai_model = item.find('.//ai:model', namespaces={'ai': 'http://xai.org/RIZZ-namespace'})
    ai_context = item.find('.//ai:context', namespaces={'ai': 'http://xai.org/RIZZ-namespace'})
    ai_quality = item.find('.//ai:dataQuality', namespaces={'ai': 'http://xai.org/RIZZ-namespace'})

    if ai_model and "Grok" in ai_model.text:  # Check compatibility
        if ai_quality and int(ai_quality.text) > 80:  # Prioritize high-quality data
            context = ai_context.text if ai_context else "Process normally"
            print(f"Processing: {title} - {context}")
            # Perform AI action (e.g., summarize, analyze)
```

## 🔐 AUTH EXAMPLES

Use standard HTTP auth (e.g., Basic or Bearer tokens) in headers:

```http
GET /RIZZ.xml
Authorization: Bearer your-token-here
```

No special endpoints needed—keep it simple and HTTP-based.

## 🛡️ SCOPE METADATA FOR AI SAFETY

Use `<ai:model>` to limit content to specific AI models (e.g., safe or compatible models only).

Use `<ai:dataQuality>` to ensure only high-quality data is consumed (e.g., >70 for safe training).

#### Example:

```xml
<item>
  <title>Safe AI Update</title>
  <ai:model>Grok, SafeGPT</ai:model>  <!-- Only safe or compatible models -->
  <ai:dataQuality>95</ai:dataQuality> <!-- High-quality, trusted data -->
</item>
```


## 🆕 JSON-LD ENHANCEMENT (Optional)

### Purpose

- Enhance semantic richness and interoperability of RSS feeds.
- Provide structured data that can be easily interpreted by AI bots and other systems.

### Implementation

- Embed JSON-LD within the `<item>` elements to provide additional structured data.

### Example RIZZ Feed with JSON-LD

```xml
<rss version="2.0" xmlns:ai="http://xai.org/RIZZ-namespace">
  <channel>
    <title>AI News Feed</title>
    <link>https://example.com/ai-news</link>
    <description>AI updates for bots</description>
    <item>
      <title>AI Reasoning Breakthrough</title>
      <link>https://example.com/news/reasoning</link>
      <description>New AI logic techniques.</description>
      <pubDate>Mon, 10 Mar 2025 01:45:00 EDT</pubDate>
      <ai:model>Grok, GPT</ai:model>
      <ai:context>Summarize for developers</ai:context>
      <ai:dataQuality>90</ai:dataQuality>
      <script type="application/ld+json">
      {
        "@context": "https://schema.org",
        "@type": "Article",
        "headline": "AI Reasoning Breakthrough",
        "url": "https://example.com/news/reasoning",
        "datePublished": "2025-03-10T01:45:00-04:00",
        "description": "New AI logic techniques.",
        "author": {
          "@type": "Organization",
          "name": "Example News"
        },
        "aiModel": ["Grok", "GPT"],
        "aiContext": "Summarize for developers",
        "aiDataQuality": 90
      }
      </script>
    </item>
  </channel>
</rss>
```

## 🌟 WHY RIZZ?

- **Lightweight and familiar:** Builds on decades of RSS use.
- **AI-ready:** Adds just enough metadata for bots without complexity.
- **Open and free:** No lock-in, no barriers for developers or bots.

## 🤝 Let's Collaborate!

RIZZ Discord: [fictional](https://discord.com/invite/nwXJMnHmXP)

Enjoy using RIZZ! 🎉

RIZZ is an open-source protocol launched under the MIT license by xAI, inspired by SLOP's simplicity for AI integration.