---
feature: ../../attachments/kunal_meeting_profile_card.png
---
### HTML Code 
```html 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profile Card</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .card {
            background-color: white;
            width: 350px;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .profile-pic {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background-color: #4a90e2;
            color: white;
            font-size: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 0 auto 20px;
        }

        .name {
            font-size: 24px;
            font-weight: bold;
            color: #333;
            margin-bottom: 5px;
        }

        .age {
            color: #666;
            margin-bottom: 15px;
        }

        .skills {
            color: #4a90e2;
            font-size: 14px;
            margin-bottom: 15px;
        }

        .bio {
            color: #555;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        .social-buttons {
            display: flex;
            justify-content: center;
            gap: 10px;
        }

        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            text-decoration: none;
            color: white;
        }

        .instagram {
            background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
        }

        .instagram:hover {
            opacity: 0.9;
        }
    </style>
</head>
<body>
    <div class="card">
        <div class="profile-pic">KT</div>
        <div class="name">Kunal Tiwari</div>
        <div class="age">20 years old • Male</div>
        <div class="skills">Skills: HTML and CSS</div>
        <div class="bio">Hi i am kunal and I learning web development</div>
        <div class="social-buttons">
            <a href="#" class="btn instagram">Instagram</a>
        </div>
    </div>
</body>
</html>
```

### It should look something like this : 
IT should look something like this : 
![[../../attachments/kunal_meeting_profile_card.png|300]]

