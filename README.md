package login;

import java.util.Scanner;

public class User {
    String handle;
    String secret;

    public User(String handle, String secret) {
        this.handle = handle;
        this.secret = secret;
    }

    public boolean verify(String h, String s) {
        return handle.equals(h) && secret.equals(s);
    }
}

public class LoginSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        User user = new User("admin", "1234");
        int tries = 0;

        while (tries < 3) {
            System.out.print("Provide identifier: ");
            String h = sc.nextLine();

            System.out.print("Provide passcode: ");
            String s = sc.nextLine();

            if (user.verify(h, s)) {
                System.out.println("Access granted");
                break;
            } else {
                System.out.println("Access denied");
                tries++;
            }
        }

        if (tries == 3) {
            System.out.println("Maximum attempts reached. Entry blocked.");
        }
    }
}
