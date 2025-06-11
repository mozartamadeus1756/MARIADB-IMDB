<script></script>
  
  <nav class="bottom-navbar">
    <div class="navbar-container">
      <a href="/about" class="nav-item">
        <div class="icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle><path d="M12 16v-4"></path><path d="M12 8h.01"></path></svg>
        </div>
        <span class="label">About</span>
      </a>
    </div>
  </nav>
  
  <style>
    .bottom-navbar {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      background-color: #1a1a1a;
      z-index: 1000;
    }
  
    .navbar-container {
      display: flex;
      justify-content: center;
      padding: 10px 0;
    }
  
    .nav-item {
      display: flex;
      align-items: center;
      text-decoration: none;
      color: #fff;
      padding: 5px 15px;
      gap: 5px;
    }
  
    .nav-item:hover {
      color: #aaa;
    }
  
    /* Make sure content doesn't get hidden behind navbar */
    :global(body) {
      padding-bottom: 50px;
    }
  </style>




