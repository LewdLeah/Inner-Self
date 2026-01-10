<p align="center">
  <img src="https://raw.githubusercontent.com/LewdLeah/Inner-Self/main/assets/cover1.png" width="800">
</p>

# Inner Self 🎭
### *Giving characters minds of their own~*
Made by LewdLeah ❤️

---

## Overview

Inner Self is an AI Dungeon mod that grants memory, goals, secrets, planning, and self-reflection capabilities to the characters living in your story. Simulated agents build and maintain their own minds to learn from experiences, form opinions, and adapt their behavior over time. Inner Self provides the AI with the tools it needs to truly embody characters, allowing them to feel more alive and nuanced over long adventures.

In some ways this is the spiritual successor to [Auto-Cards](https://github.com/LewdLeah/Auto-Cards), which is already included with Inner Self and can be enabled at any time.

---

## Main Features

| Feature | Description |
|:--------|:------------|
| **Segmented Memory** | Each NPC maintains their own private thoughts, separate from other characters |
| **Self-Organizing Thoughts** | Characters agentically revise, prune, and maintain their own mental state |
| **Zero Immersion Breaks** | Absolutely NO "please select continue" messages (!!!) |
| **Real-Time Brain Editor** | View or edit any NPC brain in the associated story card notes |
| **Name-Based Triggers** | Different NPCs coexist seamlessly, activating when mentioned in the story |
| **Visual Indicators** | See exactly which character is thinking at any given moment |
| **Universal Compatibility** | General-purpose design works across diverse character archetypes and scenarios |
| **Auto-Cards Integration** | Fully merged for comprehensive world-building (optional) |

---

## Permission

Inner Self is both free and open-source for anyone to use in their own scenarios or scripts, even published ones. You have my full permission to use, copy, or modify Inner Self. Please enjoy! ❤️

---

## Scenario Script Install Guide
1. Use the [AI Dungeon website](https://aidungeon.com/) on PC (or view as desktop if mobile-only)
2. [Create a new scenario](https://help.aidungeon.com/faq/what-are-scenarios) or edit an existing scenario
3. Open the `DETAILS` tab at the top while editing your scenario
4. Scroll to the bottom and select `EDIT SCRIPTS`
5. Select the `Input` tab on the left
6. Delete all code within said tab
7. Copy and paste the following code into your empty `Input` tab:
```javascript
// Your "Input" tab should look like this
InnerSelf("input");
const modifier = (text) => {
  // Any other input modifier scripts can go here
  return { text };
};
modifier(text);
```
8. Select the `Context` tab on the left
9. Delete all code within said tab
10. Copy and paste the following code into your empty `Context` tab:
```javascript
// Your "Context" tab should look like this
InnerSelf("context");
const modifier = (text) => {
  // Any other context modifier scripts can go here
  return { text, stop };
};
modifier(text);
```
11. Select the `Output` tab on the left
12. Delete all code within said tab
13. Copy and paste the following code into your empty `Output` tab:
```javascript
// Your "Output" tab should look like this
InnerSelf("output");
const modifier = (text) => {
  // Any other output modifier scripts can go here
  return { text };
};
modifier(text);
```
14. Select the `Library` tab on the left
15. Delete all code within said tab
16. Open the Library code (hyperlink below) in a new browser tab
- [Library code](./src/library.js)
17. Copy the *full* code from the page above and paste into your empty `Library` tab
18. Click the big yellow `SAVE` button in the top right corner

### *And you're done!*

All adventures played from your scenario will now include Inner Self (even existing adventures)

<sub>Remember to read the in-game config card!</sub>

---

## Gameplay Tips

- Read the in-game config card to learn how to easily add NPCs
- Set response length to 200 tokens if you notice short or empty outputs
- Enable scripts if you don't see a config card (homepage > settings > gameplay)
- Protect your mental health: Inner Self is intended to be a narrative experience only
- Plot components matter because the AI sees them when writing thoughts
- Different story models also tend to manage brains differently
- But avoid Atlas and Raven models for this one 😅

---

## For Creators

### Creator Control Panel
At the very top of the Inner Self `Library` script tab, you'll find optional settings with simple explanations. Modify these before publishing to customize your scenario's default experience.

### Preparing Scenario NPCs
To work on its own, provide Inner Self with the names of your scenario's most important NPCs. Inner Self will create a new brain card for each NPC you prepare, after their name appears in the story. (Kinda like story card triggers, if that makes sense!) Brains are created on-demand to avoid overwhelming players.

Creators provide Inner Self with scenario NPC names in one of two ways:

<details>
<summary><b>regular method (click to expand)</b></summary>

In the creator control panel near the top of your `Library` script tab:
```javascript
// List the first name of every scenario NPC whose brain should be simulated by Inner Self:
IMPORTANT_SCENARIO_CHARACTERS: ""
// (write a comma separated list of names inside the "" like so: "Leah, Lily, Lydia")
```
Simply list your NPC names inside the quotations. Then click the yellow `SAVE` button!

</details>

<details>
<summary><b>alternative method for mobile creators (click to expand)</b></summary>
  
Prefix regular AID story card titles with the `@` symbol so Inner Self knows which characters should think:
- Example card name: `@Leah`
- Remember to use simple first names here!
- This method is easier on mobile

</details>

### Custom NPC Brains
Inner Self uses the full context of your scenario to form minds that follow your creative vision. No extra effort required.

But if you want more advanced control:

<details>
<summary><b>initial thoughts (click to expand)</b></summary>
  
1. Transfer any NPC brain card from adventure to scenario
2. Leave the card entry completely empty
3. Replace the notes section with any valid string-valued JSON
4. Feel free to use an AI assistant to transform your concept into valid JSON by filling out the prompt below:
````markdown
# You are a JSON generator:
- Always reply with valid JSON only, no extra text
- Base your output on the instructions provided
- Do not include comments or explanations

## Overarching setting:
```
[Describe the setting of your scenario here!]
```

## Fictional character concept:
```
[Describe your character concept here!]
```

## Task instructions:
Your task is to transform the character concept into a JSON object
- The object should resemble a flat collection of key-value pairs
- All values are strings written from the character's inner 1st person PoV
- Values should be short single-sentence thoughts that capture core aspects
- Keys use distinct and descriptive lower snake_case syntax
- The object represents the character's identity of self
- Be creative when roleplaying as the character
- Respect the overarching setting
````

</details>

---

## Useful Links

<details>
<summary><b>(click to expand)</b></summary>

### Basic Demo Scenario
- [Inner Self](https://play.aidungeon.com/scenario/tsu1WMJXaaAZ/inner-self)

### Discussion Thread
- [Inner Self main thread](https://discordapp.com/channels/903327676884979802/1455232694379221165)
- [AI Dungeon official Discord server invite](https://discord.gg/MXNqpSbuZT) (required to access the first link)
- Please remember this is a personal passion project for me, something I do because I enjoy it, not as a job. Your kindness, patience, and love mean so much to me~ ❤️

</details>

---

## Changelog

<details>
<summary><b>(click to expand)</b></summary>

### 1.0.2
- Added config "Brain card notes store brains as JSON"
- When disabled, brain card notes use a simpler colon + newline delimited format instead of JSON
- Makes it much easier to manually edit NPC thoughts without accidentally breaking syntax
- Backward and forward compatible; both formats are safe during parsing
- Pull request by [dirtymined13](https://github.com/dirtymined13)

### 1.0.1
- Added config "Half thought chance for Do/Say/Story"
- Lets players decide if the thought formation chance should be reduced by half during Do/Say/Story turns
- This reduction was previously mandatory in v1.0.0, to help enforce player agency when using free models
- Pull request by [-Vinny-](https://play.aidungeon.com/profile/-Vinny-)

### 1.0.0
- Inner Self Released!

</details>

---

## Contributions

<details>
<summary><b>(click to expand)</b></summary>

- v1.0.1 → v1.0.2 by [dirtymined13](https://github.com/dirtymined13)
- v1.0.0 → v1.0.1 by [-Vinny-](https://play.aidungeon.com/profile/-Vinny-)

</details>

<p align="center"><i>Thank you so much for your curiosity and support~</i> ❤️</p>
<p align="center"><b>Inner Self v1.0.2</b> · Made with love by <a href="https://play.aidungeon.com/profile/LewdLeah">LewdLeah</a></p>
