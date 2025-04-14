<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fiche de Personnage de la Terre du Milieu</title>
  <style>
    /* Bases et mise en page générale */
    body {
      font-family: "Palatino Linotype", serif;
      background: #0c0c0c;
      color: #d6d1b1;
      max-width: 900px;
      margin: auto;
      padding: 20px;
    }
    h1, h2 {
      color: #c2b280;
      border-bottom: 2px solid #c2b280;
      padding-bottom: 5px;
      margin-bottom: 15px;
    }
    h3 {
      font-size: 1.1em;
      margin: 0 0 10px;
    }
    label {
      font-size: 0.9em;
    }
    input, select, textarea, button {
      padding: 5px;
      margin-top: 5px;
      background-color: #222;
      color: #e4e0c3;
      border: 1px solid #444;
      border-radius: 4px;
    }
    small {
      color: #888;
      font-size: 0.8em;
    }
    .section {
      background: rgba(0, 0, 0, 0.75);
      padding: 20px;
      border-radius: 8px;
      margin-bottom: 20px;
    }
    /* Section Identité réorganisée en 4 colonnes */
    .identite-container {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
    }
    .identite-basic,
    .identite-progression,
    .identite-divers,
    .identite-sauvegarde {
      flex: 1 1 300px;
    }
    .identite-basic h3,
    .identite-progression h3,
    .identite-divers h3,
    .identite-sauvegarde h3 {
      margin-bottom: 10px;
      color: #c2b280;
    }
    .identite-basic label,
    .identite-progression label,
    .identite-divers label,
    .identite-sauvegarde label {
      margin-bottom: 10px;
      display: block;
    }
    /* Section Caractéristiques compacte avec test de compétence */
    .carac-grid {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .carac-item {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 5px;
    }
    .carac-item label {
      width: 80px;
      font-weight: bold;
    }
    .carac-item input[type="number"] {
      width: 60px;
      text-align: center;
    }
    .mod-display {
      width: 50px;
      font-weight: bold;
    }
    .carac-item button {
      padding: 5px 10px;
      max-width: 80px;
    }
    .result-display {
      margin-left: 10px;
      font-weight: bold;
      color: #ffd700;
      min-width: 120px;
      text-align: center;
    }
    .desc {
      margin-left: 10px;
      font-size: 0.8em;
      color: #aaa;
    }
    /* Boutons généraux et animation */
    button {
      cursor: pointer;
    }
    @keyframes flash {
      0% { transform: scale(1); }
      50% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }
    /* SECTION : ÉTAT DU PERSONNAGE */
    .etat-section {
      display: flex;
      flex-direction: column;
      gap: 20px;
    }
    .etat-buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
    }
    .etat-buttons button {
      background-color: #222;
      border: 1px solid #444;
      padding: 10px 15px;
      border-radius: 6px;
      color: #e4e0c3;
      flex: 1 1 100px;
      transition: background 0.2s, transform 0.2s;
    }
    .etat-buttons button:hover {
      background-color: #444;
      transform: scale(1.05);
    }
    .etat-stats {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: space-around;
      background: linear-gradient(135deg, #1a1a1a, #262626);
      padding: 15px;
      border-radius: 8px;
      box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.5);
    }
    .stat-box {
      flex: 1 1 200px;
      background: rgba(0, 0, 0, 0.5);
      padding: 10px;
      border-radius: 6px;
      text-align: center;
    }
    .global-ac input {
      font-weight: bold;
      color: #ffd700;
      background-color: #333;
    }
    .pv-container {
      display: flex;
      gap: 10px;
      justify-content: center;
    }
    .pv-field {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    /* SECTION Sauvegarde / Chargement */
    .save-section {
      text-align: center;
    }
    .save-section button {
      margin: 5px;
      padding: 10px 20px;
      background-color: #222;
      border: 1px solid #444;
      border-radius: 6px;
      color: #e4e0c3;
      transition: background 0.2s, transform 0.2s;
    }
    .save-section button:hover {
      background-color: #444;
      transform: scale(1.05);
    }
    /* Responsive Design */
    @media only screen and (max-width: 600px) {
      .etat-stats {
        flex-direction: column;
        align-items: center;
      }
      .etat-buttons button {
        flex: 1 1 calc(50% - 10px);
      }
      .identite-container {
        flex-direction: column;
      }
    }
  </style>
</head>
<body>

  <h1 id="titrePerso">Fiche de Personnage de la Terre du Milieu</h1>

  <!-- Section Lancer de Dés -->
  <div class="section">
    <h2>Lancer de Dés</h2>
    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(50px, 1fr)); gap: 3px;">
      <button onclick="lancerDe(3)">D3</button>
      <button onclick="lancerDe(4)">D4</button>
      <button onclick="lancerDe(5)">D5</button>
      <button onclick="lancerDe(6)">D6</button>
      <button onclick="lancerDe(7)">D7</button>
      <button onclick="lancerDe(8)">D8</button>
      <button onclick="lancerDe(10)">D10</button>
      <button onclick="lancerDe(12)">D12</button>
      <button onclick="lancerDe(14)">D14</button>
      <button onclick="lancerDe(16)">D16</button>
      <button onclick="lancerDe(20)">D20</button>
      <button onclick="lancerDe(24)">D24</button>
      <button onclick="lancerDe(30)">D30</button>
      <button onclick="lancerDe(60)">D60</button>
      <button onclick="lancerDe(100)">D100</button>
    </div>
    <div id="resultatDe" style="margin-top: 10px; font-size: 1.5em; text-align: center; background-color: #222; padding: 10px; border: 2px solid #c2b280; border-radius: 10px; color: #ffd700; box-shadow: 0 0 10px #c2b280;"></div>
  </div>

  <!-- Section État du Personnage -->
  <div class="section etat-section">
    <h2>État du Personnage</h2>
    <div class="etat-buttons">
      <button onclick="setEtat('normal')">Normal</button>
      <button onclick="setEtat('empoisonne')">Empoisonné</button>
      <button onclick="setEtat('comas')">Comas</button>
      <button onclick="setEtat('renverse')">Renversé</button>
      <button onclick="setEtat('etourdi')">Étourdi</button>
      <button onclick="setEtat('endormi')">Endormi</button>
      <button onclick="setEtat('immobilise')">Immobilisé</button>
    </div>
    <div class="etat-stats">
      <div class="stat-box">
        <h3>Points de Vie</h3>
        <div class="pv-container">
          <div class="pv-field">
            <label>Max</label>
            <input id="pvMax" type="number" value="0" min="0">
          </div>
          <div class="pv-field">
            <label>Actuel</label>
            <input id="pvActuel" type="number" value="0" min="0">
          </div>
        </div>
      </div>
      <div class="stat-box">
        <h3>CA de Base</h3>
        <input id="classeArmure" type="number" value="10" min="0" oninput="updateGlobalAC()">
      </div>
      <div class="stat-box global-ac">
        <h3>CA Totale</h3>
        <input id="globalAC" type="number" value="10" readonly>
      </div>
    </div>
  </div>

  <!-- Section Identité réorganisée -->
  <div class="section">
    <h2>Identité</h2>
    <div class="identite-container">
      <!-- Informations de Base -->
      <div class="identite-basic">
        <h3>Informations de Base</h3>
        <label>Nom:
          <input type="text" id="nomPerso" oninput="updateTitrePerso()">
        </label>
        <label>Race:
          <select id="racePerso" onchange="updateTitrePerso()">
            <option>Humain</option>
            <option>Nain</option>
            <option>Elfe</option>
            <option>Hobbit</option>
          </select>
        </label>
        <label>Classe:
          <select id="classePerso" onchange="updateTitrePerso()">
            <option>Guerrier</option>
            <option>Voleur</option>
            <option>Nain</option>
            <option>Elfe</option>
            <option>Hobbit</option>
          </select>
        </label>
        <label>Métier:
          <input type="text" id="metierPerso" oninput="updateTitrePerso()">
        </label>
      </div>
      <!-- Progression -->
      <div class="identite-progression">
        <h3>Progression</h3>
        <label>XP:
          <input id="xp" type="number" value="0" oninput="updateNiveauFromXP()">
        </label>
        <label>Niveau:
          <input id="niveau" type="number" value="1" readonly>
        </label>
      </div>
      <!-- Informations Diverses -->
      <div class="identite-divers">
        <h3>Informations Diverses</h3>
        <label>Langues:
          <input id="langues" type="text" placeholder="Langues parlées">
        </label>
        <label>Augure de Naissance:
          <input id="augure" type="text" placeholder="Augure de naissance">
        </label>
      </div>
      <!-- Jets de Sauvegarde -->
      <div class="identite-sauvegarde">
        <h3>Jets de Sauvegarde</h3>
        <label>Vigueur: <span id="sauv_vigueur"></span></label>
        <label>Réflexes: <span id="sauv_reflexes"></span></label>
        <label>Volonté: <span id="sauv_volonte"></span></label>
      </div>
    </div>
  </div>

  <!-- Section Caractéristiques compacte avec test de compétence -->
  <div class="section">
    <h2>Caractéristiques</h2>
    <div class="carac-grid">
      <!-- Force -->
      <div class="carac-item">
        <label>Force:</label>
        <input id="force" type="number" value="10" oninput="updateModificateur('force')">
        <span id="mod-force" class="mod-display"></span>
        <button type="button" onclick="rollSkillTest('force')">Test</button>
        <span id="result-force" class="result-display"></span>
        <small class="desc">Pour actions physiques (soulever, frapper…)</small>
      </div>
      <!-- Agilité -->
      <div class="carac-item">
        <label>Agilité:</label>
        <input id="agilite" type="number" value="10" oninput="updateModificateur('agilite'); updateGlobalAC(); updateSauvegardes();">
        <span id="mod-agilite" class="mod-display"></span>
        <button type="button" onclick="rollSkillTest('agilite')">Test</button>
        <span id="result-agilite" class="result-display"></span>
        <small class="desc">Pour actions rapides (esquive, acrobaties…)</small>
      </div>
      <!-- Endurance -->
      <div class="carac-item">
        <label>Endurance:</label>
        <input id="endurance" type="number" value="10" oninput="updateModificateur('endurance'); updateSauvegardes();">
        <span id="mod-endurance" class="mod-display"></span>
        <button type="button" onclick="rollSkillTest('endurance')">Test</button>
        <span id="result-endurance" class="result-display"></span>
        <small class="desc">Pour résister aux efforts ou poisons</small>
      </div>
      <!-- Présence -->
      <div class="carac-item">
        <label>Présence:</label>
        <input id="presence" type="number" value="10" oninput="updateModificateur('presence'); updateSauvegardes();">
        <span id="mod-presence" class="mod-display"></span>
        <button type="button" onclick="rollSkillTest('presence')">Test</button>
        <span id="result-presence" class="result-display"></span>
        <small class="desc">Pour convaincre ou intimider</small>
      </div>
      <!-- Intelligence -->
      <div class="carac-item">
        <label>Intelligence:</label>
        <input id="intelligence" type="number" value="10" oninput="updateModificateur('intelligence')">
        <span id="mod-intelligence" class="mod-display"></span>
        <button type="button" onclick="rollSkillTest('intelligence')">Test</button>
        <span id="result-intelligence" class="result-display"></span>
        <small class="desc">Pour résoudre des énigmes ou analyser</small>
      </div>
      <!-- Chance -->
      <div class="carac-item">
        <label>Chance:</label>
        <input id="chance" type="number" value="10" oninput="updateModificateur('chance')">
        <span id="mod-chance" class="mod-display"></span>
        <button type="button" onclick="rollSkillTest('chance')">Test</button>
        <span id="result-chance" class="result-display"></span>
        <small class="desc">Pour coups de chance et imprévus</small>
      </div>
    </div>
  </div>

  <!-- Section Équipement -->
  <div class="section">
    <h2>Équipement</h2>
    <!-- Équipements fixes -->
    <label>Main Droite :</label>
    <div style="display: flex; gap: 10px; align-items: center;">
      <input id="equip_mainDroite_nom" type="text" placeholder="Nom" style="flex: 2;">
      <textarea id="equip_mainDroite_description" placeholder="Description / Effets / Bonus" style="flex: 3; resize: vertical;"></textarea>
      <div style="flex: 1;">
        <label style="font-size: 0.8em;">Bonus CA</label>
        <input id="equip_mainDroite_bonus" type="number" class="bonus-ca" value="0" oninput="updateGlobalAC()">
      </div>
    </div>
    <label>Main Gauche :</label>
    <div style="display: flex; gap: 10px; align-items: center;">
      <input id="equip_mainGauche_nom" type="text" placeholder="Nom" style="flex: 2;">
      <textarea id="equip_mainGauche_description" placeholder="Description / Effets / Bonus" style="flex: 3; resize: vertical;"></textarea>
      <div style="flex: 1;">
        <label style="font-size: 0.8em;">Bonus CA</label>
        <input id="equip_mainGauche_bonus" type="number" class="bonus-ca" value="0" oninput="updateGlobalAC()">
      </div>
    </div>
    <label>Dans le Dos :</label>
    <div style="display: flex; gap: 10px; align-items: center;">
      <input id="equip_dansLeDos_nom" type="text" placeholder="Nom" style="flex: 2;">
      <textarea id="equip_dansLeDos_description" placeholder="Description / Effets / Bonus" style="flex: 3; resize: vertical;"></textarea>
      <div style="flex: 1;">
        <label style="font-size: 0.8em;">Bonus CA</label>
        <input id="equip_dansLeDos_bonus" type="number" class="bonus-ca" value="0" oninput="updateGlobalAC()">
      </div>
    </div>
    <!-- Équipements dynamiques -->
    <label>Nombre d'Équipements :</label>
    <input id="nbEquipements" type="number" value="2" min="1" max="20" oninput="genererEquipements()">
    <div id="emplacementsEquipement"></div>
  </div>

  <!-- Section Bourse -->
  <div class="section">
    <h2>Bourse</h2>
    <div style="display: flex; gap: 10px; align-items: center; justify-content: space-between;">
      <div style="display: flex; align-items: center; gap: 5px;">
        <label>PO :</label>
        <input id="bourse_PO" type="number" min="0" value="0" style="width: 60px;">
      </div>
      <div style="display: flex; align-items: center; gap: 5px;">
        <label>PA :</label>
        <input id="bourse_PA" type="number" min="0" value="0" style="width: 60px;">
      </div>
      <div style="display: flex; align-items: center; gap: 5px;">
        <label>PC :</label>
        <input id="bourse_PC" type="number" min="0" value="0" style="width: 60px;">
      </div>
    </div>
    <label>Nombre de Types de Pièces Spéciales :</label>
    <input id="nbPieces" type="number" value="2" min="1" max="20" oninput="genererPieces()">
    <div id="emplacementsPieces"></div>
  </div>

  <!-- Section Sac à Dos -->
  <div class="section">
    <h2>Sac à Dos</h2>
    <label>Nombre d'Objets :</label>
    <input id="nbEmplacements" type="number" value="8" min="1" max="20" oninput="genererEmplacements()">
    <div id="emplacementsSac" class="carac-grid"></div>
  </div>

  <!-- Section Ceinture – Emplacement rapide -->
  <div class="section">
    <h2>Ceinture – Emplacement rapide</h2>
    <label>Nombre d'Objets sur la ceinture :</label>
    <input id="nbCeinture" type="number" value="4" min="1" max="10" oninput="genererCeinture()">
    <div id="emplacementsCeinture" class="carac-grid"></div>
  </div>
  
  <!-- Section Sauvegarder / Charger -->
  <div class="section save-section">
    <h2>Sauvegarder / Charger la Fiche</h2>
    <button onclick="saveCharacter()">Sauvegarder</button>
    <button onclick="loadCharacter()">Charger</button>
  </div>
  
  <script>
    // Mise à jour du titre d'identité
    function updateTitrePerso() {
      const nom = document.getElementById('nomPerso').value || 'Nom';
      const race = document.getElementById('racePerso').value || 'Race';
      const metier = document.getElementById('metierPerso').value || 'Métier';
      document.getElementById('titrePerso').textContent = `${nom} - ${race} ${metier}`;
    }
    
    // Lancer de dés avec animation flash
    function lancerDe(nbFaces) {
      const resultat = Math.floor(Math.random() * nbFaces) + 1;
      const zone = document.getElementById('resultatDe');
      zone.textContent = `🎲 D${nbFaces} : ${resultat}`;
      zone.style.animation = 'flash 0.4s ease';
      setTimeout(() => zone.style.animation = '', 400);
    }
    
    // Changement d'état (modification de l'arrière-plan)
    function setEtat(etat) {
      const body = document.body;
      const couleurs = {
        'normal': '#000',
        'empoisonne': '#003300',
        'comas': '#330033',
        'renverse': '#333300',
        'etourdi': '#003333',
        'endormi': '#222222',
        'immobilise': '#330000'
      };
      body.style.backgroundColor = couleurs[etat] || '#000';
    }
    
    // Calcul des modificateurs (table fixe)
    function calculerModParTable(score) {
      const tableMod = {
        3: -3,
        4: -2, 5: -2,
        6: -1, 7: -1, 8: -1,
        9: 0, 10: 0, 11: 0, 12: 0,
        13: 1, 14: 1, 15: 1,
        16: 2, 17: 2,
        18: 3, 19: 3, 20: 3
      };
      return tableMod[score] !== undefined ? tableMod[score] : 0;
    }
    
    function updateModificateur(carac) {
      const input = document.getElementById(carac);
      const modAffichage = document.getElementById('mod-' + carac);
      const valeur = parseInt(input.value) || 0;
      const mod = calculerModParTable(valeur);
      modAffichage.textContent = "Mod: " + (mod >= 0 ? "+" + mod : mod);
    }
    
    // Mise à jour du niveau en fonction de l'XP cumulée
    function updateNiveauFromXP() {
      const xp = parseInt(document.getElementById('xp').value) || 0;
      const xpSeuils = [0, 10, 50, 110, 190, 290, 410, 550, 710, 890, 1090];
      let niveau = 0;
      for (let i = 0; i < xpSeuils.length; i++) {
        if (xp >= xpSeuils[i]) {
          niveau = i;
        } else {
          break;
        }
      }
      document.getElementById('niveau').value = niveau;
    }
    
    // Mise à jour de la CA globale avec ajout du modificateur d'agilité
    function updateGlobalAC() {
      let baseAC = parseInt(document.getElementById('classeArmure').value) || 0;
      let bonusTotal = 0;
      document.querySelectorAll('.bonus-ca').forEach(function(input) {
        bonusTotal += parseInt(input.value) || 0;
      });
      let agilite = parseInt(document.getElementById('agilite').value) || 0;
      let modAgilite = calculerModParTable(agilite);
      let globalAC = baseAC + bonusTotal + modAgilite;
      document.getElementById('globalAC').value = globalAC;
    }
    
    // Mise à jour des jets de sauvegarde dans l'onglet Identité
    function updateSauvegardes() {
      // Vigueur = mod d'Endurance
      let endurance = parseInt(document.getElementById('endurance').value) || 0;
      document.getElementById('sauv_vigueur').textContent = calculerModParTable(endurance);
      // Réflexes = mod d'Agilité
      let agilite = parseInt(document.getElementById('agilite').value) || 0;
      document.getElementById('sauv_reflexes').textContent = calculerModParTable(agilite);
      // Volonté = mod de Présence
      let presence = parseInt(document.getElementById('presence').value) || 0;
      document.getElementById('sauv_volonte').textContent = calculerModParTable(presence);
    }
    
    // Lancer un test de compétence (d20 + mod), résultat affiché à côté
    function rollSkillTest(carac) {
      const valeur = parseInt(document.getElementById(carac).value) || 0;
      const mod = calculerModParTable(valeur);
      const d20 = Math.floor(Math.random() * 20) + 1;
      const total = d20 + mod;
      document.getElementById("result-" + carac).textContent = d20 + " + " + mod + " = " + total;
    }
    
    // Génération dynamique des équipements supplémentaires
    function genererEquipements() {
      const nb = parseInt(document.getElementById('nbEquipements').value) || 0;
      const conteneur = document.getElementById('emplacementsEquipement');
      conteneur.innerHTML = '';
      for (let i = 1; i <= nb; i++) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Nom équipement ${i}" style="flex: 2;">
          <textarea placeholder="Description / Effets / Bonus" style="flex: 3; resize: vertical;"></textarea>
          <div style="flex: 1;">
            <label style="font-size: 0.8em;">Bonus CA</label>
            <input type="number" class="bonus-ca" value="0" oninput="updateGlobalAC()">
          </div>
        `;
        conteneur.appendChild(bloc);
      }
    }
    
    // Génération dynamique des pièces
    function genererPieces() {
      const nb = parseInt(document.getElementById('nbPieces').value) || 0;
      const conteneur = document.getElementById('emplacementsPieces');
      conteneur.innerHTML = '';
      for (let i = 1; i <= nb; i++) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Nom de la pièce ${i}" style="flex: 3;">
          <input type="number" min="0" value="0" style="flex: 1;">
        `;
        conteneur.appendChild(bloc);
      }
    }
    
    // Génération dynamique des objets dans le Sac à Dos
    function genererEmplacements() {
      const nb = parseInt(document.getElementById('nbEmplacements').value) || 0;
      const conteneur = document.getElementById('emplacementsSac');
      conteneur.innerHTML = '';
      for (let i = 1; i <= nb; i++) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Objet ${i}" style="flex: 3;">
          <input type="number" min="1" value="1" style="flex: 1;">
        `;
        conteneur.appendChild(bloc);
      }
    }
    
    // Génération dynamique des objets pour la Ceinture
    function genererCeinture() {
      const nb = parseInt(document.getElementById('nbCeinture').value) || 0;
      const conteneur = document.getElementById('emplacementsCeinture');
      conteneur.innerHTML = '';
      for (let i = 1; i <= nb; i++) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Objet ceinture ${i}" style="flex: 3;">
          <input type="number" min="1" value="1" style="flex: 1;">
        `;
        conteneur.appendChild(bloc);
      }
    }
    
    // Sauvegarde complète de la fiche dans localStorage
    function saveCharacter() {
      const characterData = {
        identite: {
          nom: document.getElementById('nomPerso').value,
          race: document.getElementById('racePerso').value,
          classe: document.getElementById('classePerso').value,
          metier: document.getElementById('metierPerso').value,
          xp: document.getElementById('xp').value,
          niveau: document.getElementById('niveau').value,
          langues: document.getElementById('langues').value,
          augure: document.getElementById('augure').value
        },
        etat: {
          pvMax: document.getElementById('pvMax').value,
          pvActuel: document.getElementById('pvActuel').value,
          classeArmure: document.getElementById('classeArmure').value,
          globalAC: document.getElementById('globalAC').value
        },
        caracteristiques: {
          force: document.getElementById('force').value,
          agilite: document.getElementById('agilite').value,
          endurance: document.getElementById('endurance').value,
          presence: document.getElementById('presence').value,
          intelligence: document.getElementById('intelligence').value,
          chance: document.getElementById('chance').value
        },
        equipement: {
          fixe: {
            mainDroite: {
              nom: document.getElementById('equip_mainDroite_nom').value,
              description: document.getElementById('equip_mainDroite_description').value,
              bonusCA: document.getElementById('equip_mainDroite_bonus').value
            },
            mainGauche: {
              nom: document.getElementById('equip_mainGauche_nom').value,
              description: document.getElementById('equip_mainGauche_description').value,
              bonusCA: document.getElementById('equip_mainGauche_bonus').value
            },
            dansLeDos: {
              nom: document.getElementById('equip_dansLeDos_nom').value,
              description: document.getElementById('equip_dansLeDos_description').value,
              bonusCA: document.getElementById('equip_dansLeDos_bonus').value
            }
          },
          dynamique: {
            equipements: [],
            pieces: [],
            sac: [],
            ceinture: []
          }
        },
        bourse: {
          PO: document.getElementById('bourse_PO').value,
          PA: document.getElementById('bourse_PA').value,
          PC: document.getElementById('bourse_PC').value
        }
      };
      
      // Équipements dynamiques
      const equipementsContainer = document.getElementById("emplacementsEquipement");
      for (let i = 0; i < equipementsContainer.children.length; i++){
        const bloc = equipementsContainer.children[i];
        const inputs = bloc.querySelectorAll("input, textarea");
        characterData.equipement.dynamique.equipements.push({
          nom: inputs[0].value,
          description: inputs[1].value,
          bonusCA: inputs[2].value
        });
      }
      
      // Pièces dynamiques
      const piecesContainer = document.getElementById("emplacementsPieces");
      for (let i = 0; i < piecesContainer.children.length; i++){
        const bloc = piecesContainer.children[i];
        const inputs = bloc.querySelectorAll("input");
        characterData.equipement.dynamique.pieces.push({
          nom: inputs[0].value,
          quantite: inputs[1].value
        });
      }
      
      // Objets dans le Sac à Dos
      const sacContainer = document.getElementById("emplacementsSac");
      for (let i = 0; i < sacContainer.children.length; i++){
        const bloc = sacContainer.children[i];
        const inputs = bloc.querySelectorAll("input");
        characterData.equipement.dynamique.sac.push({
          nom: inputs[0].value,
          quantite: inputs[1].value
        });
      }
      
      // Objets dans la Ceinture
      const ceintureContainer = document.getElementById("emplacementsCeinture");
      for (let i = 0; i < ceintureContainer.children.length; i++){
        const bloc = ceintureContainer.children[i];
        const inputs = bloc.querySelectorAll("input");
        characterData.equipement.dynamique.ceinture.push({
          nom: inputs[0].value,
          quantite: inputs[1].value
        });
      }
      
      localStorage.setItem("characterData", JSON.stringify(characterData));
      alert("Fiche sauvegardée !");
    }
    
    /* Chargement complet de la fiche depuis localStorage */
    function loadCharacter() {
      const data = localStorage.getItem("characterData");
      if (!data) {
        alert("Aucune sauvegarde trouvée !");
        return;
      }
      const characterData = JSON.parse(data);
      
      // Identité
      document.getElementById('nomPerso').value = characterData.identite.nom;
      document.getElementById('racePerso').value = characterData.identite.race;
      document.getElementById('classePerso').value = characterData.identite.classe;
      document.getElementById('metierPerso').value = characterData.identite.metier;
      document.getElementById('xp').value = characterData.identite.xp;
      document.getElementById('niveau').value = characterData.identite.niveau;
      document.getElementById('langues').value = characterData.identite.langues;
      document.getElementById('augure').value = characterData.identite.augure;
      
      // État
      document.getElementById('pvMax').value = characterData.etat.pvMax;
      document.getElementById('pvActuel').value = characterData.etat.pvActuel;
      document.getElementById('classeArmure').value = characterData.etat.classeArmure;
      document.getElementById('globalAC').value = characterData.etat.globalAC;
      
      // Caractéristiques
      document.getElementById('force').value = characterData.caracteristiques.force;
      document.getElementById('agilite').value = characterData.caracteristiques.agilite;
      document.getElementById('endurance').value = characterData.caracteristiques.endurance;
      document.getElementById('presence').value = characterData.caracteristiques.presence;
      document.getElementById('intelligence').value = characterData.caracteristiques.intelligence;
      document.getElementById('chance').value = characterData.caracteristiques.chance;
      
      updateTitrePerso();
      updateNiveauFromXP();
      updateModificateur('force');
      updateModificateur('agilite');
      updateModificateur('endurance');
      updateModificateur('presence');
      updateModificateur('intelligence');
      updateModificateur('chance');
      updateGlobalAC();
      updateSauvegardes();
      
      // Équipements fixes
      document.getElementById('equip_mainDroite_nom').value = characterData.equipement.fixe.mainDroite.nom;
      document.getElementById('equip_mainDroite_description').value = characterData.equipement.fixe.mainDroite.description;
      document.getElementById('equip_mainDroite_bonus').value = characterData.equipement.fixe.mainDroite.bonusCA;
      
      document.getElementById('equip_mainGauche_nom').value = characterData.equipement.fixe.mainGauche.nom;
      document.getElementById('equip_mainGauche_description').value = characterData.equipement.fixe.mainGauche.description;
      document.getElementById('equip_mainGauche_bonus').value = characterData.equipement.fixe.mainGauche.bonusCA;
      
      document.getElementById('equip_dansLeDos_nom').value = characterData.equipement.fixe.dansLeDos.nom;
      document.getElementById('equip_dansLeDos_description').value = characterData.equipement.fixe.dansLeDos.description;
      document.getElementById('equip_dansLeDos_bonus').value = characterData.equipement.fixe.dansLeDos.bonusCA;
      
      // Équipements dynamiques
      const equipementsContainer = document.getElementById("emplacementsEquipement");
      equipementsContainer.innerHTML = "";
      characterData.equipement.dynamique.equipements.forEach(function(equip, index) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Nom équipement ${index+1}" style="flex: 2;" value="${equip.nom}">
          <textarea placeholder="Description / Effets / Bonus" style="flex: 3; resize: vertical;">${equip.description}</textarea>
          <div style="flex: 1;">
            <label style="font-size: 0.8em;">Bonus CA</label>
            <input type="number" class="bonus-ca" value="${equip.bonusCA}" oninput="updateGlobalAC()">
          </div>
        `;
        equipementsContainer.appendChild(bloc);
      });
      
      // Pièces dynamiques
      const piecesContainer = document.getElementById("emplacementsPieces");
      piecesContainer.innerHTML = "";
      characterData.equipement.dynamique.pieces.forEach(function(piece, index) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Nom de la pièce ${index+1}" style="flex: 3;" value="${piece.nom}">
          <input type="number" min="0" value="${piece.quantite}" style="flex: 1;">
        `;
        piecesContainer.appendChild(bloc);
      });
      
      // Sac à Dos
      const sacContainer = document.getElementById("emplacementsSac");
      sacContainer.innerHTML = "";
      characterData.equipement.dynamique.sac.forEach(function(objet, index) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Objet ${index+1}" style="flex: 3;" value="${objet.nom}">
          <input type="number" min="1" value="${objet.quantite}" style="flex: 1;">
        `;
        sacContainer.appendChild(bloc);
      });
      
      // Ceinture
      const ceintureContainer = document.getElementById("emplacementsCeinture");
      ceintureContainer.innerHTML = "";
      characterData.equipement.dynamique.ceinture.forEach(function(objet, index) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Objet ceinture ${index+1}" style="flex: 3;" value="${objet.nom}">
          <input type="number" min="1" value="${objet.quantite}" style="flex: 1;">
        `;
        ceintureContainer.appendChild(bloc);
      });
      
      // Bourse
      document.getElementById('bourse_PO').value = characterData.bourse.PO;
      document.getElementById('bourse_PA').value = characterData.bourse.PA;
      document.getElementById('bourse_PC').value = characterData.bourse.PC;
      
      alert("Fiche chargée !");
    }
    
    /* Génération dynamique des équipements supplémentaires */
    function genererEquipements() {
      const nb = parseInt(document.getElementById('nbEquipements').value) || 0;
      const conteneur = document.getElementById('emplacementsEquipement');
      conteneur.innerHTML = '';
      for (let i = 1; i <= nb; i++) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Nom équipement ${i}" style="flex: 2;">
          <textarea placeholder="Description / Effets / Bonus" style="flex: 3; resize: vertical;"></textarea>
          <div style="flex: 1;">
            <label style="font-size: 0.8em;">Bonus CA</label>
            <input type="number" class="bonus-ca" value="0" oninput="updateGlobalAC()">
          </div>
        `;
        conteneur.appendChild(bloc);
      }
    }
    
    function genererPieces() {
      const nb = parseInt(document.getElementById('nbPieces').value) || 0;
      const conteneur = document.getElementById('emplacementsPieces');
      conteneur.innerHTML = '';
      for (let i = 1; i <= nb; i++) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Nom de la pièce ${i}" style="flex: 3;">
          <input type="number" min="0" value="0" style="flex: 1;">
        `;
        conteneur.appendChild(bloc);
      }
    }
    
    function genererEmplacements() {
      const nb = parseInt(document.getElementById('nbEmplacements').value) || 0;
      const conteneur = document.getElementById('emplacementsSac');
      conteneur.innerHTML = '';
      for (let i = 1; i <= nb; i++) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Objet ${i}" style="flex: 3;">
          <input type="number" min="1" value="1" style="flex: 1;">
        `;
        conteneur.appendChild(bloc);
      }
    }
    
    function genererCeinture() {
      const nb = parseInt(document.getElementById('nbCeinture').value) || 0;
      const conteneur = document.getElementById('emplacementsCeinture');
      conteneur.innerHTML = '';
      for (let i = 1; i <= nb; i++) {
        const bloc = document.createElement('div');
        bloc.style.display = 'flex';
        bloc.style.gap = '10px';
        bloc.style.alignItems = 'center';
        bloc.style.borderBottom = '1px solid #555';
        bloc.style.padding = '5px 0';
        bloc.style.marginBottom = '5px';
        bloc.innerHTML = `
          <input type="text" placeholder="Objet ceinture ${i}" style="flex: 3;">
          <input type="number" min="1" value="1" style="flex: 1;">
        `;
        conteneur.appendChild(bloc);
      }
    }
    
    /* Initialisation générale au chargement */
    window.onload = function() {
      genererEquipements();
      genererPieces();
      genererEmplacements();
      genererCeinture();
      
      updateModificateur('force');
      updateModificateur('agilite');
      updateModificateur('endurance');
      updateModificateur('presence');
      updateModificateur('intelligence');
      updateModificateur('chance');
      
      updateTitrePerso();
      updateNiveauFromXP();
      updateGlobalAC();
      updateSauvegardes();
    };
  </script>
</body>
</html>
