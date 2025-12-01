
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MegaClic Challenge</title>
<style>
  body { font-family: Arial, sans-serif; text-align: center; margin: 0; background: #f0f0f0; }
  header, footer { background: red; color: white; padding: 15px 0; }
  button { padding: 20px 40px; font-size: 24px; margin: 20px; background: red; color: white; border: none; border-radius: 10px; cursor: pointer; }
  button:active { transform: scale(0.95); }
  #counter { font-size: 24px; margin-top: 20px; }
  #podium { margin-top: 40px; }
  .player { background: #fff; margin: 10px auto; padding: 10px; width: 80%; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.2);}
  .footer-info { font-size: 12px; margin-top: 10px; color: #fff; }
  .footer-legal { font-size: 11px; margin-top: 15px; color: #fff; }
</style>
</head>
<body>

<header>
  <h1>MegaClic Challenge</h1>
</header>

<div>
  <button id="clickBtn">Clique-moi !</button>
  <div id="counter">Clics: 0</div>
</div>

<h2>Podium</h2>
<div id="podium"></div>

<footer>
  <div>MegaClic Challenge &copy; 2025 Tous droits réservés.</div>

  <div class="footer-info">
    Hébergement : Google | Email : lolanberkat@gmail.com
  </div>

  <div class="footer-legal">
    Hébergeur du site : Google LLC<br>
    Adresse : 1600 Amphitheatre Parkway, Mountain View, CA 94043, USA<br>
    Site web : https://www.google.com<br><br>

    Tous les pseudos demandés ne sont pas récoltés ni stockés dans un serveur.
  </div>
</footer>

<script>
  let clicks = 0;
  const clickBtn = document.getElementById('clickBtn');
  const counter = document.getElementById('counter');
  const podiumDiv = document.getElementById('podium');

  // Demander le nom du joueur
  let playerName = prompt("Bienvenue dans MegaClic Challenge ! Quel est ton nom ?");
  if (!playerName) playerName = "Vous";

  // Sons personnalisés (son1.mp3 → son10.mp3)
  const sounds = [];
  for (let i = 1; i <= 10; i++) {
    sounds.push(`son${i}.mp3`);
  }

  clickBtn.addEventListener('click', () => {
    clicks++;
    counter.textContent = 'Clics: ' + clicks;

    // Jouer un son aléatoire
    const audio = new Audio(sounds[Math.floor(Math.random() * sounds.length)]);
    audio.play();

    updatePodium();
  });

  // Bots avec scores énormes (1000+)
  const bots = [
    { name: "Massinissa", score: Math.floor(Math.random() * 500) + 1000 },
    { name: "Lilian", score: Math.floor(Math.random() * 500) + 1000 },
    { name: "Eric", score: Math.floor(Math.random() * 500) + 1000 }
  ];

  function updatePodium() {
    const players = [...bots, { name: playerName, score: clicks }];
    players.sort((a,b) => b.score - a.score);
    
    podiumDiv.innerHTML = '';
    players.slice(0, 3).forEach((p, i) => {
      podiumDiv.innerHTML += `<div class="player">${i+1}️⃣ ${p.name}: ${p.score} clics</div>`;
    });
  }

  updatePodium();
</script>

</body>
</html>
