<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Partage de Jeux</title>
    <style>
        body {
            font-family: sans-serif;
            margin: 20px;
            background-color: #f4f4f4;
        }
        h1, h2 {
            color: #333;
        }
        .jeu {
            background-color: #fff;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .jeu h3 {
            margin-top: 0;
            color: #007bff;
        }
        .jeu p {
            margin-bottom: 5px;
        }
        .lien-telechargement {
            display: block;
            margin-top: 10px;
            color: green;
            text-decoration: none;
            font-weight: bold;
        }
        .lien-telechargement:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <h1>Partage tes Jeux !</h1>

    <div id="liste-jeux">
        </div>

    <h2>Ajouter un Nouveau Jeu</h2>
    <form id="form-ajout-jeu">
        <div>
            <label for="nom-jeu">Nom du jeu :</label>
            <input type="text" id="nom-jeu" name="nom-jeu" required><br><br>
        </div>
        <div>
            <label for="description-jeu">Description :</label><br>
            <textarea id="description-jeu" name="description-jeu" rows="4" cols="50"></textarea><br><br>
        </div>
        <div>
            <label for="lien-jeu">Lien de téléchargement :</label>
            <input type="url" id="lien-jeu" name="lien-jeu"><br><br>
        </div>
        <button type="button" onclick="ajouterJeu()">Partager ce jeu</button>
    </form>

    <script>
        function ajouterJeu() {
            const nomJeu = document.getElementById("nom-jeu").value;
            const descriptionJeu = document.getElementById("description-jeu").value;
            const lienJeu = document.getElementById("lien-jeu").value;
            const listeJeux = document.getElementById("liste-jeux");
            const formAjoutJeu = document.getElementById("form-ajout-jeu");

            if (nomJeu) {
                const nouveauJeu = document.createElement("div");
                nouveauJeu.classList.add("jeu");
                nouveauJeu.innerHTML = `
                    <h3>${nomJeu}</h3>
                    <p>${descriptionJeu}</p>
                    ${lienJeu ? `<a href="${lienJeu}" class="lien-telechargement" target="_blank">Télécharger</a>` : ''}
                `;
                listeJeux.appendChild(nouveauJeu);
                formAjoutJeu.reset(); // Effacer le formulaire après l'ajout
            } else {
                alert("Le nom du jeu est obligatoire.");
            }
        }
    </script>
</body>
</html>
