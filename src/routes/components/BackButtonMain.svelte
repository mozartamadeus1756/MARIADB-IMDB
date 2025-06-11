
<script>
    // Simple navigation function for Svelte
    function goToMainPage() {
      window.location.href = "/main";
    }
  </script>
  
  <button class="back-button" on:click={goToMainPage}>
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
      <path d="M19 12H5"></path>
      <path d="M12 19l-7-7 7-7"></path>
    </svg>
    Back
  </button>
  
  <style>
    .back-button {
      position: fixed;
      top: 15px;
      right: 15px;
      background-color: #333;
      color: white;
      border: none;
      border-radius: 4px;
      padding: 8px 15px;
      font-size: 14px;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 5px;
      z-index: 1000;
    }
  
    .back-button:hover {
      background-color: #555;
    }
  </style>