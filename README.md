<!DOCTYPE html>
<html lang="fr">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Keibstream - Accueil</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
    <link rel="icon" href="images/logo.png">
    <style>
        :root {
            --primary-color: #0077FF;
            --secondary-color: #D63031;
            --background-color: #000;
            --text-color: #fff;
            --hover-scale: 1.05;
        }

        html,
        body {
            height: 100%;
            margin: 0;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-image: url('images/fondwindows.jpg');
            background-size: cover;
        }

        .banner {
            background-position: center;
            display: flex;
            flex-direction: column;
            height: 100vh;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 4%;
            background: rgba(0, 0, 0, 0.5);
        }

        nav div {
            display: flex;
            align-items: center;
        }

        .nav-button {
            background: #0077FF; /* Bleu océan */
            border: none;
            color: white;
            font-size: 1rem;
            margin-right: 0.5rem;
            cursor: pointer;
            transition: transform 0.3s ease;
            border-radius: 0.5rem;
            padding: 0.5rem 1rem;
        }

        .nav-button:hover {
            transform: scale(1.1);
        }

        .login-button button {
            background-color: #FF3B3F; /* Rouge */
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            font-size: 1rem;
            cursor: pointer;
            border-radius: 0.25rem;
            transition: background-color 0.3s ease;
        }

        .login-button button:hover {
            background-color: #D63031; /* Rouge plus foncé au survol */
        }

        .content {
            margin: 0;
            text-align: center;
            padding: 1rem;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
        }

        .content h1 {
            font-size: 3rem;
            font-weight: bold;
            color: white;
            margin-bottom: 3rem;
            font-family: 'Roboto', sans-serif; /* Utilisation d'une police plus moderne */
            width: 100%;
            text-align: center;
        }

    
        .search-bar {
        margin: auto; /* Centrage de la barre de recherche */
        max-width: 500px; /* Largeur maximale de la barre de recherche */
        margin-top: 1rem;
        display: flex;
        align-items: center;
        justify-content: center; /* Centrage horizontal */
        width: 100%;
        transition: transform 0.3s ease; /* Ajout de transition pour un effet fluide */
        }

        .search-bar:hover {
        transform: scale(1.05); /* Effet de zoom au survol */
        }

        .search-bar input {
        padding: 0.5rem;
        font-size: 1rem;
        margin-bottom: 0.5rem;
        margin-right: 0.5rem;
        width: 100%;
        max-width: 400px;
        }


        .videos-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin-top: 20px;
            width: 100%;
        }

        .video-card {
            background: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 1rem;
            border-radius: 8px;
            text-align: center;
            transition: transform 0.2s ease-in-out;
            cursor: pointer;
            overflow: hidden;
            width: 45%; /* Largeur des cartes vidéo */
            max-width: 300px; /* Largeur maximale des cartes vidéo */
        }

        .video-card:hover {
            transform: scale(1.05);
        }

        .video-cover {
            max-width: 100%;
            height: 150px;
            border-radius: 8px;
            overflow: hidden;
        }

        .video-cover img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .video-card p {
            margin-top: 1rem;
            font-size: 1rem;
        }

        .hidden {
            display: none;
        }

        /* Style pour le menu déroulant */
        .dropdown {
            position: relative;
            display: inline-block;
        }

        .dropdown-content {
            display: none;
            position: absolute;
            background-color: #f9f9f9;
            min-width: 160px;
            box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
            z-index: 1;
        }

        .dropdown-content a {
            color: black;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
        }

        .dropdown-content a:hover {
            background-color: #f1f1f1;
        }

        .dropdown:hover .dropdown-content {
            display: block;
        }
        
        .about-button {
            background-color: black; /* Couleur noire */
            color: white; /* Texte blanc */
            border: none;
            padding: 0.5rem 1rem;
            font-size: 1rem;
            cursor: pointer;
            border-radius: 0.25rem;
            transition: transform 0.3s, background-color 0.3s; /* Ajout de transition pour un effet fluide */
            margin-right: 2rem; /* Écart par rapport au bouton de connexion */
        }

.         about-button:hover {
            transform: scale(1.1); /* Effet de zoom au survol */
            background-color: #333; /* Légère variation de couleur au survol */
        }

    </style>
</head>

<body class="antialiased text-gray-800">
    <div class="banner">
        <nav>
            <div>
                <a href="index.html" style="display: inline-block;">
                    <img src="images/logo.png" alt="Logo" width="60" height="60" style="margin-right: 0.5rem;">
                </a>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                <div class="dropdown">
                    <button class="nav-button">Films</button>
                    <div class="dropdown-content">
                        <a href="movietout.html">Tout</a>
                        <a href="movieparfamille.html">Par Famille</a>
                </div>
                </div>
                <div class="dropdown">
                    <button class="nav-button">Séries</button>
                    <div class="dropdown-content">
                        <a href="seriestout.html">Tout</a>
                        <a href="seriesparfamille.html">Par Famille</a>
            </div>
            </div>

            </div>

            <div class="login-button">
                <button onclick="redirectToLogin()">Connexion</button>
            </div>
        </nav>
        <div class="content">
            <div class="search-bar">
                <input id="searchInput" type="text" placeholder="Rechercher" oninput="searchMovies()">
            </div>
            <br>
            <div class="videos-container" id="videosContainer">
                <!-- Cartes vidéo ici -->
            <div class="video-card" data-video-link="https://drive.google.com/file/d/1_SbYuHgQgUH2I6TKvmhP8uHz5_oGqgrW/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/kingdomofheaven.png" width="100%" alt="kingdomofheaven">
                    </div>
                    <p>Kingdom of Heaven 2005</p>
                </div>

                <div class="video-card" data-video-link="https://drive.google.com/file/d/1FM9RZ5zU8cwtb3aYeLckMNbsUsRnkhpH/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/les-trois-mousquetaires-dartagnan.jpg" width="100%" alt="les-trois-mousquetaires-dartagnan">
                    </div>
                    <p>Les Trois Mousquetaires - D'Artagnan 2023</p>
                </div>

                 <div class="video-card" data-video-link="https://drive.google.com/file/d/1Nj1J1ZydGKpv7X3eaRU2kxgATANuC2uy/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/titanic.jpg" width="100%" alt="titanic">
                    </div>
                    <p>Titanic 1997</p>
                </div>
                
                    <div class="video-card" data-video-link="https://drive.google.com/file/d/16d0WGKlP51SO2TpP9rrxB55VfhaDum1r/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/dune 1.jpg" width="100%" alt="dune 1 2021">
                    </div>
                    <p>Dune 1 2021</p>
                </div>
                 <div class="video-card" data-video-link="https://drive.google.com/file/d/1PbYc4I6C0bYRB5CDEGjFYeja_wvfN-Q5/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/Les Gardiens de la Galaxie 3 2023.jpg" width="100%" alt="Les Gardiens de la Galaxie 3 2023">
                    </div>
                    <p>Les Gardiens de la Galaxie 3 2023</p>
                </div>
                
                    <div class="video-card" data-video-link="https://drive.google.com/file/d/1Hs88_3MoMgkC3ds2Fp54UHpHqJv11Xct/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/Les Gardiens de la Galaxie 2 2017.jpeg" width="100%" alt="Les Gardiens de la Galaxie 2 2017">
                    </div>
                    <p>Les Gardiens de la Galaxie 2 2017</p>
                </div>
                
                    <div class="video-card" data-video-link="https://drive.google.com/file/d/1hYVgG_WGEEqprABFdIjcmxwSxzx-eNNX/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/Les Gardiens de la Galaxie 1 2014.jpeg" width="100%" alt="Les Gardiens de la Galaxie 1 2014">
                    </div>
                    <p>Les Gardiens de la Galaxie 1 2014</p>
                </div>
                
                    <div class="video-card" data-video-link="https://drive.google.com/file/d/1zGQ8bE-lPy_mpBWShUQb6GSpfDaNSNRt/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/Grand%20Turismo%202023.jpeg" width="100%" alt="Grand Turismo 2023">
                    </div>
                    <p>Grand Turismo 2023</p>
                </div>

                    <div class="video-card" data-video-link="https://drive.google.com/file/d/1oyeiPyvB5ng5Ov4HUC0Gm82vXYBr4Kus/view?usp=drive_link" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/Oppenheimer 2023.jpg" width="100%" alt="Oppenheimer 2023">
                    </div>
                    <p>Oppenheimer 2023</p>
                </div>
                
                  <div class="video-card" data-video-link="https://drive.google.com/drive/u/3/folders/1OSI4R-6EIcY0Zvl_UEGJ56jP1xrlifwn" onclick="playVideo(this)">
                    <div class="video-cover">
                        <img src="miniatures/Ferrari.2023.4k.jpg" width="100%" alt="Ferrari 2023">
                    </div>
                    <p>Ferrari, 2023</p>
            </div>
        </div>
    </div>

    <script>
    function redirectTo(page) {
        window.location.href = page;
    }

    function redirectToLogin() {
        window.location.href = 'login.php';
    }

    function searchMovies() {
        var input, filter, videos, videoCards, title, i;
        input = document.getElementById('searchInput');
        filter = input.value.toUpperCase();
        videos = document.getElementById('videosContainer');
        videoCards = videos.getElementsByClassName('video-card');

        for (i = 0; i < videoCards.length; i++) {
            title = videoCards[i].getElementsByTagName('p')[0];
            if (title.innerHTML.toUpperCase().indexOf(filter) > -1) {
                videoCards[i].style.display = '';
            } else {
                videoCards[i].style.display = 'none';
            }
        }
    }

    function playVideo(videoCard) {
        var videoLink = videoCard.getAttribute('data-video-link');

        // Open the YouTube link in a new browser tab
        window.open(videoLink, '_blank');
    }
        </script>
</body>

</html>
