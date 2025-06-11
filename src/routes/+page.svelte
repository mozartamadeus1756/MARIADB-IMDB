<script lang="ts">
  import Navbar from "./components/Navbar.svelte";
  import BottomNav from "./components/BottomNav.svelte";


  // Sample movie data - you can replace with your actual data
  const movies = [
    { title: "Movie of the day" },
    { title: "Movie of the day" },
    { title: "Movie of the day" }
  ];
</script>

<Navbar />


<div class="container">
  <div class="movie-grid">
    {#each movies as movie}
      <div class="movie-box">
        <div class="movie-content">
          <p class="movie-title">{movie.title}</p>
        </div>
      </div>
    {/each}
  </div>
</div>

<style>
.container {
  width: 100%;
  max-width: 100%;
  margin: 0 auto;
  padding: 20px;
  height: calc(100vh - 130px); /* Accounts for top navbar and bottom navbar */
  display: flex;
  align-items: center;
}

.movie-grid {
  display: flex;
  justify-content: space-between;
  gap: 3%;
  width: 100%;
  padding: 0 5%;
}

.movie-box {
  width: 30%;
  height: 70vh;
  border: 2px solid #000;
  display: flex;
  flex-direction: column;
}

.movie-content {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  padding: 10px;
}

.movie-title {
  writing-mode: vertical-rl;
  transform: rotate(180deg);
  text-align: center;
  font-size: 24px;
}

@media (max-width: 768px) {
  .movie-grid {
    flex-direction: column;
    align-items: center;
  }
  
  .movie-box {
    width: 90%;
    height: 30vh;
    margin-bottom: 20px;
  }
}
</style>

<BottomNav />