# Orçamento API – Backend Spring Boot

[![Status](https://img.shields.io/badge/status-finalizado-green)]()
[![License](https://img.shields.io/badge/licença-Privado-red)]()
[![Java](https://img.shields.io/badge/Java-21-blue?logo=java)]()
[![Kotlin](https://img.shields.io/badge/Kotlin-JVM-lightgrey?logo=kotlin)]()
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen?logo=springboot)]()
[![Spring Data JPA](https://img.shields.io/badge/Spring%20Data%20JPA-ORM-blue?logo=spring)]()
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-DB-316192?logo=postgresql)]()
[![Maven](https://img.shields.io/badge/Maven-build-red?logo=apachemaven)]()
[![Lombok](https://img.shields.io/badge/Lombok-annotation-orange?logo=java)]()
[![Git](https://img.shields.io/badge/Git-version%20control-orange?logo=git)]()
[![GitHub](https://img.shields.io/badge/GitHub-repo-181717?logo=github)]()


API para **gerenciamento de orçamentos** com cálculo de **ICMS por estado** e controle básico de usuários.  
Desenvolvida em Kotlin/Java com Spring Boot 3, persistência em PostgreSQL e build Maven.

## Índice

- [Pré‑requisitos](#pré‑requisitos)
- [Configurando o banco](#configurando-o-banco)
- [Como rodar](#como-rodar)
- [Estrutura de pastas](#estrutura-de-pastas)
- [Principais endpoints](#principais-endpoints)
- [Personalização](#personalização)
- [Créditos](#créditos)

## Pré‑requisitos

| Ferramenta | Versão sugerida |
|------------|-----------------|
| JDK | 21 LTS |
| Maven | 3.9+ |
| PostgreSQL | 15+ |

## Configurando o banco

Edite `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/money
spring.datasource.username=postgres
spring.datasource.password={sua_senha}
```

> Opcional: use variáveis de ambiente ou profiles (`application-prod.properties`) para separar dev e produção.

## Como rodar

```bash
# 1. build
./mvnw clean package

# 2. executar
java -jar target/orcamento-0.0.1-SNAPSHOT.jar
```

Por padrão, a aplicação sobe em <http://localhost:8080>.

### Execução em modo dev

Use o Spring DevTools já incluso:

```bash
./mvnw spring-boot:run
```

## Estrutura de pastas
```text
teste-main/
├── pom.xml
├── src/
│   ├── main/
│   │   ├── kotlin/com/finan/orcamento/
│   │   │   ├── OrcamentoApplication.kt      (# classe principal)
│   │   │   ├── controller/
│   │   │   ├── model/
│   │   │   ├── repositories/
│   │   │   └── service/
│   │   └── resources/
│   │       └── application.properties
│   └── test/
└── README.md  (este arquivo)
```

## Principais endpoints

| Método | Rota | Descrição |
|--------|------|-----------|
| `POST` | `/orcamentos` | Cria um novo orçamento |
| `GET`  | `/orcamentos` | Lista orçamentos |
| `GET`  | `/orcamentos/{id}` | Consulta orçamento |
| `POST` | `/usuarios` | Cria usuário |
| `POST` | `/auth/login`* | (caso adicione segurança) |

\* Endpoints de autenticação podem ser ajustados conforme implantação de Spring Security.

## Personalização

- **Estados/ICMS:** implemente novas classes que estendam `IcmsStrategy`.
- **Banco:** altere `postgresql` para qualquer BD suportado pelo Spring Data.
- **Segurança:** adicione `spring-boot-starter-security` e configure JWT ou session.

## Créditos

- **Spring Boot** & **Spring Data JPA** – Pivotal / VMware  
- **Lombok** – Projeto Open Source  
- **PostgreSQL** – The PostgreSQL Global Development Group  

---

> Projeto de estudo. Sinta‑se livre para adaptar conforme sua necessidade.
