import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class CurrencyConverter {
    private static final Map<String, Double> exchangeRates = new HashMap<>();

    static {
        // Initialize exchange rates (you can update these with real-time data)
        exchangeRates.put("USD", 1.0);
        exchangeRates.put("EUR", 0.85);
        exchangeRates.put("GBP", 0.72);
        // Add more currencies as needed
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Step 1: Allow the user to choose base and target currencies
        System.out.print("Enter base currency (e.g., USD, EUR, GBP): ");
        String baseCurrency = scanner.nextLine().toUpperCase();
        System.out.print("Enter target currency (e.g., USD, EUR, GBP): ");
        String targetCurrency = scanner.nextLine().toUpperCase();

        // Step 2: Fetch exchange rates from the map
        Double baseRate = exchangeRates.get(baseCurrency);
        Double targetRate = exchangeRates.get(targetCurrency);

        if (baseRate == null || targetRate == null) {
            System.out.println("Invalid currency code(s). Please try again.");
            return;
        }

        // Step 3: Take input from the user
        System.out.print("Enter amount to convert: ");
        double amount = scanner.nextDouble();

        // Step 4: Convert the amount
        double convertedAmount = amount * (targetRate / baseRate);

        // Step 5: Display the result
        System.out.println(amount + " " + baseCurrency + " equals " + convertedAmount + " " + targetCurrency);

        scanner.close();
    }
}
