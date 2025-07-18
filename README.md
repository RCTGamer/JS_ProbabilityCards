# Problem Content Management

This system allows you to easily edit problem content by modifying a single text file per problem instead of HTML/JavaScript code.

## File Structure

Each problem has its own folder in `problems/data/` with a single content file:

```
problems/data/
├── ace-clubs/
│   └── content.txt         # All problem content in one file
├── two-clubs/
│   └── content.txt         # All problem content in one file
└── three-clubs/
    └── content.txt         # All problem content in one file
```

## File Format

Each `content.txt` file contains all the problem information organized in sections using square brackets:

```
[CONFIG]
title: A♣
difficulty: Easy
answers: a)=7, b)=14

[PROBLEM]
Problem Title Here

Problem description goes here.

a) First part of the question
b) Second part of the question

[HINTS]
First hint here.

Second hint here.

[SOLUTION]
Step 1 Title:
Explanation for step 1
Mathematical formulas using $LaTeX$ syntax

---

Step 2 Title:
Explanation for step 2
More $LaTeX$ formulas

[TOPICS]
Topic 1, Topic 2, Topic 3, Topic 4
```

## Section Details

### [CONFIG] Section
Contains basic problem configuration:
- **title**: The display title (can include symbols like ♣, ♠, ♥, ♦)
- **difficulty**: Easy, Medium, or Hard
- **answers**: Format as `label=value` separated by commas. For single answers, use `=value`

### [PROBLEM] Section
Contains the complete problem statement:
- First line is the problem title
- Following lines are the description
- Parts starting with a), b), c) etc. are automatically formatted

### [HINTS] Section
Contains hints separated by blank lines

### [SOLUTION] Section
Contains step-by-step solution. Use `---` to separate different solution steps.

### [TOPICS] Section
Contains comma-separated related topics/tags

## LaTeX Support

You can use LaTeX mathematical notation in any section:
- Inline math: `$x^2 + y^2 = z^2$`
- Display math: `$$E[X] = \sum_{i} x_i P(x_i)$$`
- Fractions: `$\frac{1}{2}$`
- Greek letters: `$\alpha, \beta, \gamma$`

## Adding New Problems

1. Create a new folder in `problems/data/` with your problem name
2. Create a `content.txt` file in that folder with all sections
3. Add the problem name to the `problemOrder` array in `problem-template.html`
4. Update the link in `expectation.html` to point to your new problem

## Example Complete File

```
[CONFIG]
title: K♠
difficulty: Hard
answers: a)=0.25, b)=12.5

[PROBLEM]
Advanced Card Probability

You have a modified deck with special rules.

a) What is the probability of drawing a face card?
b) What is the expected value when drawing with replacement?

[HINTS]
Consider the modified probabilities.

Use the definition of expected value.

[SOLUTION]
Part a) Calculating probability:
There are 12 face cards in a standard deck.
$P(\text{face card}) = \frac{12}{52} = \frac{3}{13} \approx 0.23$

---

Part b) Expected value calculation:
$E[X] = \sum_{i} x_i \cdot P(x_i)$
Calculate for each card value and sum.

[TOPICS]
Probability, Expected Value, Card Games, Modified Distributions
```

## Tips

- Keep each section clearly separated
- Use meaningful section headers in square brackets
- Test your LaTeX formulas to ensure they render correctly
- Use blank lines to improve readability within sections
- Keep problem folder names lowercase with hyphens for spaces
