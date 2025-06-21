## User Prompt

Here are a few examples of converting natural language descriptions of products into a structured JSON format. Please follow this exact structure for your output.

Example 1:

Input:
"The new Acme noise-cancelling headphones offer superior sound quality and comfortable earcups, perfect for long flights. They come with a 2-year warranty."

Output:

JSON

{
  "product_name": "Acme Noise-Cancelling Headphones",
  "category": "Audio",
  "features": [
    "Superior sound quality",
    "Comfortable earcups",
    "Noise-cancelling"
  ],
  "warranty_years": 2,
  "suitable_for": ["Long flights"]
}
Example 2:

Input:
"Our latest smartwatch, the Chronos X, tracks heart rate, steps, and sleep. It's water-resistant up to 50 meters and has a battery life of 7 days."

Output:

JSON

{
  "product_name": "Chronos X Smartwatch",
  "category": "Wearable Technology",
  "features": [
    "Heart rate tracking",
    "Step tracking",
    "Sleep tracking",
    "Water-resistant (50m)"
  ],
  "battery_life_days": 7
}
Now, convert the following product description into the same JSON format:

Input:
"The 'Everest' hiking backpack features a 60-liter capacity, multiple compartments for organization, and a durable waterproof design. It's ideal for multi-day treks."

## Chatgpt GPT-4o
{
  "product_name": "Everest Hiking Backpack",
  "category": "Outdoor Gear",
  "features": [
    "60-liter capacity",
    "Multiple compartments for organization",
    "Durable waterproof design"
  ],
  "suitable_for": ["Multi-day treks"]
}
