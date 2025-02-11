# Système de Recommandation en Temps Réel avec Apache Kafka et Hadoop

## 📌 Description
Ce projet implémente un système de recommandation en temps réel pour une plateforme de streaming, en utilisant **Apache Kafka** pour le traitement des événements en temps réel et **Hadoop** pour le stockage des données. 

## 📂 Structure du projet
```
├── kafka-3.7.2-src/            # Code source de Kafka (à compiler)
├── kafka_2.13-3.7.2/           # Distribution binaire de Kafka (après compilation)
├── hadoop/                     # Dossier de configuration Hadoop
├── scripts/                    # Scripts d'automatisation
├── data/                       # Données utilisées pour les tests
└── README.md                   # Documentation du projet
```

## ⚙️ Installation et Configuration

### 1️⃣ Installation de Kafka
```sh
# Cloner le projet
git clone https://github.com//system-recommandations.git

# Compiler Kafka (si non pré-compilé)
cd kafka-3.7.2-src
./gradlew clean releaseTarGz -PscalaVersion=2.13.12

# Extraire la distribution binaire
cd ..
tar -xzf kafka-3.7.2-src/core/build/distributions/kafka_2.13-3.7.2.tgz
```

### 2️⃣ Démarrer Zookeeper et Kafka
```sh
# Lancer Zookeeper
./kafka_2.13-3.7.2/bin/zookeeper-server-start.sh -daemon kafka_2.13-3.7.2/config/zookeeper.properties

# Lancer Kafka
./kafka_2.13-3.7.2/bin/kafka-server-start.sh -daemon kafka_2.13-3.7.2/config/server.properties
```

### 3️⃣ Création d'un topic Kafka
```sh
./kafka_2.13-3.7.2/bin/kafka-topics.sh --create --topic user-events --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
```

### 4️⃣ Vérification des topics Kafka
```sh
./kafka_2.13-3.7.2/bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```

### 5️⃣ Production et consommation de messages
#### 🚀 Envoyer des messages
```sh
./kafka_2.13-3.7.2/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic user-events
```
Ensuite, tapez des messages et appuyez sur **Entrée**.

#### 🔍 Lire les messages
```sh
./kafka_2.13-3.7.2/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic user-events --from-beginning
```

## 📊 Intégration avec Hadoop
Ce projet stocke les événements Kafka dans **HDFS** à l'aide de **Kafka Connect HDFS Sink**.

1. Configurer Hadoop et HDFS.
2. Utiliser un connecteur Kafka Connect HDFS.
3. Consommer les données stockées pour analyse et recommandations.

## 📌 Objectifs du projet
- 🚀 Implémenter un système de recommandation en temps réel basé sur les événements utilisateurs.
- 🔗 Intégrer Kafka avec Hadoop pour la persistance des logs.
- 📊 Analyser les événements utilisateurs pour générer des recommandations optimisées.

## 🛠 Technologies utilisées
- **Apache Kafka 3.7.2** 🚀
- **Scala 2.13.12** 🛠️
- **Hadoop** 🏗️
- **PySpark** 🔥
- **Google Colab** ⚡

## 📌 Auteurs
- [Votre Nom](https://github.com/votre-profil)

## 📜 Licence
Ce projet est sous licence libre  ,  par ailleurs je ne suis responsable d'aucune  utilisation en  production
