<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Al Yamamah Project Hub</title>
    <style>
        :root {
            --yu-blue: #003366; /* University blue */
            --yu-gold: #CC9900; /* University gold */
        }

        body {
            font-family: 'Segoe UI', sans-serif;
            margin: 0;
            background: #f8f9fa;
        }

        .navbar {
            background: var(--yu-blue);
            padding: 1rem;
            color: white;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .navbar a {
            color: white;
            text-decoration: none;
            margin-right: 2rem;
        }

        .container {
            max-width: 1200px;
            margin: 80px auto 100px;
            padding: 20px;
        }

        .project-card {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin: 20px 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .project-interactions {
            display: flex;
            gap: 15px;
            margin-top: 15px;
        }

        .like-btn, .comment-btn {
            padding: 5px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            background: var(--yu-gold);
            color: white;
        }

        .search-bar {
            width: 100%;
            padding: 10px;
            margin: 20px 0;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        form input, form textarea {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin: 5px 0;
        }

        form button {
            background: var(--yu-blue);
            color: white;
            padding: 10px 25px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        mark {
            background-color: #fff3cd;
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <a href="#home">Home</a>
        <a href="#projects">Projects</a>
        <a href="#submit">Submit Project</a>
        <a href="#contact">Contact</a>
        <a href="#login" style="float: right;">Login</a>
    </nav>
<div class="MIS project">
    <h2>Your Projects HUB</h2>
    <p>By: Faris AlShashaa, Hussam Alsaif, Saad, Faisal, abdullaziz</p>
    <p>Gathering students projects...</p>
    <div class="project-interactions">
        <button class="like-btn" onclick="incrementLikes(this)">👍 0</button>
        <button class="comment-btn" onclick="showComments()">💬 0 Comments</button>
        <div class="rating">⭐ 5/5</div>
    </div>
</div>
    <div class="container" id="home">
        <input type="text" class="search-bar" placeholder="Search projects...">

        <!-- Project Showcase -->
        <div class="project-card">
            <h2>AI-Powered Campus Navigation</h2>
            <p>By: MIS Team</p>
            <p>A machine learning project to optimize campus routes...</p>
            <div class="project-interactions">
                <button class="like-btn" onclick="incrementLikes(this)">👍 12</button>
                <button class="comment-btn" onclick="showComments()">💬 5 Comments</button>
                <div class="rating">⭐ 4.5/5</div>
            </div>
        </div>

        <div class="project-card">
            <h2>Smart Waste Management System</h2>
            <p>By: Engineering Team</p>
            <p>IoT-based solution for campus waste optimization...</p>
            <div class="project-interactions">
                <button class="like-btn" onclick="incrementLikes(this)">👍 8</button>
                <button class="comment-btn" onclick="showComments()">💬 2 Comments</button>
                <div class="rating">⭐ 4.2/5</div>
            </div>
        </div>
    </div>

    <!-- Contact Section -->
    <section class="container" id="contact" style="display: none;">
        <div class="project-card">
            <h2>Contact Administrators</h2>
           <form
  action="https://formspree.io/f/mrbpebyb"
  method="POST"
>
  <label>
    Your email:
    <input type="202111166@yu.edu.sa" name="faris">
  </label>
  <label>
    Your message:
    <textarea name="faris"></textarea>
  </label>
  <!-- your other form fields go here -->
  <button type="submit">Send</button>
</form>
        </div>
    </section>

    <!-- ER Diagram Documentation (Hidden) -->
    <div style="display: none;">
        <!--
        ER Diagram Structure:
        [User]-(1:M)-[Project]
        [User]-(1:M)-[Comment]
        [User]-(1:M)-[Like]
        [User]-(1:M)-[Notification]
        [Project]-(1:M)-[Comment]
        [Project]-(1:M)-[Like]
        -->
    </div>

    <script>
        // Like functionality
        function incrementLikes(button) {
            let count = parseInt(button.innerText.match(/\d+/)[0]);
            button.innerText = `👍 ${count + 1}`;
        }

        // Comment mockup
        function showComments() {
            alert("Comments feature coming soon!");
        }

        // Search functionality
        document.querySelector('.search-bar').addEventListener('input', function(e) {
            const searchTerm = e.target.value.toLowerCase();
            document.querySelectorAll('.project-card').forEach(card => {
                const text = card.innerText.toLowerCase();
                card.style.display = text.includes(searchTerm) ? 'block' : 'none';
                
                // Highlight matches
                const title = card.querySelector('h2');
                title.innerHTML = title.innerText.replace(
                    new RegExp(searchTerm, 'gi'), 
                    match => `<mark>${match}</mark>`
                );
            });
        });

        // Form submission
        document.querySelector('#contact form')?.addEventListener('submit', async (e) => {
            e.preventDefault();
            const form = e.target;
            const response = await fetch(form.action, {
                method: 'POST',
                body: new FormData(form),
                headers: { 'Accept': 'application/json' }
            });
            
            if (response.ok) {
                alert('Message sent successfully!');
                form.reset();
            } else {
                alert('Error sending message. Please try again.');
            }
        });
    </script>
</body>
</html>
