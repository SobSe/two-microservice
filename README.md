# Кейс Два микросервиса
Реализовано два микросервиса.
1. [user-service](https://github.com/SobSe/user-service.git) Хранит информацию о пользователях и ролях пользователей.  Используется база данных Posgtre SQL. Используется OAuth2 авторизация.
2. [client-user-service](https://github.com/SobSe/client-user-service.git) Клиент первого сервиса. Получает информацию о списке пользователей. Для соединения первым микросервисом используется RestClient.

# Keycloak
Сервисом аутентификации, авторизации является Keycloak. [Настройки Keycloak.](./realm-export.json) 

Команда запуска:

	docker run -itd -p 8082:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin -v ./config/keycloak/import:/opt/keycloak/data/import quay.io/keycloak/keycloak:23.0.7 start-dev —import-realm

Для корректной работы в Keycloak необходимо зайти в консоль realm userservice в клиенте userservice на закладке Credentials сформировать Client secret. Сформированный токен записать в настройках микросервиса client-user-service в параметр client-secret.