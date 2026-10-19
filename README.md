# ⛵ Ship Drift

A 3D sailing roguelike built with Blueprints in Unreal Engine 5. I worked on the game as the UI Designer, UI Developer, and Scrum Master at 3Bee. This README focuses on the user interface: the HUD, menus, and the systems behind them.

## 📦 Technologies

- `Unreal Engine 5`
- `Blueprints`
- `UMG (Unreal Motion Graphics)`
- `Scrumwise`
- `Lospec500 Colour Palette`
- `Germania One Font`
- `Easy Input Prompts by Nerwy`


## ⚙️ Features

Here's what you can do in Ship Drift's user interface:

- **Browse the Shop**: Spend your collected scrap with the scrap trader. Four items are on offer each time: two upgrades, a skill point, and an extra life. Hover over an item and the trader explains it in a speech bubble. You can only buy one item before the shop closes, so choose carefully.

- **Manage Your Inventory**: Use two panels, Equipped and Inventory, to swap upgrades in and out of your boat. Hover over an upgrade to see its name, description, and skill point cost. Click to equip it, and click it again in the Equipped panel to remove it.

- **Track Everything in the HUD**: Keep an eye on your total scrap, remaining lives (shown as hearts), and both cannon cooldowns. The cannon icons sit on the left and right of the boat to match where the cannons are in the world.

- **Pause and Review**: Pause at any time to resume, open settings, or exit to the main menu. The pause menu also shows your current mission and bonus challenges without the distraction of gameplay.

- **Navigate the Main Menu**: Play, open settings, view the credits, or exit. The menu sits over the same ocean scene shown in the opening cutscene.

- **Get Clear Feedback**: Error and confirm tooltips pop up over any menu to explain why an action failed or to double-check an important purchase.

### 🎨 Design Details:

- **Consistent Icons**: Lives, capacity, and scrap icons share one style, with a single base colour, a lighter and darker shade, and a thin dark outline. All colours come from the Lospec500 palette.
- **Accurate Input Prompts**: Footers show the correct prompts for the active control scheme.
- **Smooth Transitions**: Menus animate in and out instead of snapping on and off the screen.

## 🔨 The Process

I started in Pre-Production by building the UI Manager, a layering system that pushes and pops widgets onto layers: `Game` for the HUD, `Menu` for full menus, and `Modal` for tooltips. Every menu after that reused it, so transitions stayed consistent and I could build new screens faster. The UI Manager took many hours, but it needed to be right before I could integrate it cleanly into the game code.

Next, I built the Shop and Inventory. The Shop gathers a reference to the score manager and player, then fills each item with data from the upgrades data table, so changing prices is easy. A function called `Set Not Owned Upgrades` makes sure players are never offered an upgrade they already own. The Inventory is driven by an `On Update Inventory` event that refreshes both panels and assigns the click and hover behaviour to each upgrade.

After that, I added the tooltip system. The error and confirm tooltips are deliberately simple, so each menu decides what happens when a button is clicked. I also made a Modal component that lets any menu open when the player collides with an object in the level, which is how the Shop appears.

The HUD came in Sprint 2 of Production. The scrap counter updates through an `On Increment Scrap` event, while the cannon cooldown bars update on `Event Tick`. That makes the HUD the only menu that uses Tick, because the player can be moving quickly and needs up-to-date cooldowns.

Then I iterated. Every menu went through at least one redesign based on user feedback, and the Inventory and Shop have been through several major and minor iterations. Some of the changes:

- Added the scrap trader character so players understand what items do.
- Added a persistent scrap counter after players couldn't plan their upgrades.
- Combined the loadout and owned upgrades into one two-panel screen.
- Moved the mission objective from the HUD to the pause menu to reduce clutter.
- Replaced static menu backgrounds with an ocean scene and a blur effect.

Alongside the UI, I acted as Scrum Master. I organised sprint planning, reviews, and retrospectives, tracked work in Scrumwise, and used burndown charts to spot problems early. I also made an Estimation Table to track team availability. The team didn't end up using it, but it taught me a lot about adapting a process to the people using it.

## 📚 What I Learned

During this project, I picked up a lot about designing for players who have to make quick decisions, and about building UI that other people can work with.

### 🧭 Player-Centred UX Design:

- **Clarity Under Pressure**: Ship Drift mixes fast combat with roguelite progression, so the interface has to communicate instantly. I learned to ask what a player really needs to see at any moment, and to remove anything that doesn't earn its place on screen.
- **Balancing Information**: Too many HUD elements overwhelm the player, but too few leave them confused. Finding that balance took several iterations.

### 🗂️ UI Layering and Architecture:

- **Planning Ahead**: Building the UI Manager taught me to think about how menus relate to each other. Keeping menus on separate layers means a tooltip can sit on top of a menu without removing it from the stack.

### 🧩 Blueprint Structure:

- **Readable, Reusable Logic**: The Shop and Inventory were complex Blueprints. I learned to keep them robust and bug-free while still being readable, such as storing each item's data in its own custom widget.

### 🔁 Iterating From Feedback:

- **Redesigning Existing Work**: Revisiting menus I had already built was challenging, but user tests kept showing me problems I hadn't noticed.

### 🏃 Agile and Scrum:

- **Flexibility**: Strict Scrum didn't always fit a student project with changing schedules. I learned that a Scrum Master's job is more about communication and adapting the workflow than enforcing rules.
- **Realistic Scope**: Early estimates were often too optimistic, which taught me to break tasks down more carefully.

### 📈 Overall Growth:

Each part of this project helped me understand more about how interface design, programming, and team process fit together. It was more than just making menus. It was about solving problems with a team, listening to feedback, and improving my skills for future work.

## ✔️ How can it be improved?

- Cross out or remove completed missions and bonus challenges in the HUD.
- Keep running user tests on the Inventory and Shop and refine them further.
- Add new hover and idle animations to the main menu buttons.
- Add more upgrade types and attribute icons as the game grows.
- Add more feedback to the HUD during combat.
- Keep improving accessibility and input prompts for different control schemes.

## 🚚 Running the Project

To run the project in your local environment, follow these steps:

1. Clone the repository to your local machine.
2. Install Unreal Engine 5 (use the version the project was built with).
3. Open the `.uproject` file with Unreal Engine.
4. Wait for the shaders to compile, then open the main menu level.
5. Press Play in the editor to start the game.

## 📽️ Video

[**Gameplay showreel!**](https://www.youtube.com/watch?v=3TQ8KpqaiMk&t=56s)
