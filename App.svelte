<!-- App.svelte -->
<script>
  let isMenuOpen = false;
  
  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
    const leftMenu = document.querySelector('.left-menu');
    const topBar = document.querySelector('.top-bar');
    leftMenu.classList.toggle('open');
    topBar.classList.toggle('open');
  }
</script>
  
<style>
  /* Style for the top bar */
  .footer{
    position: fixed;
    bottom: 30;
    background-color: #1649FF;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 40px;
    padding: 0px;
    width: 95%;
    align-self: center;
    margin: 5px;
    border-radius: 10px;
    font-family: 'Trebuchet MS';
  }
  .link {
    color: white;
    text-decoration: none;
    font-size: 20px;
    margin: 10px;
    font-family: 'Trebuchet MS';
  }
  body {
    margin: 0;
    padding: 20px;
    font-family: 'Trebuchet MS';
    background-color: whitesmoke;
  }
  .top-bar {
    background-color: #1649FF;
    color: white;
    display: flex;
    align-items: center;
    justify-content: left;
    height: 50px;
    padding: 10px;
    width: 95%;
    align-self: center;
    margin: 5px;
    border-radius: 10px;
    font-family: 'Trebuchet MS';
    transition: all 0.3s ease-in-out;
    z-index: 1;
  }
  /* Style for the burger menu */
  .burger-menu {
    align-items: left;
    font-size: 25px;
    margin-right: 50px;
    cursor: pointer;
  }
  
  /* Style for the close menu button */
  .close-menu {
    position: absolute;
    top: 10px;
    right: 10px;
    font-size: 25px;
    cursor: pointer;
  }
  
  /* Style for the left menu */
  .left-menu {
    position: fixed;
    top: 0;
    left: -200px;
    width: 200px;
    height: 100%;
    background-color: #1649FF;
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease-in-out;
    font-family: 'Trebuchet MS';
    z-index: 1; /* Add this line to ensure the menu is on top of other elements */
  }
  
  .left-menu.open {
    left: 0;
  }
  .left-menu.open ~ * {
    transform: translateX(200px);
  }
  
  /* Style for the top bar when menu is open */
  .top-bar.open {
    transform: translateX(200px);
  }
</style>
<body class:open={isMenuOpen}>
  <div class="top-bar" class:open={isMenuOpen}>
    <div class="burger-menu" tabindex="0" on:keydown={(e) => {if (e.key === 'Enter') toggleMenu()}} on:click={() => toggleMenu()} aria-label="Menu" role="button">
      &#9776;
    </div>
    <img src="https://raw.githubusercontent.com/pjgraczyk/pganalytics.me/48e0e63ad85fdd934a711d8204b02207ad41f54e/images/logo.svg" alt="logo" width="60" height="60">
    <h1>Home</h1>    
  </div>
  <div class="left-menu" class:open={isMenuOpen}>
    <div class="close-menu" on:click={() => isMenuOpen = false}>
      &times;
    </div>
    <!-- Your menu items go here -->
    <a href="https://pganalytics.me/" target="_blank" class="link">Home</a>
    <a href="https://pganalytics.me/about/" target="_blank" class="link">About</a>
    <a href="https://pganalytics.me/contact/" target="_blank" class="link">Contact</a>
    <a href="https://pganalytics.me/blog/" target="_blank" class="link">Blog</a>
    <a href="https://pganalytics.me/portfolio/" target="_blank" class="link">Portfolio</a>
    <a href="https://pganalytics.me/privacy-policy/" target="_blank" class="link">Privacy Policy</a>
  </div>
  
  <h1>Welcome to my Data Analyst Webpage</h1>
  <p>Here you will find all the latest news and insights on data analysis.</p>
  <p>Stay tuned for more updates!</p>
  <div class="container">
    <h2>Data Analysis Report</h2>
    <!-- Rest of the webpage content goes here -->
  </div>
  
  <!-- Add privacy policy and terms of service -->
  <div class="footer">
    <p>© 2021 PGAnalytics.me</p>
  </div>
</body>