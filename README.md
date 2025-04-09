<!DOCTYPE html>
<html>
<head>
  <title>Your Name | GitHub Profile</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;700&display=swap');
    body {
      font-family: 'Roboto Mono', monospace;
      background: #0d1117;
      color: #c9d1d9;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 800px;
      margin: 0 auto;
      padding: 2rem;
    }
    .header {
      text-align: center;
      margin-bottom: 2rem;
    }
    .avatar {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      border: 5px solid #38C172;
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0% { box-shadow: 0 0 0 0 rgba(56, 193, 114, 0.7); }
      70% { box-shadow: 0 0 0 15px rgba(56, 193, 114, 0); }
      100% { box-shadow: 0 0 0 0 rgba(56, 193, 114, 0); }
    }
    .social-icons {
      display: flex;
      justify-content: center;
      gap: 1rem;
      margin: 1rem 0;
    }
    .social-icon {
      transition: transform 0.3s;
    }
    .social-icon:hover {
      transform: scale(1.2);
    }
    .stats {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 1rem;
      margin: 2rem 0;
    }
    .stat-card {
      background: #161b22;
      padding: 1rem;
      border-radius: 6px;
      text-align: center;
      transition: transform 0.3s;
    }
    .stat-card:hover {
      transform: translateY(-5px);
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <img src="https://avatars.githubusercontent.com/u/YOUR_GITHUB_ID?v=4" alt="Avatar" class="avatar">
      <h1>Your Name</h1>
      <p>Passionate Developer | Open Source Enthusiast</p>
      <div class="social-icons">
        <a href="https://github.com/yourusername" target="_blank">
          <img src="https://img.icons8.com/fluent/48/000000/github.png" width="32" class="social-icon"/>
        </a>
        <a href="https://linkedin.com/in/yourprofile" target="_blank">
          <img src="https://img.icons8.com/fluent/48/000000/linkedin.png" width="32" class="social-icon"/>
        </a>
        <a href="https://twitter.com/yourhandle" target="_blank">
          <img src="https://img.icons8.com/fluent/48/000000/twitter.png" width="32" class="social-icon"/>
        </a>
      </div>
    </div>

    <div class="stats">
      <div class="stat-card">
        <h3>Repositories</h3>
        <p id="repo-count">Loading...</p>
      </div>
      <div class="stat-card">
        <h3>Followers</h3>
        <p id="followers-count">Loading...</p>
      </div>
      <div class="stat-card">
        <h3>Stars</h3>
        <p id="stars-count">Loading...</p>
      </div>
    </div>

    <h2>🚀 My Tech Stack</h2>
    <div id="tech-stack">
      <!-- Will be populated by JavaScript -->
    </div>
  </div>

  <script>
    // Fetch GitHub stats
    async function fetchGitHubStats() {
      try {
        const response = await fetch('https://api.github.com/users/yourusername');
        const data = await response.json();
        
        document.getElementById('repo-count').textContent = data.public_repos;
        document.getElementById('followers-count').textContent = data.followers;
        
        // Fetch starred repos count
        const starsResponse = await fetch('https://api.github.com/users/yourusername/starred');
        const starsData = await starsResponse.json();
        document.getElementById('stars-count').textContent = starsData.length;
      } catch (error) {
        console.error('Error fetching GitHub data:', error);
      }
    }
    
    // Tech stack icons
    const techStack = [
      { name: 'C++', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg' },
      { name: 'Python', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg' },
      { name: 'JavaScript', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg' },
      { name: 'Docker', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg' },
      { name: 'Git', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg' },
      { name: 'Linux', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg' }
    ];
    
    function renderTechStack() {
      const container = document.getElementById('tech-stack');
      container.innerHTML = techStack.map(tech => `
        <div style="display: inline-block; text-align: center; margin: 10px;">
          <img src="${tech.icon}" width="48" height="48" alt="${tech.name}" />
          <p>${tech.name}</p>
        </div>
      `).join('');
    }
    
    // Initialize
    fetchGitHubStats();
    renderTechStack();
  </script>
</body>
</html>
