# springbootproject
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.*;

@SpringBootApplication
public class JwtAuthenticationApplication {

    public static void main(String[] args) {
        SpringApplication.run(JwtAuthenticationApplication.class, args);
    }
}

@RestController
@RequestMapping("/api")
public class AuthenticationController {

    @PostMapping("/login")
    public String login(@RequestBody UserCredentials userCredentials) {
        // Validate the username and password
        if (isValidUser(userCredentials.getUsername(), userCredentials.getPassword())) {
            // Generate and return a JWT token
            String token = generateToken(userCredentials.getUsername());
            return token;
        } else {
            return "Invalid credentials";
        }
    }

    private boolean isValidUser(String username, String password) {
        // Implement your validation logic here (e.g., check against a user database)
        // Return true if the username and password are valid, otherwise false
        return true;
    }

    private String generateToken(String username) {
        // Implement your JWT token generation logic here
        // Generate a token using a library like 'jjwt' and return it
        return "your_generated_jwt_token";
    }
}

class UserCredentials {
    private String username;
    private String password;

    // Getters and setters

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }
}
