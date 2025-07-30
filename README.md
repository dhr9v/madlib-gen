# 📝 Mad Libs Story Generator

This is a simple Python program that creates a fun Mad Libs story by replacing placeholders in a story template with user-provided words.

---

## 📂 File Structure

```
madlibs/
├── story.txt         # Text file containing the story template with <placeholders>
├── main.py        # Python script to generate the final story
```

---

## 📖 How It Works

1. The program reads a story template from `story.txt`.
2. It searches for all placeholders inside triangle brackets like `<noun>`, `<verb>`, `<adjective>`, etc.
3. It asks the user to input words to replace each of these placeholders.
4. It replaces the placeholders with the user's inputs and prints the final completed story.

---

## 🛠️ Setup & Running

### 1. Create the `story.txt` File

Make sure you have a `story.txt` file in the same directory.

Example content for `story.txt`:

```
Today I went to the zoo and saw a(n) <adjective> <animal> jumping up and down in its tree.  
It <verb_past_tense> <adverb> through the large tunnel that led to its <adjective2> <noun>.  
I got some peanuts and passed them through the cage to a gigantic gray <animal2> towering above my head.  
Feeding that animal made me hungry, so I went to get a <adjective3> scoop of ice cream.  
It filled my stomach. Afterwards, I had to <verb> <adverb2> to catch our bus.  
When I got home, I <verb_past_tense2> my mom for a <adjective4> day at the zoo.
```

### 2. Create the `main.py` File

Here's the Python script that generates the story:

```python
with open("story.txt", "r") as f:
    story = f.read()

words = set()
start_of_word = -1

target_start = "<"
target_end = ">"

for i, char in enumerate(story):
    if char == target_start:
        start_of_word = i

    if char == target_end and start_of_word != -1:
        word = story[start_of_word: i + 1]
        words.add(word)
        start_of_word = -1

answers = {}

for word in words:
    answer = input("Enter a word for " + word + ": ")
    answers[word] = answer

for word in words:
    story = story.replace(word, answers[word])

print(story)
```

### 3. Run the Script

In your terminal:

```bash
python main.py
```

---

## 📤 Output

After entering all words, you'll see the final completed story printed with your custom inputs!

---

## 🧠 Learnings

This project helps you understand:
- File reading in Python
- Sets and dictionaries
- String parsing and replacement
- User input interaction

---


