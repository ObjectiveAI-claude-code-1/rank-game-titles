# rank-game-titles

Ranks candidate video game titles from most fitting to least fitting, given a description of the game. A video game title is a player's first encounter with a world they haven't yet entered — it sets expectations, sparks curiosity, and shapes how a game is discovered, perceived, and remembered. This function brings structure and rigor to the difficult task of choosing the right name.

## Input

The function accepts an object with two required fields:

| Field | Type | Description |
|---|---|---|
| `game_description` | `string` | A description of the video game, including its themes, mechanics, setting, tone, and narrative. This can range from a brief pitch to a detailed design overview. |
| `titles` | `string[]` | A list of candidate titles to rank (minimum 2). These might come from brainstorming sessions, marketing teams, or AI-generated suggestions. |

### Example Input

```json
{
  "game_description": "A single-player narrative adventure about a retired deep-sea diver returning to the ocean to search for a lost colleague. The game explores themes of grief, memory, and letting go, set against a hauntingly beautiful underwater world. The tone is melancholic but ultimately hopeful, with slow-paced exploration and environmental storytelling.",
  "titles": [
    "Abyssal",
    "The Last Depth",
    "Sunken Memories",
    "Ocean Hero Extreme",
    "Pressure"
  ]
}
```

## Output

A probability distribution (array of numbers summing to 1) over the input titles, where higher values indicate stronger, more fitting titles. The output array preserves the same ordering as the input `titles` array.

## What It Evaluates

The function evaluates each candidate title across three core dimensions, then combines the results into a unified ranking. No single dimension is sufficient on its own — the best title is one that performs well across all three.

### 1. Thematic Relevance

Assessed by [{{ .Task0 }}](https://github.com/{{ .Owner }}/{{ .Task0 }}).

Evaluates how well each title connects to the game's core themes, subject matter, setting, and central conceit. A strong title should feel like it naturally belongs to the game — not in a bluntly literal way, but in a way that captures the essence of what the game is about. A player who finishes the game should be able to look back at the title and feel it was the right name all along. Titles that are clever but thematically disconnected rank lower.

### 2. Tonal Resonance

Assessed by [{{ .Task1 }}](https://github.com/{{ .Owner }}/{{ .Task1 }}).

Evaluates how well each title matches the emotional register, mood, and feel of the game. Two games might share a theme — say, survival — but feel entirely different: one bleak and harrowing, the other lighthearted and comedic. The title must sound the way the game feels. Titles that create tonal dissonance — a whimsical name for a grim game, or a somber name for a playful one — rank lower.

### 3. Memorability

Assessed by [{{ .Task2 }}](https://github.com/{{ .Owner }}/{{ .Task2 }}).

Scores each title individually on distinctiveness, compactness, rhythm, phonetic appeal, and ease of recall. A great title sticks in the mind, is easy to share in conversation, and is easy to search for. Overly generic titles disappear into marketplace noise. Overly long or cumbersome titles resist being spoken aloud. The best titles are distinctive without being alienating, compact without being vague.

## Use Cases

- **Indie developers** brainstorming names who want a structured evaluation of which options best represent their game.
- **Studios** narrowing down finalists for a game reveal, pressure-testing a shortlist against the game's identity.
- **Publishers** reviewing a portfolio of upcoming releases to ensure each title communicates the right idea to its audience.
- **Marketing teams** validating that a proposed title aligns with the game's themes and tone before committing to branding.
- **Game jam participants** quickly choosing the strongest title from a pool of last-minute ideas.

## Sub-Functions

| Task | Name | Type | Purpose |
|---|---|---|---|
| 0 | [{{ .Task0 }}](https://github.com/{{ .Owner }}/{{ .Task0 }}) | Vector | Ranks titles by thematic relevance to the game |
| 1 | [{{ .Task1 }}](https://github.com/{{ .Owner }}/{{ .Task1 }}) | Vector | Ranks titles by tonal resonance with the game |
| 2 | [{{ .Task2 }}](https://github.com/{{ .Owner }}/{{ .Task2 }}) | Scalar (mapped) | Scores each title's memorability independently |
