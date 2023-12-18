import java.util.HashMap;
import java.util.*;
import java.util.Map;
import java.util.Scanner;
import java.util.List;

/**
 * @Author Bernard Ginn
 * @Version 0.01
 * 
 */
/**
 * This class simulates a simple subway system that allows users to plan routes between stations.
 */
public class SubwaySystem {
    /**
     * The main method that starts the subway system program.
     *
     * @param args Command-line arguments (not used).
     */
    public static void main(String[] args) {
        // Create a map to represent subway routes and their corresponding station lists
        Map<String, List<String>> subwayRoutes = new HashMap<>();
        subwayRoutes.put("Route 1", Arrays.asList("Unicentro", "Marsella", "Mu", "Bosa"));
        subwayRoutes.put("Route 2", Arrays.asList("Germania", "Sabana", "F"));
        subwayRoutes.put("Route 3", Arrays.asList("Gu", "Santiago", "Sena", "Mu", "Timiza"));

        Scanner scanner = new Scanner(System.in);

        while (true) {
            // Display available routes to the user
            System.out.println("Available routes:");
            for (String route : subwayRoutes.keySet()) {
                System.out.println("- " + route);
            }

            // Ask the user for the desired route or option to quit
            System.out.print("Enter the desired route (or type 'quit' to exit): ");
            String selectedRoute = scanner.nextLine();

            if (selectedRoute.equalsIgnoreCase("quit")) {
                System.out.println("Exiting...");
                break; // Exit the loop if the user wants to quit
            }

            // Check if the selected route is valid
            List<String> stations = subwayRoutes.get(selectedRoute);
            if (stations == null) {
                System.out.println("Invalid route selection.");
                continue; // Restart the loop if the route is invalid
            }

            // Display available stops for the selected route
            System.out.println("Available stops for " + selectedRoute + ":");
            for (String station : stations) {
                System.out.println("- " + station);
            }

            // Ask the user for starting and destination stations
            System.out.print("Enter the starting station: ");
            String startingStation = scanner.nextLine();
            System.out.print("Enter the destination station: ");
            String destinationStation = scanner.nextLine();

            int startIndex = stations.indexOf(startingStation);
            int endIndex = stations.indexOf(destinationStation);

            if (startIndex == -1 || endIndex == -1) {
                System.out.println("Invalid station selection.");
                continue; // Restart the loop if either station is invalid
            }

            // Display the selected route from starting to destination stations
            System.out.println("Your selected route from " + startingStation + " to " + destinationStation + ":");
            if (startIndex < endIndex) {
                for (int i = startIndex; i <= endIndex; i++) {
                    System.out.println("- " + stations.get(i));
                }
            } else {
                for (int i = startIndex; i >= endIndex; i--) {
                    System.out.println("- " + stations.get(i));
                }
            }
        }

        System.out.println("Thank you for using the subway system!");
    }
}
