# 🍳 Smart Recipe Generator

Smart Recipe Generator is a web app that suggests recipes based on available ingredients entered by text or image. It uses AI-powered ingredient recognition, dietary filters, and a smart matching algorithm to deliver personalized, healthy recipes with nutrition info and substitutions in a clean, responsive UI.

---

## 🚀 Overview
Smart Recipe Generator suggests multiple ranked recipes using typed or photographed ingredients. It supports dietary filters, serving-size adjustments, substitutions, ratings, and favorites. The focus is on clean UX, robust matching logic, and practical AI-backed ingredient recognition.

---

## ✨ Features
- Ingredient input (text, list, or photo)
- Dietary filters: vegetarian, vegan, gluten-free, etc.
- Recipe ranking algorithm with substitutions
- Nutritional info display
- Serving-size adjustment
- Recipe ratings and favorites (localStorage)
- Mobile-responsive design
- Hosting ready (Vercel/Netlify for frontend, Render/Heroku for backend)

---

## 🧠 Tech Stack
**Frontend:** React (Vite) + Tailwind CSS  
**Backend:** Node.js + Express  
**ML:** TensorFlow.js (MobileNet) or Google Vision API  
**Database:** JSON file (`recipes.json`)  
**Hosting:** Vercel / Netlify (frontend), Render / Heroku (backend)

---

## ⚙️ Architecture


---

## 🧩 API Endpoints
| Method | Endpoint | Description |
|--------|-----------|-------------|
| GET | `/recipes` | List all recipes with filters |
| POST | `/recipes/match` | Returns ranked recipes |
| POST | `/recognize-image` | Detects ingredients from image |
| POST | `/rating` | Adds or updates recipe rating |
| POST | `/favorites` | Adds/removes favorites |

---

## 🧮 Recipe Matching Logic
```js
function scoreRecipe(recipe, availableIngredients, dietaryPrefs) {
  if (recipe.violates(dietaryPrefs)) return -Infinity;
  const totalWeight = recipe.ingredients.length;
  const presentWeight = recipe.ingredients.filter(i =>
    availableIngredients.includes(i.name)
  ).length;
  const score = presentWeight / totalWeight;
  return score;
}
{
  "id": "r001",
  "title": "Tomato Basil Pasta",
  "cuisine": "Italian",
  "ingredients": [
    {"name": "pasta", "qty": 200, "unit": "g"},
    {"name": "tomato", "qty": 2, "unit": "pcs"},
    {"name": "basil", "qty": 5, "unit": "leaves"}
  ],
  "nutritional": {"calories": 450, "protein_g": 12},
  "steps": ["Boil pasta", "Make sauce", "Mix and serve"],
  "difficulty": "easy",
  "time_minutes": 25,
  "dietary_tags": ["vegetarian"]
}

# Clone repo
git clone https://github.com/yourusername/smart-recipe-generator.git
cd smart-recipe-generator

# Install dependencies
cd backend && npm install
cd ../frontend && npm install

# Run locally
npm run dev  # in both frontend and backend folders

# Build for production
cd frontend && npm run build


