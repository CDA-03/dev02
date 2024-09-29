# Challenge : Conversion de Nombres

## Objectif

🚀 Créez une application React permettant de convertir des nombres entre décimal et binaire.

### Configuration Initiale avec Vite

1. **Créez un nouveau projet Vite** :
   ```bash
   npm create vite@latest conversion-app -- --template react
   cd conversion-app
   npm install
   ```

2. **Organisez votre structure de dossier** :
   - Créez un dossier `components` dans `src`.

### Partie 1 : Conversion Décimal vers Binaire

**Exigences :**

- Créez deux champs de saisie :
  - Un pour les nombres décimaux.
  - Un autre pour les nombres binaires.

**Hiérarchie des composants** :
```plaintext
    App
   .    .
 .        .
Form      Form
```

### Code de Base

#### `src/App.jsx`

```javascript
import React, { useState } from 'react';
import Form from './components/Form';

function App() {
  const [decimalValue, setDecimalValue] = useState('');
  const [binaryValue, setBinaryValue] = useState('');

  const handleChange = (value, type) => {
    if (type === 'decimal') {
      const binary = parseInt(value, 10).toString(2);
      setBinaryValue(binary);
      setDecimalValue(value);
    } else if (type === 'binary') {
      const decimal = parseInt(value, 2).toString(10);
      setDecimalValue(decimal);
      setBinaryValue(value);
    }
  };

  return (
    <div>
      <h1>Convertisseur Décimal/Binaire</h1>
      <Form
        value={decimalValue}
        binaryValue={binaryValue}
        onChangeBase={handleChange}
      />
    </div>
  );
}

export default App;
```

#### `src/components/Form.jsx`

```javascript
import React from 'react';

function Form({ value, binaryValue, onChangeBase }) {
  return (
    <div>
      <label>
        Nombre décimal :
        <input
          type="number"
          value={value}
          onChange={(e) => onChangeBase(e.target.value, 'decimal')}
          placeholder="Entrez un nombre décimal"
        />
      </label>
      <br />
      <label>
        Nombre binaire :
        <input
          type="text"
          value={binaryValue}
          onChange={(e) => onChangeBase(e.target.value, 'binary')}
          placeholder="Entrez un nombre binaire"
        />
      </label>
    </div>
  );
}

export default Form;
```

### Partie 2 : Conversion Binaire vers Décimal

Dans la logique de `handleChange` du composant `App`, la conversion binaire vers décimal est déjà gérée grâce à l'utilisation de `parseInt` avec une base de 2. Ainsi, si l'utilisateur entre un nombre binaire dans le champ correspondant, la conversion se fait automatiquement.

### Exécution de l'Application

1. Lancez le serveur de développement :
   ```bash
   npm run dev
   ```

2. Ouvrez votre navigateur à l'adresse `http://localhost:5173` pour voir l'application en action.

### Résumé

- **Organisation du Code** : Utilisation d'un dossier `components` pour structurer les composants.
- **Remontée d'État** : La logique de conversion est gérée dans le composant parent `App`, assurant un flux de données unidirectionnel.
- **Réactivité** : Les conversions se font en temps réel lors de la saisie de l'utilisateur.

### Challenge Additionnel

Pour aller plus loin, vous pouvez ajouter :
- Une gestion des erreurs pour vérifier si les entrées sont valides.
- Un historique des conversions effectuées.
- Des styles CSS pour améliorer l'interface utilisateur.
