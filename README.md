import java.io.*;
import java.util.*;

public class LibraryManagementSystem {

    public static void main(String[] args) {
        text();
        loading();
        menu();
    }

    public static void loading() {
        System.out.println("\n\n\n\n\n\t\t\t\t\t\tPlease Wait...");
        try {
            for (int i = 10; i <= 100; i += 10) {
                System.out.printf("\t\t\t\t\t\tLoading %d%%\r", i);
                Thread.sleep(200);
            }
        } catch (InterruptedException e) {
            System.err.println("Error during loading: " + e.getMessage());
        }
        System.out.flush();
    }

    public static void text() {
        System.out.println("\n\n\n\n\n\t\t\t\t||Welcome to the Library Management System!||\n");
        System.out.println("\t\t\t\t===========================================\n\n");
        System.out.println("\t\t\t ||We're here to help you manage your library efficiently.||\n");
        System.out.println("\t\t\t\t||Please login to get started.||\n\n\n");
    }

    public static void menu() {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("----------------------------------");
            System.out.println(">>> Library Management System <<< ");
            System.out.println("----------------------------------\n");
            System.out.println("> 1. User Management Panel ");
            System.out.println("> 2. Book Management Panel ");
            System.out.println("> 3. Exit\n");
            System.out.print("> Enter the number & hit ENTER: ");

            int number = scanner.nextInt();
            scanner.nextLine(); // Clear buffer

            switch (number) {
                case 1:
                    userPanel();
                    break;
                case 2:
                    bookPanel();
                    break;
                case 3:
                    System.out.println("Exiting Program. Goodbye!");
                    System.exit(0);
                default:
                    System.out.println("\n>>> Invalid Input! Redirecting to Main Menu... <<<\n");
            }
        }
    }

    public static void userPanel() {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("-----------------------------------------------");
            System.out.println(">>> Library Management System - User Panel <<< ");
            System.out.println("-----------------------------------------------\n");
            System.out.println("> 1. Add User ");
            System.out.println("> 2. Search User ");
            System.out.println("> 3. Delete User ");
            System.out.println("> 4. List Users ");
            System.out.println("> 5. Open Main Menu ");
            System.out.println("> 6. Close the Program... \n");

            System.out.print("> Enter the number & hit ENTER: ");
            int number = scanner.nextInt();
            scanner.nextLine(); // Clear buffer

            switch (number) {
                case 1:
                    addUser();
                    break;
                case 2:
                    searchUser();
                    break;
                case 3:
                    deleteUser();
                    break;
                case 4:
                    listUsers();
                    break;
                case 5:
                    return;
                case 6:
                    System.out.println("Exiting Program. Goodbye!");
                    System.exit(0);
                default:
                    System.out.println("\n>>> Invalid Input! Redirecting to User Panel... <<<\n");
            }
        }
    }

    public static void bookPanel() {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("-----------------------------------------------");
            System.out.println(">>> Library Management System - Book Panel <<< ");
            System.out.println("-----------------------------------------------\n");
            System.out.println("> 1. Add Book ");
            System.out.println("> 2. List Books ");
            System.out.println("> 3. Search Book ");
            System.out.println("> 4. Delete Book ");
            System.out.println("> 5. Open Main Menu ");
            System.out.println("> 6. Close the Program... \n");

            System.out.print("> Enter the number & hit ENTER: ");
            int number = scanner.nextInt();
            scanner.nextLine(); // Clear buffer

            switch (number) {
                case 1:
                    addBook();
                    break;
                case 2:
                    listBooks();
                    break;
                case 3:
                    searchBook();
                    break;
                case 4:
                    deleteBook();
                    break;
                case 5:
                    return;
                case 6:
                    System.out.println("Exiting Program. Goodbye!");
                    System.exit(0);
                default:
                    System.out.println("\n>>> Invalid Input! Redirecting to Book Panel... <<<\n");
            }
        }
    }

    public static void addUser() {
        // Implementation for adding a user
        System.out.println("Add user functionality under construction.");
    }

    public static void searchUser() {
        // Implementation for searching a user
        System.out.println("Search user functionality under construction.");
    }

    public static void deleteUser() {
        // Implementation for deleting a user
        System.out.println("Delete user functionality under construction.");
    }

    public static void listUsers() {
        // Implementation for listing users
        System.out.println("List users functionality under construction.");
    }

    public static void addBook() {
        // Implementation for adding a book
        System.out.println("Add book functionality under construction.");
    }

    public static void listBooks() {
        // Implementation for listing books
        System.out.println("List books functionality under construction.");
    }

    public static void searchBook() {
        // Implementation for searching a book
        System.out.println("Search book functionality under construction.");
    }

    public static void deleteBook() {
        // Implementation for deleting a book
        System.out.println("Delete book functionality under construction.");
    }
}
