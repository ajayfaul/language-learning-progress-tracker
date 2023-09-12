# **Language Learning Progress Tracker**

![image.png](https://res.craft.do/user/full/55fbf0f6-b802-cfae-f9ae-874a9e8e032d/doc/83440545-b64f-433a-b558-bf80861f1661/6bb1fe31-c7ec-4a26-831b-d6ee1c46b346)

---

In our increasingly globalized world, the ability to communicate in multiple languages has become a valuable skill. Language learning is a journey, and tracking your progress is a crucial aspect of mastering a new language. To address this need,  I have developed the "Language Learning Progress Tracker," a user-friendly web application that empowers language learners to monitor their daily study efforts and proficiency levels. This project created for bounty on Stackup site.

### Project Overview

This project is using HTML, CSS, and Javascript, here are the overview  and walkthrough of the project:

1. **Language Selection:** To begin, select your target language from the dropdown menu. We offer a wide range of options, from commonly studied languages like Spanish and French to less common ones like Vietnamese or Indonesian. If your language isn't listed, simply choose "Others."

```javascript
<div id="language-selector">
        <label for="language">Select a Language:</label>
        <select id="language">
          <option value="spanish">Spanish</option>
          <option value="french">French</option>
          <!-- ... other language options ... -->
          <option value="indonesia">Indonesian</option>
          <option value="others">Others</option>
        </select>
      </div>
```

2. **Daily Study Hours:** Input the amount of time you dedicate to studying your chosen language every day. This helps us keep track of your daily efforts and progress.

```javascript
<label for="study-hours">Daily Study Hours:</label>
        <input type="number" id="study-hours" />
```

3. **Proficiency Level:** Select your current proficiency level from the dropdown. Whether you're just starting ("No Proficiency") or already fluent ("Native/Bilingual Proficiency"), we cater to learners of all levels.

```javascript
<label for="proficiency">Proficiency Level:</label>
        <select id="proficiency">
          <option value="0">0. No Proficiency</option>
          <option value="1">1. Elementary Proficiency</option>
          <option value="2">2. Limited Working Proficiency</option>
          <option value="3">3. Professional Working Proficiency</option>
          <option value="4">4. Full Professional Proficiency</option>
          <option value="5">5. Native / Bilingual Proficiency</option>
        </select>
```

4. **Adding Progress:** Click the "Add Progress" button to record your study session. You can repeat this step daily to continuously update your language learning journey.

```javascript
<button id="add-progress">Add Progress</button>
```

### **Tracking Progress with Classes**

Behind the scenes, we use object-oriented programming principles, specifically JavaScript classes, to structure and manage the data. The "Language" class represents the languages being learned, with properties like "name," "studyHours," and "proficiencyLevels." When you add progress, a new instance of the "Language" class is created based on your language selection, and your study hours and proficiency level are added to the corresponding arrays.

```javascript
// Language class to represent languages being learned
class Language {
    constructor(name) {
        this.name = name;
        this.studyHours = [];
        this.proficiencyLevels = [];
    }

    addProgress(hours, proficiency) {
        this.studyHours.push(hours);
        this.proficiencyLevels.push(proficiency);
    }
}
```

### **Utilizing Switch Statements**

Switch statements are employed to manage language selection. We use a switch statement to handle different language cases. If you select a language, the switch statement ensures that the data is stored in the appropriate language object.

```javascript
const languages = {};

document.getElementById("add-progress").addEventListener("click", function () {
    const selectedLanguage = document.getElementById("language").value;
    const studyHours = parseFloat(document.getElementById("study-hours").value);
    const proficiency = parseFloat(document.getElementById("proficiency").value);

    try {
        switch (selectedLanguage) {
            case "spanish":
            case "french":
            case "japanese":
            case "korean":
            case "chinese":
            case "german":
            case "italian":
            case "portuguese":
            case "russian":
            case "turkish":
            case "vietnamese":
            case "indonesia":
            case "others":
                if (isNaN(studyHours) || isNaN(proficiency)) {
                    throw new Error("Please enter valid study hours and proficiency level.");
                }

                if (!languages[selectedLanguage]) {
                    languages[selectedLanguage] = new Language(selectedLanguage);
                }

                languages[selectedLanguage].addProgress(studyHours, proficiency);
                updateLanguageProgress();
                break;

            default:
                throw new Error("Invalid language selection.");
        }
    } catch (error) {
        alert("Error: " + error.message);
    } finally {
        document.getElementById("study-hours").value = "";
        document.getElementById("proficiency").value = "0"; // Set proficiency to default "No Proficiency"
    }
});
```

### **Handling Errors with Try-Catch-Finally**

Robust error handling is crucial for a seamless user experience. Our application incorporates try-catch statements to detect and handle errors gracefully. If you input invalid study hours or proficiency levels, the try-catch block will catch these errors and display a user-friendly alert message. This ensures that you receive immediate feedback and can correct any mistakes.

```javascript
try {
    // ...
} catch (error) {
    alert("Error: " + error.message);
} finally {
    // ...
}
```

### **Visualizing Progress**

After you've added your progress, the Language Learning Progress Tracker provides a visual representation of your journey. Your average study hours and proficiency levels are displayed for each selected language in a clear and organized manner.

```javascript
function updateLanguageProgress() {
    const languageProgressDiv = document.getElementById("language-progress");
    languageProgressDiv.innerHTML = "";

    for (const lang in languages) {
        const language = languages[lang];
        const avgHours = language.studyHours.reduce((acc, val) => acc + val, 0) / language.studyHours.length;
        const avgProficiency = language.proficiencyLevels.reduce((acc, val) => acc + val, 0) / language.proficiencyLevels.length;

        const languageDiv = document.createElement("div");
        languageDiv.classList.add("language-progress");
        languageDiv.innerHTML = `
        <h2>${language.name}</h2>
        <p>Average Study Hours: ${avgHours}</p>
        <p>Average Proficiency: ${avgProficiency}</p>
        `;

        languageProgressDiv.appendChild(languageDiv);
    }
}
```

> The Language Learning Progress Tracker is more than just a tool; it's a partner in your language learning adventure. With a user-friendly interface and robust programming principles like classes, switch statements, and try-catch-finally, it simplifies progress tracking and encourages you to stay dedicated to your language learning goals.

---

## Link to the website:

- Deployed site:

