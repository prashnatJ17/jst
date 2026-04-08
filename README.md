# jst
/**
 * JAVASCRIPT PRACTICAL EXAM - ALL SOLUTIONS
 */

// --- Task 1: Reverse each word in a sentence ---
const reverseWords = (sentence) => {
  return sentence.split(' ')
    .map(word => word.split('').reverse().join(''))
    .join(' ');
};

// --- Task 2: Word frequency counter ---
const getWordFrequency = (text) => {
  const words = text.toLowerCase().replace(/[^\w\s]/g, '').split(/\s+/);
  return words.reduce((acc, word) => {
    if (word) acc[word] = (acc[word] || 0) + 1;
    return acc;
  }, {});
};

// --- Task 3: Filter users by age (> 18) ---
const filterAdults = (users) => users.filter(u => u.age > 18);

// --- Task 4: Sort products by price ascending ---
const sortProducts = (products) => [...products].sort((a, b) => a.price - b.price);

// --- Task 5: URL Slug Generator ---
const createSlug = (title) => {
  return title.toLowerCase()
    .replace(/[^\w\s]/g, '')
    .trim()
    .replace(/\s+/g, '-');
};

// --- Task 6: Group words by length ---
const groupByLength = (words) => {
  return words.reduce((acc, word) => {
    const len = word.length;
    acc[len] = acc[len] || [];
    acc[len].push(word);
    return acc;
  }, {});
};

// --- Task 7: Debounce utility ---
function debounce(func, delay) {
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => func(...args), delay);
  };
}

// --- Task 8: Deep Copy Object ---
// (Note: structuredClone is the modern standard, JSON is the classic fallback)
const deepCopy = (obj) => JSON.parse(JSON.stringify(obj));

// --- Task 9: Sequential Async Tasks ---
async function runSequentialTasks() {
  const taskIds = ['A', 'B', 'C'];
  for (const id of taskIds) {
    const delay = Math.random() * 1500 + 500; // 0.5 to 2 seconds
    await new Promise(res => setTimeout(res, delay));
    console.log(`Task ${id} completed`);
  }
  console.log("All tasks completed");
}

// --- Task 10: Simple Calculator with Precedence ---
const calculate = (expr) => {
  try {
    return Function(`"use strict"; return (${expr})`)();
  } catch {
    return "Error";
  }
};

/** * TEST CASES (Optional)
 */
console.log("Task 1:", reverseWords("Hello World"));
console.log("Task 2:", getWordFrequency("JavaScript is fun! Fun..."));
console.log("Task 5:", createSlug("Learn JavaScript in 30 Days!"));
console.log("Task 10:", calculate("3 + 5 * 2 - 4 / 2"));
runSequentialTasks();
