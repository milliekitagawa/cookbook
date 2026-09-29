# PICK A PLATE

PICK A PLATE is a minimal recipe generator for people who do not know what to cook or want more variation in their meals. Users choose a difficulty, cooking-time range, and dietary preference, then generate and browse matching recipes. Recipes can be saved to a personal cookbook, opened in a full-recipe view, and downloaded as self-contained PNG recipe sheets.

The project uses a small built-in recipe dataset, so it works immediately without accounts, APIs, or external services.

## Run locally

Open `index.html` directly in a browser, or serve the project folder locally:

```sh
python3 -m http.server 4173
```

Then visit [http://localhost:4173](http://localhost:4173). No installation or build step is required.

## AI tool used

This project was developed with Codex. I used it to build the HTML, CSS, and JavaScript prototype; develop the recipe content; and iterate on visual hierarchy, interaction feedback, layout, saving, and download behavior.

## Selected prompts

1. **Initial concept**

   > A random recipe generator for people who do not know what to cook, or want more variation to their meals. Users can set preferences like difficulty and cooking time, then save recipes they like to their personal cookbook.
   >
   > When someone finds a recipe they like, the experience should let them save it to their personal cookbook. The website should be minimal. The website should have a small box for preferences at the top, where users can choose level of hardness, time to cook, and options like vegetarian, gluten-free, vegan, and others. On the very right of the box there should be a “generate” button. Under this box will be the main visual, which would be in the form of cards. Each card contains the recipe name, level of hardness, time to cook, and tags like vegan, vegetarian, gluten free, and others. A list of material should be on there as well. Arrows should be placed on the left and right of the card, for users to browse their recipe options. A save function should be prominently displayed on each card. It should not disappear because of scrolling, and it should also be prominently displayed if the recipe card is expanded into its own page.

2. **Generation feedback**

   > When GENERATE is clicked, immediately keep/show the full recipe card structure, but clear the previous recipe content and begin a short generation animation for the first matching recipe. Use a subtle typewriter-style generation animation. Reveal the new recipe’s actual content progressively from left to right, as though the interface is actively writing the recipe. Stagger the animation in this order: recipe title → difficulty/time/diet metadata → description → ingredients.

3. **Recipe-card structure**

   > Restructure and rebuild the entire recipe card layout from scratch. Do not simply adjust the spacing or patch the existing card structure. Reorganize the card’s internal HTML/CSS so the layout is cleaner, more compact, and easier to control. Preserve all existing recipe data and functionality, including SAVE/SAVED, FULL RECIPE, navigation, and recipe generation. Structure the rebuilt card into clear sections in this order: Recipe title + SAVE/SAVED → metadata row → description → ingredients → FULL RECIPE. Each section should have a deliberate amount of spacing rather than relying on fixed heights or large empty areas to position elements.

## Reflection

My website is a random recipe generator for people who do not know what to cook. The website executes my main interaction precisely: it makes it easy for users to save and unsave generated recipes.

Throughout the iterations, I used AI to address three main design decisions. First, I made the save button prominent so users can easily tell whether they have saved a recipe. Second, I horizontally stacked the **Generated Recipes** and **Saved Recipes** sections. Keeping them in the same viewport lets users immediately see the feedback of saving. Third, I limited each recipe to a concise preview, preventing information overload. I also prompted AI to ensure that saving works properly. To extend this action, I added a download option so users can save a full recipe as a PNG file on their device. This completes the notion of saving beyond the in-page cookbook.

Though the project started by focusing on saving, I spent time testing and changing other interactions. A major problem I found was the lack of signifiers, so I added three:

1. **Indication of generation.** This was nonexistent in the first iteration, so users would not know if the recipes shown had regenerated. At first I asked AI to add a signifier without specifying how it should work; it produced a “Recipe Generated” message, which was functional but rudimentary and not seamless. I then considered how LLMs generate outputs as if the text is being typed. This idea became the typewriter-style generation animation in the design.
2. **Reminder to press Generate.** I noticed that after editing preferences, I sometimes forgot to press **Generate**. I added a flashing effect to the button as a reminder.
3. **Progression of browsing generated recipes.** Showing progression gives users an expectation of how many recipes they can browse.

Through the iterations and working with Codex, I discovered that AI code generation is extremely helpful for structuring the page and generating recipe content. However, it can overlook small details that elevate the user experience, including the signifiers described above. I needed to explicitly state the flow of interactions and how feedback should look. I also found that a basic understanding of HTML and CSS is useful for styling issues. When fixing a layout mistake, AI often edits the existing code, and those existing blocks can limit layout variation. Understanding that helped me instruct it to rebuild a structure rather than only patch it.

There are parts that did not fully match my original intention. The generated recipes are placeholders; I originally hoped they could be generated on the spot. Another unresolved issue is responsive behavior on smaller screens. The design works best in a larger viewport, and could be refined further for compact screens.
