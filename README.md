
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CineWorld | Movie Hub</title>

    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: #101018;
            color: white;
        }

        header {
            background: #191923;
            padding: 18px 7%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }

        .logo {
            color: #ff4545;
            font-size: 28px;
            font-weight: 700;
        }

        nav {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-size: 14px;
        }

        nav a:hover {
            color: #ff4545;
        }

        .hero {
            min-height: 350px;
            padding: 70px 7%;
            display: flex;
            align-items: center;
            background:
                linear-gradient(90deg, #101018 10%, #101018cc 55%, #10101833),
                url('https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1600&q=85')
                center/cover;
        }

        .hero-content {
            max-width: 600px;
        }

        .hero h1 {
            font-size: clamp(34px, 5vw, 55px);
            margin-bottom: 15px;
        }

        .hero p {
            color: #ddd;
            margin-bottom: 22px;
        }

        .btn {
            background: #ff4545;
            color: white;
            border: none;
            padding: 12px 22px;
            border-radius: 5px;
            text-decoration: none;
            cursor: pointer;
            font: inherit;
            display: inline-block;
        }

        .btn:hover {
            background: #d92e2e;
        }

        .container {
            padding: 45px 7%;
        }

        .section-title {
            font-size: 27px;
            margin-bottom: 22px;
            border-left: 4px solid #ff4545;
            padding-left: 12px;
        }

        .filters {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin-bottom: 25px;
        }

        .filters input,
        .filters select {
            padding: 12px;
            background: #20202c;
            color: white;
            border: 1px solid #393947;
            border-radius: 5px;
            font: inherit;
        }

        .filters input {
            flex: 1;
            min-width: 180px;
        }

        .filters select {
            max-width: 100%;
        }

        .movie-grid {
            display: grid;
            grid-template-columns: repeat(4, minmax(0, 1fr));
            gap: 24px;
        }

        .movie-card {
            background: #1b1b27;
            border-radius: 10px;
            overflow: hidden;
            transition: transform 0.3s;
            border: 1px solid #2c2c3b;
        }

        .movie-card:hover {
            transform: translateY(-6px);
        }

        .poster {
            position: relative;
        }

        .poster img {
            width: 100%;
            height: 320px;
            object-fit: cover;
            display: block;
        }

        .rating {
            position: absolute;
            top: 12px;
            right: 12px;
            background: #ffc107;
            color: #171717;
            padding: 5px 9px;
            border-radius: 5px;
            font-size: 13px;
            font-weight: 700;
        }

        .movie-info {
            padding: 17px;
        }

        .movie-info h3 {
            font-size: 18px;
            margin-bottom: 8px;
        }

        .genre {
            color: #ff7777;
            font-size: 12px;
            margin-bottom: 8px;
        }

        .release {
            color: #aaa;
            font-size: 13px;
            margin-bottom: 10px;
        }

        .synopsis {
            font-size: 13px;
            color: #ccc;
            margin-bottom: 14px;
        }

        .details-btn {
            width: 100%;
            background: transparent;
            color: white;
            border: 1px solid #ff4545;
            padding: 9px;
            border-radius: 5px;
            cursor: pointer;
        }

        .details-btn:hover {
            background: #ff4545;
        }

        .reviews-section {
            background: #191923;
        }

        .reviews-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }

        .review-card {
            padding: 22px;
            background: #242431;
            border-radius: 8px;
        }

        .review-card h3 {
            margin-bottom: 8px;
        }

        .stars {
            color: #ffc107;
            margin: 10px 0;
        }

        .review-card p {
            color: #ccc;
            font-size: 14px;
        }

        .about {
            text-align: center;
            color: #bbb;
        }

        footer {
            background: #0a0a10;
            padding: 25px;
            text-align: center;
            color: #aaa;
        }

        /* Movie details popup */
        dialog {
            background: #20202c;
            color: white;
            border: 1px solid #444;
            border-radius: 10px;
            padding: 28px;
            width: min(90%, 550px);
            max-height: 85vh;
            overflow-y: auto;
            margin: auto;
        }

        dialog::backdrop {
            background: #000b;
        }

        dialog h2 {
            margin-bottom: 12px;
        }

        dialog p {
            margin-bottom: 12px;
            color: #ddd;
        }

        .close-btn {
            margin-top: 12px;
        }

        @media (max-width: 1000px) {
            .movie-grid {
                grid-template-columns: repeat(3, minmax(0, 1fr));
            }

            .reviews-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 700px) {
            header {
                flex-direction: column;
                align-items: flex-start;
            }

            .movie-grid {
                grid-template-columns: repeat(2, minmax(0, 1fr));
                gap: 14px;
            }

            .poster img {
                height: 250px;
            }

            .reviews-grid {
                grid-template-columns: 1fr;
            }

            .container {
                padding: 35px 5%;
            }
        }

        @media (max-width: 380px) {
            .movie-grid {
                grid-template-columns: 1fr;
            }

            .poster img {
                height: 360px;
            }
        }
    </style>
</head>

<body>

<header>
    <div class="logo">CineWorld</div>

    <nav>
        <a href="#home">Home</a>
        <a href="#movies">Movies</a>
        <a href="#reviews">Reviews</a>
        <a href="#about">About</a>
    </nav>
</header>

<!-- HERO SECTION -->
<section class="hero" id="home">
    <div class="hero-content">
        <h1>Your Next Movie Adventure Starts Here</h1>
        <p>
            Discover amazing movies, explore different genres,
            meet your favourite stars, and read reviews.
        </p>
        <a href="#movies" class="btn">Explore Movies</a>
    </div>
</section>

<!-- MOVIES SECTION -->
<section class="container" id="movies">
    <h2 class="section-title">Popular Movies</h2>

    <div class="filters">
        <input type="text" id="searchInput"
               placeholder="Search movies or actors...">

        <select id="genreFilter">
            <option value="all">All Genres</option>
            <option value="Action">Action</option>
            <option value="Sci-Fi">Sci-Fi</option>
            <option value="Drama">Drama</option>
            <option value="Adventure">Adventure</option>
            <option value="Crime">Crime</option>
            <option value="Animation">Animation</option>
        </select>

        <select id="sortFilter">
            <option value="default">Sort By</option>
            <option value="rating">Highest Rated</option>
            <option value="newest">Newest Release</option>
        </select>
    </div>

    <div class="movie-grid" id="movieGrid">

        <article class="movie-card"
            data-title="Interstellar"
            data-genre="Sci-Fi"
            data-date="2014-11-07"
            data-rating="8.7"
            data-cast="Matthew McConaughey, Anne Hathaway, Jessica Chastain"
            data-critic="A visually ambitious science-fiction epic praised for its scale, emotional story and scientific ideas.">

            <div class="poster">
                <img src="https://image.tmdb.org/t/p/w500/gEU2QniE6E77NI6lCU6MxlNBvIx.jpg"
                     alt="Interstellar movie poster">
                <span class="rating">★ 8.7</span>
            </div>

            <div class="movie-info">
                <h3>Interstellar</h3>
                <p class="genre">Sci-Fi • Adventure • Drama</p>
                <p class="release">Release: November 7, 2014</p>
                <p class="synopsis">
                    A group of explorers travels through a wormhole
                    to search for a future home for humanity.
                </p>
                <button class="details-btn">View Details</button>
            </div>
        </article>

        <article class="movie-card"
            data-title="Inception"
            data-genre="Sci-Fi"
            data-date="2010-07-16"
            data-rating="8.8"
            data-cast="Leonardo DiCaprio, Joseph Gordon-Levitt, Elliot Page"
            data-critic="A mind-bending thriller widely admired for its inventive concept, visual effects and layered storytelling.">

            <div class="poster">
                <img src="https://image.tmdb.org/t/p/w500/oYuLEt3zVCKq57qu2F8dT7NIa6f.jpg"
                     alt="Inception movie poster">
                <span class="rating">★ 8.8</span>
            </div>

            <div class="movie-info">
                <h3>Inception</h3>
                <p class="genre">Sci-Fi • Action • Thriller</p>
                <p class="release">Release: July 16, 2010</p>
                <p class="synopsis">
                    A skilled thief enters people's dreams to steal
                    secrets and attempt an extraordinary mission.
                </p>
                <button class="details-btn">View Details</button>
            </div>
        </article>

        <article class="movie-card"
            data-title="The Dark Knight"
            data-genre="Crime"
            data-date="2008-07-18"
            data-rating="9.0"
            data-cast="Christian Bale, Heath Ledger, Aaron Eckhart"
            data-critic="A celebrated superhero crime drama, especially noted for its performances, tension and moral complexity.">

            <div class="poster">
                <img src="https://image.tmdb.org/t/p/w500/qJ2tW6WMUDux911r6m7haRef0WH.jpg"
                     alt="The Dark Knight movie poster">
                <span class="rating">★ 9.0</span>
            </div>

            <div class="movie-info">
                <h3>The Dark Knight</h3>
                <p class="genre">Crime • Action • Drama</p>
                <p class="release">Release: July 18, 2008</p>
                <p class="synopsis">
                    Batman faces the Joker, a criminal mastermind
                    who pushes Gotham City into chaos.
                </p>
                <button class="details-btn">View Details</button>
            </div>
        </article>

        <article class="movie-card"
            data-title="Avatar"
            data-genre="Adventure"
            data-date="2009-12-18"
            data-rating="7.9"
            data-cast="Sam Worthington, Zoe Saldaña, Sigourney Weaver"
            data-critic="Known for groundbreaking visual effects, immersive world-building and environmental themes.">

            <div class="poster">
                <img src="https://image.tmdb.org/t/p/w500/kyeqWdyUXW608qlYkRqosgbbJyK.jpg"
                     alt="Avatar movie poster">
                <span class="rating">★ 7.9</span>
            </div>

            <div class="movie-info">
                <h3>Avatar</h3>
                <p class="genre">Adventure • Sci-Fi • Action</p>
                <p class="release">Release: December 18, 2009</p>
                <p class="synopsis">
                    On Pandora, a former Marine becomes involved
                    in a conflict over the planet's future.
                </p>
                <button class="details-btn">View Details</button>
            </div>
        </article>

        <article class="movie-card"
            data-title="The Shawshank Redemption"
            data-genre="Drama"
            data-date="1994-09-23"
            data-rating="9.3"
            data-cast="Tim Robbins, Morgan Freeman, Bob Gunton"
            data-critic="A highly regarded prison drama praised for its performances, friendship and enduring themes of hope.">

            <div class="poster">
                <img src="https://image.tmdb.org/t/p/w500/9cqNxx0GxF0bflZmeSMuL5tnGzr.jpg"
                     alt="The Shawshank Redemption movie poster">
                <span class="rating">★ 9.3</span>
            </div>

            <div class="movie-info">
                <h3>Shawshank Redemption</h3>
                <p class="genre">Drama</p>
                <p class="release">Release: September 23, 1994</p>
                <p class="synopsis">
                    Two prisoners form a lasting friendship while
                    holding on to hope inside Shawshank prison.
                </p>
                <button class="details-btn">View Details</button>
            </div>
        </article>

        <article class="movie-card"
            data-title="The Lion King"
            data-genre="Animation"
            data-date="1994-06-24"
            data-rating="8.5"
            data-cast="Matthew Broderick, James Earl Jones, Jeremy Irons"
            data-critic="An acclaimed animated classic praised for its music, memorable characters and emotional storytelling.">

            <div class="poster">
                <img src="https://image.tmdb.org/t/p/w500/sKCr78MXSLixwmZ8DyJLrpMsd15.jpg"
                     alt="The Lion King movie poster">
                <span class="rating">★ 8.5</span>
            </div>

            <div class="movie-info">
                <h3>The Lion King</h3>
                <p class="genre">Animation • Adventure • Drama</p>
                <p class="release">Release: June 24, 1994</p>
                <p class="synopsis">
                    A young lion prince learns about responsibility,
                    loss and his place in the circle of life.
                </p>
                <button class="details-btn">View Details</button>
            </div>
        </article>

        <article class="movie-card"
            data-title="Dune"
            data-genre="Sci-Fi"
            data-date="2021-10-22"
            data-rating="8.0"
            data-cast="Timothée Chalamet, Rebecca Ferguson, Zendaya"
            data-critic="A visually striking science-fiction adaptation praised for its atmosphere, scale and production design.">

            <div class="poster">
                <img src="https://image.tmdb.org/t/p/w500/d5NXSklXo0qyIYkgV94XAgMIckC.jpg"
                     alt="Dune movie poster">
                <span class="rating">★ 8.0</span>
            </div>

            <div class="movie-info">
                <h3>Dune</h3>
                <p class="genre">Sci-Fi • Adventure • Drama</p>
                <p class="release">Release: October 22, 2021</p>
                <p class="synopsis">
                    Paul Atreides travels to the desert planet Arrakis,
                    where rival forces fight over a valuable resource.
                </p>
                <button class="details-btn">View Details</button>
            </div>
        </article>

        <article class="movie-card"
            data-title="Joker"
            data-genre="Crime"
            data-date="2019-10-04"
            data-rating="8.3"
            data-cast="Joaquin Phoenix, Robert De Niro, Zazie Beetz"
            data-critic="A dark character study praised for its central performance, though its themes and violence divided critics.">

            <div class="poster">
                <img src="https://image.tmdb.org/t/p/w500/udDclJoHjfjb8Ekgsd4FDteOkCU.jpg"
                     alt="Joker movie poster">
                <span class="rating">★ 8.3</span>
            </div>

            <div class="movie-info">
                <h3>Joker</h3>
                <p class="genre">Crime • Drama • Thriller</p>
                <p class="release">Release: October 4, 2019</p>
                <p class="synopsis">
                    A struggling comedian in Gotham City experiences
                    events that transform his life.
                </p>
                <button class="details-btn">View Details</button>
            </div>
        </article>

    </div>

    <p id="noResults" hidden style="margin-top:25px;">
        No movies found. Try another title or genre.
    </p>
</section>

<!-- CRITIC REVIEWS -->
<section class="container reviews-section" id="reviews">
    <h2 class="section-title">Critic Reviews</h2>

    <div class="reviews-grid">
        <div class="review-card">
            <h3>Interstellar</h3>
            <div class="stars">★★★★★</div>
            <p>
                An ambitious space epic that combines spectacular
                visuals with a deeply personal story.
            </p>
            <p><strong>Editorial rating: 9/10</strong></p>
        </div>

        <div class="review-card">
            <h3>Inception</h3>
            <div class="stars">★★★★★</div>
            <p>
                A clever, layered thriller that rewards attention
                and leaves viewers debating its ending.
            </p>
            <p><strong>Editorial rating: 9/10</strong></p>
        </div>

        <div class="review-card">
            <h3>Avatar</h3>
            <div class="stars">★★★★☆</div>
            <p>
                An immersive cinematic experience with ambitious
                world-building and spectacular imagery.
            </p>
            <p><strong>Editorial rating: 8/10</strong></p>
        </div>
    </div>
</section>

<!-- ABOUT -->
<section class="container about" id="about">
    <h2 class="section-title">About CineWorld</h2>
    <p>
        CineWorld is a movie discovery website where film lovers
        can explore movies, check ratings, discover casts, and
        read reviews across different genres.
    </p>
</section>

<footer>
    <p>© 2026 CineWorld | Movie Discovery Website</p>
    <p>Made for movie lovers.</p>
</footer>

<!-- MOVIE DETAILS DIALOG -->
<dialog id="movieDialog">
    <h2 id="dialogTitle"></h2>
    <p id="dialogGenre"></p>
    <p id="dialogRelease"></p>
    <p id="dialogCast"></p>
    <p id="dialogSynopsis"></p>
    <p id="dialogCritic"></p>
    <p id="dialogRating"></p>
    <button class="btn close-btn" id="closeDialog">Close</button>
</dialog>

<script>
    const searchInput = document.getElementById("searchInput");
    const genreFilter = document.getElementById("genreFilter");
    const sortFilter = document.getElementById("sortFilter");
    const movieGrid = document.getElementById("movieGrid");
    const noResults = do
