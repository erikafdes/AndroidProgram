# CURRENCYPAL – ANDROID CURRENCY CONVERTER APPLICATION USING KOTLIN

## PROJECT TITLE
CurrencyPal – Android Currency Converter Application Using Kotlin.

## AIM
To design and develop an Android-based currency converter application using Kotlin that converts monetary amounts between different currencies using exchange rates fetched from a public REST API, with local data persistence and offline fallback support.

## ABSTRACT
CurrencyPal is an Android application developed using Kotlin that allows users to convert monetary values between different international currencies. The application retrieves exchange rates from the Frankfurter public REST API using HTTP GET requests.

The application provides a simple interface where users can enter an amount, select the source and target currencies, and view the converted amount. It also provides features such as currency swapping, resetting inputs, displaying a loading indicator, and remembering previously selected currency pairs.

SharedPreferences is used to store user preferences and cache the last successfully retrieved exchange rates. If the internet connection becomes unavailable, the application uses the previously saved exchange rate to perform offline conversions.

## OBJECTIVES
1. To develop a user-friendly Android currency conversion application.
2. To implement currency conversion using exchange rates obtained from a public API.
3. To understand REST API integration using HTTP GET requests.
4. To implement background processing using ExecutorService.
5. To update the user interface using Handler on the main thread.
6. To store user preferences using SharedPreferences.
7. To implement offline conversion using cached exchange rates.
8. To provide additional functionalities such as currency swapping and resetting.
9. To understand JSON parsing in Android application development.

## PROBLEM STATEMENT
Currency conversion is frequently required when travelling, shopping internationally, or dealing with foreign currencies. Manually calculating exchange rates can be time-consuming and inconvenient.

Basic currency converters may also require continuous internet connectivity and may not remember previously selected currencies.

Therefore, CurrencyPal aims to provide a simple Android application that performs currency conversion using exchange rates obtained from an external API while offering saved preferences and offline fallback functionality.

## PROPOSED SYSTEM
The proposed system is an Android application that provides an easy way to convert monetary values between different currencies.

The user enters an amount and selects the source and target currencies from dropdown lists. When the Convert button is clicked, the application sends an HTTP GET request to the Frankfurter API.

The received JSON response is parsed to extract the exchange rate. The application then calculates and displays the converted amount.

The last successfully retrieved exchange rate is stored locally using SharedPreferences. If the internet connection fails, the application retrieves the previously saved exchange rate and uses it for offline conversion.

## SOFTWARE REQUIREMENTS
- Operating System: Windows/Linux/macOS
- IDE: Android Studio
- Programming Language: Kotlin
- UI Design: XML
- Database/Local Storage: SharedPreferences
- API: Frankfurter REST API
- Version Control: Git and GitHub
- Android SDK and JDK

## HARDWARE REQUIREMENTS
- Computer or laptop
- Minimum 4 GB RAM (8 GB recommended)
- Android emulator or Android smartphone
- Internet connection for fetching exchange rates

## TECHNOLOGIES AND TOOLS USED

**Kotlin:** Used as the primary programming language for developing the Android application.

**Android Studio:** Used as the integrated development environment for writing, testing, and running the application.

**XML:** Used to design the application's user interface.

**Frankfurter API:** Used to retrieve exchange-rate information.

**HttpURLConnection:** Used to establish HTTP connections and send GET requests to the API.

**JSON:** Used to receive and process exchange-rate information.

**SharedPreferences:** Used to store selected currency preferences and previously retrieved exchange rates.

**ExecutorService:** Used to execute network operations in the background.

**Handler:** Used to update the user interface safely on the main thread.

**Git and GitHub:** Used for source code management and project hosting.

## FEATURES OF THE APPLICATION

1. Live Currency Conversion: Retrieves exchange rates from the Frankfurter API.
2. Multiple Currency Support: Supports USD, INR, EUR, GBP, JPY, AUD, and CAD.
3. Currency Swapping: Allows users to exchange the source and target currencies.
4. Reset Functionality: Clears the entered amount and resets currency selections.
5. Loading Indicator: Displays a ProgressBar while fetching exchange rates.
6. Persistent Preferences: Remembers the last selected currency pair.
7. Offline Fallback: Uses the last saved exchange rate when the internet connection is unavailable.
8. Result Display: Displays the converted amount in the selected target currency.

## SUPPORTED CURRENCIES

| Currency Code | Currency Name |
|---|---|
| USD | US Dollar |
| INR | Indian Rupee |
| EUR | Euro |
| GBP | British Pound |
| JPY | Japanese Yen |
| AUD | Australian Dollar |
| CAD | Canadian Dollar |

##  DEVELOPMENT PROCEDURE

1. Open Android Studio and create a new Android project.
2. Select an appropriate project template and choose Kotlin as the programming language.
3. Name the application CurrencyPal.
4. Design the user interface using XML in activity_main.xml.
5. Add an EditText for entering the amount.
6. Add two Spinner components for selecting currencies.
7. Add an ImageButton to swap the selected currencies.
8. Add Convert and Reset buttons.
9. Add a ProgressBar to indicate loading and a TextView to display the result.
10. Open MainActivity.kt and declare the required UI components.
11. Initialize the components using findViewById().
12. Create an array containing the supported currency codes.
13. Populate the Spinners using ArrayAdapter.
14. Implement the swap and reset functionalities.
15. Add INTERNET permission in AndroidManifest.xml.
16. Implement SharedPreferences to save and restore the currency selections.
17. Use HttpURLConnection to send HTTP GET requests to the Frankfurter API.
18. Use ExecutorService to execute network operations in the background.
19. Parse the JSON response using JSONObject and retrieve the required exchange rate.
20. Calculate the converted amount using the retrieved exchange rate.
21. Save the last successfully retrieved exchange rate using SharedPreferences.
22. Implement offline fallback functionality.
23. Use Handler with Looper.getMainLooper() to update the UI on the main thread.
24. Run the application on an Android emulator or physical device.
25. Test the currency conversion, swapping, resetting, and offline functionalities.


## TESTING

The following test cases are used to verify the application:

| Test Case | Input/Action | Expected Output |
|---|---|---|
| Valid conversion | 100 USD to INR | Displays converted amount |
| Currency selection | Select EUR and GBP | Selected currencies are displayed |
| Currency swapping | Click Swap | Source and target currencies are exchanged |
| Reset operation | Click Reset | Amount and selections are reset |
| Empty input | Click Convert without entering amount | Displays validation message |
| Same currency | Select USD to USD | Displays the same amount |
| Internet available | Perform conversion | Fetches exchange rate from API |
| Internet unavailable | Use previously saved rate | Performs offline conversion |
| No cached rate | Disable internet before first conversion | Displays network error |
| Preference restoration | Close and reopen application | Restores saved currency pair |

## ADVANTAGES
1. Simple and user-friendly interface.
2. Supports multiple international currencies.
3. Retrieves exchange rates from a public API.
4. Provides automatic currency conversion.
5. Saves previously selected currency preferences.
6. Supports offline conversion using cached exchange rates.
7. Uses background processing to avoid blocking the user interface.
8. Provides currency swapping and reset functionalities.

## LIMITATIONS
1. Internet connectivity is required to retrieve updated exchange rates.
2. Offline conversion uses previously saved rates, which may be outdated.
3. The application currently supports only seven currencies.
4. Historical exchange-rate charts are not available.
5. Exchange rates may differ from those offered by banks and payment providers.

## FUTURE ENHANCEMENTS
1. Add support for more international currencies.
2. Include historical exchange-rate information.
3. Implement currency conversion charts.
4. Improve the interface using Material Design.
5. Add automatic exchange-rate refreshing.
6. Implement conversion history.
7. Add a favourite currency list.
8. Improve error handling and input validation.


## SCREENSHOTS

<img width="1080" height="2424" alt="Screenshot_20261112_114124" src="https://github.com/user-attachments/assets/314a09b1-c514-434e-aa4a-dc292bfc7c27" />
<img width="1080" height="2424" alt="Screenshot_20261112_113905" src="https://github.com/user-attachments/assets/e1938572-b7fc-456c-be8e-5cc2b68dcf3e" />
<img width="1080" height="2424" alt="Screenshot_20261112_113958" src="https://github.com/user-attachments/assets/e16b5597-9e0b-49c8-9209-93253d0954b9" />


## RESULT
The CurrencyPal Android application was developed using Kotlin and XML. It successfully implements currency conversion using exchange rates retrieved from the Frankfurter REST API. The application uses JSON parsing to retrieve exchange rates, ExecutorService for background network operations, Handler for updating the user interface, and SharedPreferences for storing user preferences and cached exchange rates.

The application also provides currency swapping, resetting, loading indication, and offline fallback functionality.

## CONCLUSION
CurrencyPal demonstrates the practical implementation of Android application development using Kotlin. It provides a convenient solution for currency conversion by integrating an external REST API with local storage.
Through this project, concepts such as Android UI development, API integration, HTTP networking, JSON parsing, multithreading, and SharedPreferences were implemented and understood.
The project provides a foundation for developing more advanced financial applications with additional features and improved user experience.



