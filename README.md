# Security Configuration for Spring Boot Application

This project contains the security configuration for a Spring Boot application using Spring Security. The configuration includes basic HTTP authentication, stateless session management, and custom authentication providers.

---

## Key Features

- **Stateless Session Management:** Ensures each request is authenticated independently.
- **Custom Authentication Provider:** Uses `DaoAuthenticationProvider` to authenticate users.
- **Basic Authentication:** Implements HTTP Basic Authentication for simplicity.
- **CSRF Disabled:** Cross-Site Request Forgery protection is disabled for APIs (use with caution).

---

## Code Overview

### `SecurityConfig` Class

This class configures the security settings for the application.

### Annotations Used

- `@Configuration`: Marks this class as a source of bean definitions.
- `@EnableWebSecurity`: Enables Spring Security for the application.

---

### 1. Security Filter Chain (`securityFilterChain`)
- Disables CSRF.
- Requires authentication for all HTTP requests.
- Configures HTTP Basic authentication.
- Configures the application to use **stateless** sessions.

```java
@Bean
public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
    http.csrf(customizer -> customizer.disable());
    http.authorizeHttpRequests(request -> request.anyRequest().authenticated());
    http.httpBasic(Customizer.withDefaults());
    http.sessionManagement(session -> session.sessionCreationPolicy(SessionCreationPolicy.STATELESS));
    return http.build();
}

```
# Getting Started

## Clone the Repository

Clone the repository to your local machine:

```bash
git clone https://github.com/rajsrm2021/Security-Configuration-for-Spring-Boot-Application.git

