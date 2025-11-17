## 📋 **Day 1 To-Do List: HTTP Protocol Mastery**

_Monday, October 28, 2024_

---

### **🌅 Morning Session (9:00 AM - 12:00 PM)**

#### **Task 1: HTTP Foundation Study** ⏱️ 9:00-10:00 AM

- [ ] **Read:** MDN's "An overview of HTTP" ([link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview))
- [ ] **Create a diagram** showing:
    - Client makes request → DNS lookup → TCP handshake → HTTP request → Server processing → HTTP response
- [ ] **Take notes on:**
    - What happens when you type a URL in browser
    - Difference between HTTP/1.1 and HTTP/2
    - What is HTTPS and how TLS works (high level)
- [ ] **Quick Test:** Explain to yourself: "What happens when I hit Enter after typing google.com?"

#### **Task 2: HTTP Methods & Idempotency** ⏱️ 10:00-10:45 AM

- [ ] **Create a table** with columns: Method | Use Case | Idempotent? | Safe? | Example
- [ ] **Fill for each:** GET, POST, PUT, PATCH, DELETE, OPTIONS, HEAD
- [ ] **Critical Understanding:**
    - Why is GET safe but not POST?
    - Real scenario: Why would you choose PUT over PATCH?
    - What makes a method idempotent and why does it matter?
- [ ] **Interview Prep Note:** Write 2 sentences explaining idempotency (you WILL be asked this)

#### **☕ Break** ⏱️ 10:45-11:00 AM

#### **Task 3: Status Codes Deep Dive** ⏱️ 11:00 AM-12:00 PM

- [ ] **Create your personal status code reference:**
```
    2xx Success- 200 OK: Standard success- 201 Created: Resource created (POST success)- 204 No Content: Success but no body (DELETE success)3xx Redirection  - 301 Moved Permanently: SEO-friendly redirect- 302 Found: Temporary redirect- 304 Not Modified: Cache is still valid4xx Client Errors- 400 Bad Request: Malformed request- 401 Unauthorized: Need authentication- 403 Forbidden: Authenticated but not allowed- 404 Not Found: Resource doesn't exist- 429 Too Many Requests: Rate limited5xx Server Errors- 500 Internal Server Error: Generic server failure- 502 Bad Gateway: Upstream server error- 503 Service Unavailable: Server overloaded/maintenance
```
    
- [ ] **Memory Trick:** Create mnemonics or stories for each category
- [ ] **Real Examples:** Find one real-world API that returns each status code

---

### **Lunch Break (12:00 PM - 1:00 PM)**

---

### **Afternoon Session (1:00 PM - 4:00 PM)**

#### **Task 4: Browser DevTools Mastery**  1:00-2:00 PM

- [ ] **Setup:**
    - Open Chrome/Firefox
    - Open DevTools (F12) → Network Tab
    - Check "Preserve log" and "Disable cache"
- [ ] **Analyze these specific sites:**
    1. **github.com** - Observe:
        - [ ] How many requests for homepage?
        - [ ] What headers does GitHub send?
        - [ ] Find the main HTML, CSS, JS files
        - [ ] Check Cookie headers
    2. api.github.com/users/torvalds - Note:
        - [ ] Response headers
        - [ ] Rate limit headers
        - [ ] Content-Type
    3. **stackoverflow.com** - Look for:
        - [ ] CORS headers
        - [ ] Cache-Control headers
        - [ ] Any 304 responses after refresh
    4. **Your favorite website** - Document:
        - [ ] Total load time
        - [ ] Largest request
        - [ ] Any failed requests (4xx/5xx)
- [ ] **Create a document:** "HTTP in the Wild - My Findings" with screenshots
    

#### **Task 5: Hands-on with cURL & Postman**  2:00-3:00 PM

- [ ] **Install Tools:**
    
    - [ ] Verify cURL: `curl --version`
    - [ ] Install Postman or Insomnia
- [ ] **Complete these cURL challenges:**
    
    ```bash
    # Challenge 1: GET request with custom header
    curl -H "Accept: application/json" https://api.github.com
    
    # Challenge 2: POST with JSON data
    curl -X POST https://jsonplaceholder.typicode.com/posts \
      -H "Content-Type: application/json" \
      -d '{"title":"My first post","body":"Learning HTTP!","userId":1}'
    
    # Challenge 3: See only headers
    curl -I https://www.google.com
    
    # Challenge 4: Follow redirects
    curl -L http://github.com
    
    # Challenge 5: Download with progress bar
    curl -O --progress-bar https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf
    ```
    
- [ ] **In Postman:**
    
    - [ ] Recreate all 5 cURL requests above
    - [ ] Save as a collection named "HTTP Basics"
    - [ ] Test with different headers and observe changes

#### **Task 6: Build Mini HTTP Client** ⏱️ 3:00-4:00 PM

- [ ] **Create file:** `http-explorer.js`
- [ ] **Code this Node.js script:**
    
    ```javascript
    const https = require('https');// Task: Make a GET request without using any librariesconst options = {  hostname: 'api.github.com',  path: '/users/nodejs',  method: 'GET',  headers: {    'User-Agent': 'My-HTTP-Explorer'  }};const req = https.request(options, (res) => {  console.log(`STATUS: ${res.statusCode}`);  console.log(`HEADERS: ${JSON.stringify(res.headers, null, 2)}`);    let data = '';  res.on('data', (chunk) => data += chunk);  res.on('end', () => {    console.log('BODY:', JSON.parse(data));  });});req.on('error', (e) => console.error(e));req.end();
    ```
    
- [ ] **Extend it to:**
    - [ ] Accept URL as command line argument
    - [ ] Show response time
    - [ ] Pretty-print JSON responses

---

### **🌆 Evening Session (5:00 PM - 7:00 PM)**

#### **Task 7: DSA Foundation - Arrays** ⏱️ 5:00-6:30 PM

- [ ] **LeetCode Problem 1: Two Sum** (#1)
    
    - [ ] First attempt without looking at solution
    - [ ] Understand brute force O(n²) approach
    - [ ] Learn HashMap O(n) optimization
    - [ ] Write both solutions with comments
    - [ ] Note: This is THE most common interview question
- [ ] **LeetCode Problem 2: Best Time to Buy and Sell Stock** (#121)
    
    - [ ] Identify the pattern (track minimum, calculate profit)
    - [ ] Draw the logic on paper first
    - [ ] Code the solution
    - [ ] Time: O(n), Space: O(1) - understand why
- [ ] **LeetCode Problem 3: Contains Duplicate** (#217)
    
    - [ ] Try Set approach
    - [ ] Try sorting approach
    - [ ] Compare time/space tradeoffs
    - [ ] Which is better and why?
- [ ] **Document patterns:** Create `dsa-patterns.md`
    
    ```markdown
    ## Array Patterns Day 1
    
    ### Pattern 1: HashMap for lookups
    - Used when: Need to find pairs/complements
    - Example: Two Sum
    - Complexity: O(n) time, O(n) space
    
    ### Pattern 2: Single Pass with variable tracking
    - Used when: Finding min/max in one pass
    - Example: Best Time to Buy Stock
    - Complexity: O(n) time, O(1) space
    ```
    

#### **Task 8: Day 1 Review & Setup Tomorrow** ⏱️ 6:30-7:00 PM

- [ ] **Quick Reviews:**
    
    - [ ] Can you explain HTTP request lifecycle?
    - [ ] What status code for successful DELETE? (204)
    - [ ] What's idempotency? Give example
    - [ ] Solve Two Sum mentally in 30 seconds
- [ ] **Prepare for tomorrow:**
    
    - [ ] Install Node.js LTS version
    - [ ] `npm init -y` in a folder called `backend-month1`
    - [ ] Install: `npm install express nodemon`
    - [ ] Create `server.js` with basic hello world
- [ ] **Log your progress:**
    
    ```markdown
    ## Day 1 Completed ✅
    - Understood: HTTP lifecycle, methods, status codes
    - Practiced: DevTools, cURL, Postman
    - Solved: 3 LeetCode problems
    - Tomorrow: Build first Express server
    ```
    

---

### **💯 Day 1 Success Checklist:**

- [ ] Can explain what happens when you type a URL
- [ ] Have personal status code cheat sheet
- [ ] Analyzed 5+ real HTTP requests in DevTools
- [ ] Executed 5 cURL commands successfully
- [ ] Solved 3 LeetCode problems with complexity analysis
- [ ] Created study notes for future reference

---

### **🎯 Bonus (if you finish early):**

- [ ] Read about HTTP headers: Authorization, Content-Type, Accept
- [ ] Try one more LeetCode Easy: "Move Zeroes" (#283)
- [ ] Watch: [How Does the Internet Work in 5 Minutes](https://www.youtube.com/watch?v=7_LPdttKXPc)

---

**Remember:** Don't just read about HTTP - inspect it, break it, play with it. Every senior engineer has spent hours in DevTools. Today, you join that club!

**End of Day Reflection Question:** _"If you had to explain to a friend why some websites load faster than others based on what you learned today about HTTP, what would you say?"_

Good luck! Check off each item as you complete it. The satisfaction of checking boxes will keep you motivated!




