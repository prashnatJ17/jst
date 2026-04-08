<!DOCTYPE html>
<html lang="en">
<head>
    <title>JS Exam Results</title>
    <style>
        body { font-family: sans-serif; padding: 20px; line-height: 1.6; background: #f4f4f4; }
        .task { background: white; padding: 15px; margin-bottom: 10px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        h3 { color: #2c3e50; margin-top: 0; }
        pre { background: #272822; color: #f8f8f2; padding: 10px; border-radius: 5px; overflow-x: auto; }
    </style>
</head>
<body>
    <h1>JavaScript Exam Output</h1>
    <div id="output"></div>

    <script>
        const logToScreen = (task, data) => {
            const div = document.createElement('div');
            div.className = 'task';
            div.innerHTML = `<h3>Task ${task}</h3><pre>${JSON.stringify(data, null, 2)}</pre>`;
            document.getElementById('output').appendChild(div);
        };

        // --- Task 1 ---
        const t1 = (s) => s.split(' ').map(w => w.split('').reverse().join('')).join(' ');
        logToScreen(1, t1("Hello World From Wisdom Sprouts"));

        // --- Task 2 ---
        const t2 = (t) => {
            const res = {};
            t.toLowerCase().replace(/[^\w\s]/g, '').split(/\s+/).forEach(w => { if(w) res[w] = (res[w]||0)+1; });
            return res;
        };
        logToScreen(2, t2("Learning JavaScript is fun! Fun and easy."));

        // --- Task 3 ---
        const users = [{name:"Alice", age:22}, {name:"Bob", age:17}, {name:"Charlie", age:19}];
        logToScreen(3, users.filter(u => u.age > 18));

        // --- Task 4 ---
        const products = [{name:"Keyboard", price:499}, {name:"Monitor", price:8999}, {name:"Mouse", price:299}];
        logToScreen(4, [...products].sort((a,b) => a.price - b.price));

        // --- Task 5 ---
        const t5 = (t) => t.toLowerCase().replace(/[^\w\s]/g, '').trim().split(/\s+/).join('-');
        logToScreen(5, t5("Learn JavaScript in 30 Days!"));

        // --- Task 6 ---
        const t6 = (arr) => arr.reduce((acc, w) => {
            const l = w.length;
            acc[l] = acc[l] || [];
            acc[l].push(w);
            return acc;
        }, {});
        logToScreen(6, t6(["dog", "apple", "sun", "table", "cat", "pie"]));

        // --- Task 8 (Deep Copy) ---
        const obj = { name: "John", address: { city: "New York" } };
        const copy = JSON.parse(JSON.stringify(obj));
        logToScreen(8, { original: obj, isCopySuccessful: copy !== obj });

        // --- Task 10 (Calculator) ---
        const t10 = (exp) => { try { return eval(exp); } catch(e) { return "Error"; } };
        logToScreen(10, { expression: "3 + 5 * 2 - 4 / 2", result: t10("3 + 5 * 2 - 4 / 2") });

    </script>
</body>
</html>
