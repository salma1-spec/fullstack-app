# Étape 1 : Build du projet Spring Boot avec Maven
FROM maven:3.9.6-eclipse-temurin-17 AS build

# Définir le répertoire de travail
WORKDIR /app

# Copier tous les fichiers du projet Spring Boot dans le conteneur
COPY . .

# Lancer la compilation du projet (génère un fichier .jar)
RUN mvn clean package -DskipTests


# Étape 2 : Exécuter l'application Java
FROM eclipse-temurin:17-jdk

# Répertoire de travail pour l'exécution
WORKDIR /app

# Copier le .jar compilé depuis l'étape précédente
COPY --from=build /app/target/*.jar app.jar

# Exposer le port 8080 (port standard de Spring Boot)
EXPOSE 8080

# Démarrer l'application
ENTRYPOINT ["java", "-jar", "app.jar"]
