<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulaire avec Photo</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
        }
        form {
            margin-top: 20px;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input[type="text"], input[type="date"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        input[type="file"] {
            margin-bottom: 15px;
        }
        input[type="submit"] {
            background-color: #4CAF50;
            color: white;
            padding: 12px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
        }
        input[type="submit"]:hover {
            background-color: #45a049;
        }
        #carteIdentite {
            border: 4px solid #ccc; /* Cadre plus épais et gris */
            padding: 20px;
            margin-top: 20px;
            border-radius: 8px;
            background-color: #f9f9f9;
            display: none; /* Initialement masqué */
        }
        #carteIdentite.generer {
            display: block; /* Afficher la carte d'identité après soumission */
        }
        #carteIdentite img {
            max-width: 200px; /* Reduire la taille de l'image */
            height: auto;
            border-radius: 8px; /* Appliquer un style de bord arrondi */
            display: block;
            margin: 0 auto; /* Centrer l'image */
            margin-top: 10px; /* Ajouter un peu d'espace au-dessus de l'image */
        }
        /* Style pour la partie générée */
        .generer {
            font-size: 20px;
        }
        .generer p {
            margin-bottom: 10px; /* Plus d'espace entre les paragraphes */
        }
        .nomPrenom, .dateAge {
            display: flex;
            justify-content: space-between; /* Espace entre le nom et le prénom */
            margin-bottom: 10px;
        }
        .nomPrenom span, .dateAge span {
            font-weight: bold;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Formulaire avec Photo</h2>
    <form id="formulaire">
        <label for="nom">Nom :</label>
        <input type="text" id="nom" name="nom" required>

        <label for="prenom">Prénom :</label>
        <input type="text" id="prenom" name="prenom" required>

        <label for="dateNaissance">Date de Naissance :</label>
        <input type="date" id="dateNaissance" name="dateNaissance" required>

        <label for="photo">Photo :</label>
        <input type="file" id="photo" name="photo" accept="image/*" required>

        <input type="submit" value="Soumettre">
    </form>

    <div id="carteIdentite">
        <h2>Carte d'Identité</h2>
        <div class="nomPrenom">
            <p><span id="nomLabel">Nom :</span> <span id="nomComplet"></span></p>
            <p><span id="prenomLabel">Prénom :</span> <span id="prenomComplet"></span></p>
        </div>
        <div class="dateAge">
            <p><span id="dateNaissanceLabel">Date de Naissance :</span> <span id="dateNaissanceInfo"></span></p>
            <p><span id="ageLabel">Âge :</span> <span id="ageInfo"></span></p>
        </div>
        <img id="photoCarte" src="#" alt="Photo">
    </div>
</div>

<script>
    document.getElementById("formulaire").addEventListener("submit", function(event) {
        event.preventDefault();
        
        var nom = document.getElementById("nom").value;
        var prenom = document.getElementById("prenom").value;
        var dateNaissance = document.getElementById("dateNaissance").value;
        
        // Calculer l'âge à partir de la date de naissance
        var today = new Date();
        var birthDate = new Date(dateNaissance);
        var age = today.getFullYear() - birthDate.getFullYear();
        var m = today.getMonth() - birthDate.getMonth();
        if (m < 0 || (m === 0 && today.getDate() < birthDate.getDate())) {
            age--;
        }
        
        // Afficher les informations sur la carte d'identité
        document.getElementById("nomComplet").innerText = nom;
        document.getElementById("prenomComplet").innerText = prenom;
        document.getElementById("dateNaissanceInfo").innerText = dateNaissance;
        document.getElementById("ageInfo").innerText = age + " ans";
        
        // Afficher la photo sur la carte d'identité
        var photo = document.getElementById("photo").files[0];
        var reader = new FileReader();
        reader.onload = function(e) {
            document.getElementById("photoCarte").src = e.target.result;
        }
        reader.readAsDataURL(photo);
        
        // Afficher la carte d'identité
        document.getElementById("carteIdentite").classList.add("generer");

        // Masquer le formulaire
        document.getElementById("formulaire").style.display = "none";
    });
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulaire avec Photo</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
        }
        form {
            margin-top: 20px;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input[type="text"], input[type="date"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        input[type="file"] {
            margin-bottom: 15px;
        }
        input[type="submit"] {
            background-color: #4CAF50;
            color: white;
            padding: 12px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
        }
        input[type="submit"]:hover {
            background-color: #45a049;
        }
        #carteIdentite {
            border: 4px solid #ccc; /* Cadre plus épais et gris */
            padding: 20px;
            margin-top: 20px;
            border-radius: 8px;
            background-color: #f9f9f9;
            display: none; /* Initialement masqué */
        }
        #carteIdentite.generer {
            display: block; /* Afficher la carte d'identité après soumission */
        }
        #carteIdentite img {
            max-width: 200px; /* Reduire la taille de l'image */
            height: auto;
            border-radius: 8px; /* Appliquer un style de bord arrondi */
            display: block;
            margin: 0 auto; /* Centrer l'image */
            margin-top: 10px; /* Ajouter un peu d'espace au-dessus de l'image */
        }
        /* Style pour la partie générée */
        .generer {
            font-size: 20px;
        }
        .generer p {
            margin-bottom: 10px; /* Plus d'espace entre les paragraphes */
        }
        .nomPrenom, .dateAge {
            display: flex;
            justify-content: space-between; /* Espace entre le nom et le prénom */
            margin-bottom: 10px;
        }
        .nomPrenom span, .dateAge span {
            font-weight: bold;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Formulaire avec Photo</h2>
    <form id="formulaire">
        <label for="nom">Nom :</label>
        <input type="text" id="nom" name="nom" required>

        <label for="prenom">Prénom :</label>
        <input type="text" id="prenom" name="prenom" required>

        <label for="dateNaissance">Date de Naissance :</label>
        <input type="date" id="dateNaissance" name="dateNaissance" required>

        <label for="photo">Photo :</label>
        <input type="file" id="photo" name="photo" accept="image/*" required>

        <input type="submit" value="Soumettre">
    </form>

    <div id="carteIdentite">
        <h2>Carte d'Identité</h2>
        <div class="nomPrenom">
            <p><span id="nomLabel">Nom :</span> <span id="nomComplet"></span></p>
            <p><span id="prenomLabel">Prénom :</span> <span id="prenomComplet"></span></p>
        </div>
        <div class="dateAge">
            <p><span id="dateNaissanceLabel">Date de Naissance :</span> <span id="dateNaissanceInfo"></span></p>
            <p><span id="ageLabel">Âge :</span> <span id="ageInfo"></span></p>
        </div>
        <img id="photoCarte" src="#" alt="Photo">
    </div>
</div>

<script>
    document.getElementById("formulaire").addEventListener("submit", function(event) {
        event.preventDefault();
        
        var nom = document.getElementById("nom").value;
        var prenom = document.getElementById("prenom").value;
        var dateNaissance = document.getElementById("dateNaissance").value;
        
        // Calculer l'âge à partir de la date de naissance
        var today = new Date();
        var birthDate = new Date(dateNaissance);
        var age = today.getFullYear() - birthDate.getFullYear();
        var m = today.getMonth() - birthDate.getMonth();
        if (m < 0 || (m === 0 && today.getDate() < birthDate.getDate())) {
            age--;
        }
        
        // Afficher les informations sur la carte d'identité
        document.getElementById("nomComplet").innerText = nom;
        document.getElementById("prenomComplet").innerText = prenom;
        document.getElementById("dateNaissanceInfo").innerText = dateNaissance;
        document.getElementById("ageInfo").innerText = age + " ans";
        
        // Afficher la photo sur la carte d'identité
        var photo = document.getElementById("photo").files[0];
        var reader = new FileReader();
        reader.onload = function(e) {
            document.getElementById("photoCarte").src = e.target.result;
        }
        reader.readAsDataURL(photo);
        
        // Afficher la carte d'identité
        document.getElementById("carteIdentite").classList.add("generer");

        // Masquer le formulaire
        document.getElementById("formulaire").style.display = "none";
    });
</script>

</body>
</html>
