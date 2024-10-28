<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Parking Availability</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        .counter {
            font-size: 24px;
            margin: 20px 0;
        }
        button {
            padding: 10px 20px;
            font-size: 18px;
            margin: 10px;
        }
    </style>
</head>
<body>
    <h1>Parking Availability</h1>

    <!-- Parking Availability Section -->
    <p class="counter">Total Spots: <span id="total-spots">50</span></p>
    <p class="counter">Parked Vehicles: <span id="parked-vehicles">0</span></p>
    <p class="counter">Available Spots: <span id="available-spots">50</span></p>

    <button onclick="parkVehicle()">Park Vehicle</button>
    <button onclick="removeVehicle()">Remove Vehicle</button>

    <!-- Manual Reset Button -->
    <h2>Admin Controls</h2>
    <button onclick="resetParkingData()">Reset Parking Data</button>

    <script>
        let totalSpots = 50; // Total parking spots
        let parkedVehicles = 0; // Initially, no vehicles are parked

        // Store the last reset date in the browser's local storage
        let today = new Date().toDateString(); // Get today's date in a readable format

        // Function to reset parking data daily
        function resetDaily() {
            let lastResetDate = localStorage.getItem('lastResetDate');

            // If there is no last reset date stored or if the stored date is not today
            if (!lastResetDate || lastResetDate !== today) {
                // Reset the parked vehicles count
                parkedVehicles = 0;

                // Store today's date as the new reset date
                localStorage.setItem('lastResetDate', today);

                // Update the display
                updateDisplay();
            }
        }

        // Function to manually reset the parking data
        function resetParkingData() {
            // Reset parked vehicles to 0
            parkedVehicles = 0;

            // Update the display to show reset values
            updateDisplay();

            // Notify the user
            alert("Parking data has been reset!");
        }

        // Function to update the display
        function updateDisplay() {
            document.getElementById("parked-vehicles").textContent = parkedVehicles;
            document.getElementById("available-spots").textContent = totalSpots - parkedVehicles;
        }

        // Function to add a parked vehicle
        function parkVehicle() {
            if (parkedVehicles < totalSpots) {
                parkedVehicles++;
                updateDisplay();
            } else {
                alert("Parking is full!");
            }
        }

        // Function to remove a parked vehicle
        function removeVehicle() {
            if (parkedVehicles > 0) {
                parkedVehicles--;
                updateDisplay();
            } else {
                alert("No vehicles to remove!");
            }
        }

        // Initialize the display on page load and check for daily reset
        resetDaily();
        updateDisplay();
    </script>
</body>
</html>

<!---
Parkingmanagement-Qr/Parkingmanagement-Qr is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
