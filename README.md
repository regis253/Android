Blutter est un outil puissant pour la rétro-ingénierie des applications Flutter, et vous pouvez l'exécuter directement sur votre appareil Android avec Termux. Voici un guide complet pour installer, utiliser et mettre à jour Blutter dans Termux. C'est parti !

🎥 Guide vidéo :
Bien qu'il existe des guides vidéo disponibles, ils peuvent ne pas être très utiles car ils sont obsolètes :

Ancien guide vidéo
Nouveau guide vidéo
Mais ne vous inquiétez pas, ce guide textuel vous permettra de démarrer en douceur ! 😄

🖥 Exigences :
Assurez-vous que les éléments suivants sont installés dans Termux :

pkg i -y git python
👉 Étapes d'installation :
Accédez au répertoire personnel :

cd $HOME
Cloner le référentiel Blutter :

git clone https://github.com/dedshit/blutter-termux.git
Installer les dépendances :

pip install requests pyelftools
pkg install -y cmake ninja build-essential pkg-config libicu capstone fmt
Entrez dans le répertoire Blutter :

cd blutter-termux
✨ Utilisation :
Accédez au répertoire Blutter :

cd $HOME
pwd   # To check if you're in the correct directory
Si vous n'êtes pas dans le répertoire Blutter, naviguez-y :

cd blutter-termux
Exécutez Blutter :

python3 blutter.py path/to/app/lib/arm64-v8a out_dir
Ou alternativement :

python blutter.py path/to/app/lib/arm64-v8a out_dir
🖥 Exemple de commande :
Par exemple, si vous souhaitez extraire des fichiers d’une application :

python3 blutter.py /storage/emulated/0/MT2/lib_edit/ /storage/emulated/0/MT2/lib_edit/blutter-output/
✨ Remarques importantes :
Saisissez les commandes une par une :

Appuyez enteraprès chaque commande.
Vérifiez votre répertoire personnel :

Votre $HOMErépertoire dans Termux devrait être :
   /data/data/com.termux/files/home
Correction des erreurs :

Si vous rencontrez des erreurs liées à no member named 'format' in namespace std, exécutez la commande suivante dans le répertoire Blutter :
   find -type f -exec sed -i 's/std::format/fmt::format/g' {} +
👉 Mise à jour de Blutter :
Mises à jour automatiques :
chaque fois que vous exécutez blutter.py, il recherche automatiquement les mises à jour et les applique, y compris les modifications nécessaires à std::format.

Mise à jour manuelle (si nécessaire) : si Blutter ne se met pas à jour ou si vous avez effectué des modifications manuelles, vous devrez peut-être réinitialiser et récupérer les dernières mises à jour :

  git reset --hard && git pull
🥷 Supplément : Gestion des erreurs de version de développement Dart 🐛
Si vous utilisez une version de développement Dart comprise entre 3.0.0-30.devet 3.0.0-51.dev, utilisez la mise à jour suivante :

git clone https://github.com/AbhiTheModder/blutter-termux -b 3.0.0-XX.0.dev blutter-termux-dev
Cela créera un nouveau répertoire nommé blutter-termux-devdans votre répertoire actuel Termux, spécifiquement pour ces versions Dart.

👷‍♂️ Astuce rapide pour utiliser (b)lutter :
Si vous utilisez des versions de Dart partageant les mêmes snapshots (comme Dart 3.4.x), vous pouvez éviter de recompiler Blutter en utilisant l' --dart-versionoption. Par exemple :

--dart-version 3.4.1_android_arm64
Ce drapeau vous permet d'utiliser une version compilée pour d'autres versions comme 3.4.2 ou 3.4.3 sans avoir besoin de recompiler ! 😎

Et voilà ! Vous êtes prêt à utiliser Blutter dans Termux pour vos besoins de rétro-ingénierie.

Bonne marche arrière ! 🔧💻
