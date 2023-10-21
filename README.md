# next-recipe
Using LLMs to help find new recipes that you are similar to ones you have tried before!

## Inspiration
My great friend and avid home cook has mentioned the "cooking drought", where he has cooked at a high level for a long while, resulting in cooking becoming rather boring since he "already knows what it will taste like before I even make it". As good as the food may be, this lack of "surprise" can affect many home cooks out there. The only hope in spicing up his cooking more, as he puts it, is to get more cooking equipment  or try new cooking techniques with existing equipment.

## User Journey
Within this web-app, the user can supply 3-5 recipes they have made before (either in url form or just the dish name), and (optionally) a rating out of 5 for each dish and a short comment as to why they loved this recipe/dish. After the user presses "Generate!", the web-app will use LLMs to find a few new recipes which are 
1. _Similar_ in difficulty and requirements for equipment
2. _Similar_ in key feats (key ingredients, cuisine, dietary style) as the user-inputted recipes
3. _Different_ in a new dimension that would add creativity or fun

Optionally, the UI can also have a "preview" function, where each suggested recipe is shown as just the `Name`, then can "Expand" to show a short summary (which most avid home cooks should be able to get a decent grasp of the food just through this), equipment requirements, cuisine type, and required time.

## Under the Hood
The technology underlying the search is LLMs:
1. Using a LLM that is plugged into the internet to provide summaries of key features of each user-inputted recipe (technique, cuisine, ingredients, flavours, etc)
2. Prompting LLM to suggest new recipes/dishes based on the key features provided in step 1
   - One approach could be to ask "Summarize how the 5 recipes are similar, and how they are different", and then we could structure the `<similarities>` into another prompt such as "Suggest 5 dishes that have a key component of `<similarities>` but be creative with the other components of the dishes."
4. Using another internet plug in to find recipes for dishes suggested in step 2
