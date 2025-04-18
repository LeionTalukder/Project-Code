import java.util.*;

public class LibraryManagementSystem {

    private static final Scanner scanner = new Scanner(System.in);
    private static final HashMap<String, String> users = new HashMap<>();
    private static final ArrayList<Book> books = new ArrayList<>();
    private static String currentUser = null;

    public static void main(String[] args) {
        welcomeScreen();
    }

    private static void welcomeScreen() {
        while (true) {
            System.out.println("\n=== Welcome to the Library System ===");
            System.out.println("1. Register");
            System.out.println("2. Login");
            System.out.println("3. Exit");
            System.out.print("Choose an option: ");

            String choice = scanner.nextLine();

            switch (choice) {
                case "1":
                    register();
                    break;
                case "2":
                    login();
                    break;
                case "3":
                    System.out.println("Goodbye!");
                    return;
                default:
                    System.out.println("Invalid input. Try again.");
            }
        }
    }

    private static void register() {
        System.out.print("Enter a new username: ");
        String username = scanner.nextLine();

        if (users.containsKey(username)) {
            System.out.println("Username already exists. Try a different one.");
            return;
        }

        System.out.print("Enter a password: ");
        String password = scanner.nextLine();

        users.put(username, password);
        System.out.println("Registration successful! You can now log in.");
    }

    private static void login() {
        System.out.print("Enter your username: ");
        String username = scanner.nextLine();

        System.out.print("Enter your password: ");
        String password = scanner.nextLine();

        if (users.containsKey(username) && users.get(username).equals(password)) {
            currentUser = username;
            System.out.println("Login successful! Welcome, " + currentUser + "!");
            mainMenu();
        } else {
            System.out.println("Invalid username or password.");
        }
    }

    private static void mainMenu() {
        while (true) {
            System.out.println("\n=== Main Menu ===");
            System.out.println("1. Book Panel");
            System.out.println("2. Logout");
            System.out.print("Choose an option: ");

            String choice = scanner.nextLine();

            switch (choice) {
                case "1":
                    bookPanel();
                    break;
                case "2":
                    System.out.println("Logged out successfully.");
                    currentUser = null;
                    return;
                default:
                    System.out.println("Invalid input. Try again.");
            }
        }
    }

    private static void bookPanel() {
        while (true) {
            System.out.println("\n--- Book Panel ---");
            System.out.println("1. Add Book");
            System.out.println("2. Remove Book");
            System.out.println("3. Search Book");
            System.out.println("4. Display All Books");
            System.out.println("5. Checkout Book");
            System.out.println("6. Return Book");
            System.out.println("7. Back to Main Menu");
            System.out.print("Choose an option: ");

            String choice = scanner.nextLine();

            switch (choice) {
                case "1":
                    addBook();
                    break;
                case "2":
                    removeBook();
                    break;
                case "3":
                    searchBook();
                    break;
                case "4":
                    displayBooks();
                    break;
                case "5":
                    checkoutBook();
                    break;
                case "6":
                    returnBook();
                    break;
                case "7":
                    return;
                default:
                    System.out.println("Invalid input. Try again.");
            }
        }
    }

    // ==== Book Methods ====

    private static void addBook() {
        System.out.print("Enter book title: ");
        String title = scanner.nextLine();

        System.out.print("Enter author name: ");
        String author = scanner.nextLine();

        books.add(new Book(title, author));
        System.out.println("Book added successfully.");
    }

    private static void removeBook() {
        System.out.print("Enter book title to remove: ");
        String title = scanner.nextLine();

        Book book = findBook(title);
        if (book != null) {
            books.remove(book);
            System.out.println("Book removed.");
        } else {
            System.out.println("Book not found.");
        }
    }

    private static void searchBook() {
        System.out.print("Enter book title to search: ");
        String title = scanner.nextLine();

        Book book = findBook(title);
        if (book != null) {
            System.out.println("Found: " + book);
        } else {
            System.out.println("Book not found.");
        }
    }

    private static void displayBooks() {
        if (books.isEmpty()) {
            System.out.println("No books available.");
            return;
        }

        System.out.println("\n--- Available Books ---");
        for (Book book : books) {
            System.out.println(book);
        }
    }

    private static void checkoutBook() {
        System.out.print("Enter book title to checkout: ");
        String title = scanner.nextLine();

        Book book = findBook(title);
        if (book != null && !book.isCheckedOut) {
            book.isCheckedOut = true;
            book.checkedOutBy = currentUser;
            System.out.println("Book checked out successfully.");
        } else if (book != null && book.isCheckedOut) {
            System.out.println("Book is already checked out by " + book.checkedOutBy);
        } else {
            System.out.println("Book not found.");
        }
    }

    private static void returnBook() {
        System.out.print("Enter book title to return: ");
        String title = scanner.nextLine();

        Book book = findBook(title);
        if (book != null && book.isCheckedOut && book.checkedOutBy.equals(currentUser)) {
            book.isCheckedOut = false;
            book.checkedOutBy = null;
            System.out.println("Book returned successfully.");
        } else if (book != null) {
            System.out.println("You can't return this book. It may not be checked out by you.");
        } else {
            System.out.println("Book not found.");
        }
    }

    private static Book findBook(String title) {
        for (Book book : books) {
            if (book.title.equalsIgnoreCase(title)) {
                return book;
            }
        }
        return null;
    }

    // ==== Book Class ====

    static class Book {
        String title;
        String author;
        boolean isCheckedOut = false;
        String checkedOutBy = null;

        Book(String title, String author) {
            this.title = title;
            this.author = author;
        }

        public String toString() {
            return "\"" + title + "\" by " + author + (isCheckedOut ? " [Checked out by: " + checkedOutBy + "]" : " [Available]");
        }
    }
}
