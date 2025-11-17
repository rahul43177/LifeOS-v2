## Read about 
1. non blocking i/o 
2. Parallelism vs Concurrency 
3. Event driven ? 
4. Threads 
5. 
## What is NodeJS 
Runtime environment for the JavaScript 

## Concurrency vs Parallelism
Lecture : https://www.youtube.com/watch?v=RlM9AfWf1WU
![[../../../attachments/01 - NodejS - concurrency.png]]
### Concurrency ≠ Parallelism

### Key Concepts
- **Concurrency**: Structure for dealing with multiple tasks (design pattern)
- **Parallelism**: Simultaneous execution of tasks (physical property)

### Quick Reference
| Type | Cores | Execution |
|------|-------|-----------|
| Sequential | 1 | One task completes before next starts |
| Concurrent | 1 | Tasks interleaved via context switching |
| Parallel | 2+ | Different tasks on different cores |
| Concurrent + Parallel | 2+ | Multiple interleaved tasks on multiple cores |

### Remember
- Concurrency = **about** dealing with many things at once
- Parallelism = **doing** many things at once
- You can have concurrency without parallelism
- Parallelism requires multiple CPU cores


## Where to use NodeJs ? 
![[../../../attachments/01 - NodeJS Fundamentals - where to use nodejs.png]]
We should never use NodeJs for CPU intensive applications. 

## How to start any node project
- First step is to initialise it with npm -> `npm init`
- Then if we want to install any dependency -> `npm install <dependecy_name>` or `npm i <dependency_name>`
- We are installing -> 
	1. express -> to create server 
	2. axios -> to send request
	3. bunyan -> authentication 

##### Dev Dependency 
Some dependency which are only required for local development , for example server restart -> `nodemon` which restarts the server automatically when we change something in the file or the code. 
So this is not required in the production , but on development environment only. 
So we can install dev dependency as well , which will not be pushed to the production. 
Using -> 
Full hand : `npm install <package_name> --save-dev`
Short hand : `npm install <package_name> -D`

##### Global Dependency 
We can install the dependency globally where it will be installed for all the npm repos 
using -> 
`npm install -g <package_name`



## Additive Changes vs Destructive Changes
![[../../../attachments/01 - NodeJS Fundamentals - changes.png]]

### Tilde (~) and Caret (^)
![[../../../attachments/01 - NodeJS Fundamentals.png]]

##### Quick Reference
| Symbol | Updates | Example | Accepts | Rejects |
|--------|---------|---------|---------|---------|
| `~` | PATCH only | `~1.2.3` | 1.2.4, 1.2.9 | 1.3.0, 2.0.0 |
| `^` | MINOR + PATCH | `^1.2.3` | 1.3.0, 1.9.9 | 2.0.0 |
| `*` | ALL | `*` | Any version | None |

##### package.json Examples
```json
{
  "dependencies": {
    "express": "^4.17.1",  // 4.17.x, 4.18.x OK, 5.0.0 NO
    "lodash": "~4.17.21",   // 4.17.x only, 4.18.0 NO
    "react": "*"            // Any version (risky!)
  }
}
```

##### Best Practices
- Use `^` for most dependencies (default npm behavior)
- Use `~` for critical dependencies needing stability
- Avoid `*` in production
- Use exact versions (no symbol) for maximum control: `"express": "4.17.1"`

##### Remember
- 🔒 Tilde (~) = Conservative (patch only)
- ⚖️ Caret (^) = Balanced (minor + patch)
- 🚀 Asterisk (*) = Aggressive (all updates)

## Package.json vs Package-lock.json

### Quick Comparison
| Aspect | package.json | package-lock.json |
|--------|--------------|-------------------|
| Purpose | Declare dependencies | Lock exact versions |
| Created by | Developer | npm automatically |
| Edit? | ✅ Yes | ❌ No (auto-generated) |
| Versions | Flexible (^, ~) | Exact (1.2.3) |
| Tracks | Direct deps | All deps + sub-deps |
| File size | Small | Large |

### Simple Analogy
**package.json**: "I need flour and milk"
**package-lock.json**: "I got Ashirvad atta (flour) 20kg bag and Nandini Orange full cream fat milk."

### Why Both?
```json
// package.json says:
"express": "^4.17.0"  // Any 4.x.x version >= 4.17.0

// package-lock.json records:
"express": "4.18.2"   // Exactly this version installed
```

### Key Commands
- `npm install` - Uses lock file if exists (fast, consistent)
- `npm update` - Updates packages per package.json rules
- `npm ci` - Installs directly from lock file (for CI/CD)

### Best Practices
✅ **DO**:
- Commit both files to git
- Run `npm ci` in production
- Delete node_modules + `npm install` if issues

❌ **DON'T**:
- Manually edit package-lock.json
- Delete package-lock.json (unless fixing conflicts)
- Ignore lock file in version control

### Remember
- package.json = **Wishlist** 📋
- package-lock.json = **Snapshot** 📸
- Together = **Reproducible builds** ✨

## Package-lock.json - Git & Hashes

### The Hash/Integrity
Each package has a SHA512 hash:
- Verifies package authenticity
- Prevents tampering/corruption
- Ensures exact same code everywhere

### Git Strategy: COMMIT IT! ✅

### Why Commit package-lock.json?
✅ **Team Consistency**: Everyone gets exact same versions
✅ **Faster Installs**: npm uses cached versions
✅ **Security**: Integrity hashes prevent tampering
✅ **CI/CD**: Reproducible builds in production
✅ **History**: Track exact dependency changes

### When NOT to Commit (Rare Cases)
❌ Building a library/package for npm
❌ Multiple package managers (yarn + npm)
❌ Experimental/learning projects

### Common Misconceptions
❌ "It's generated, so gitignore it" → **WRONG**
❌ "It's too large" → **Worth it for consistency**
❌ "It causes conflicts" → **Easy to resolve**

### Merge Conflict Resolution
```bash
# When package-lock.json conflicts:
git checkout --theirs package-lock.json  # or --ours
rm package-lock.json
npm install  # Regenerates it
git add package-lock.json
git commit
```

### The Rule
📋 **package.json** → Git ✅
🔒 **package-lock.json** → Git ✅
📦 **node_modules/** → Git ❌ (gitignore)

### Remember
- Hash = Security fingerprint
- Commit = Team consistency
- Ignore = Dependency hell 🔥

## Project - AirTribe File Manager 
![[../../../attachments/02 - Node.js - Rest API and Express - project description.png]]The requirements : 
![[../../../attachments/02 - Node.js - Rest API and Express - requirements project.png]]
It looks something like this : 
![[../../../attachments/02 - Node.js - Rest API and Express - looks like something.png]]