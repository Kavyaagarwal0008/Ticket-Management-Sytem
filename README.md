# Ticket-Management-Sytem
SImple Ticket Book web using HTML, CSS and JS which show particular details for booking ticket
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ticket Management System</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background-color: #f1f1f1;
    padding: 20px;
    background-image: url('tkt.jpg');
    background-size: cover;
    background-position: center;
    height: 100vh;
}

.background-img {
    background-color: rgba(255, 255, 255, 0.8);
    padding: 20px;
    border-radius: 10px;
    max-width: 400px;
    margin: 50px auto;
}

h2 {
    text-align: center;
    color: #333;
}

.ticket-section {
    max-width: 400px;
    margin: 0 auto;
}

input[type="text"], input[type="date"], input[type="submit"] {
    width: calc(100% - 20px);
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 5px;
}

input[type="submit"] {
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

input[type="submit"]:hover {
    background-color: #45a049;
}

#ticket-history {
    margin-top: 20px;
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    display: none;
}
#view-history-btn{
    background-color:rgb(24, 24, 92);
    color: white;
    cursor: pointer;
    transition: background-color 0.3s;
    width: calc(100% - 20px);
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 5px;

}

#history-table {
    width: 100%;
    border-collapse: collapse;
}

#history-table th, #history-table td {
    padding: 8px;
    border-bottom: 1px solid #ddd;
}

#history-table th {
    background-color: #f2f2f2;
    text-align: left;
}

#history-table td {
    text-align: center;
}

.delete-btn {
    background-color: #dc3545;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 5px 10px;
    cursor: pointer;
}

</style>
</head>
<body>


<div class="background-img">
<div class="ticket-section">
    <form id="ticket-form">
        <h2>Ticket Management System</h2>
        <input type="text" id="name" placeholder="Name" required><br>
        <input type="text" id="seat" placeholder="Seat No" required><br>
        <input type="date" id="date" required><br>
        <input type="text" id="from" placeholder="From Location" required><br>
        <input type="text" id="to" placeholder="To Location" required><br>
        <input type="submit" value="Book Ticket">
    </form>
    <button id="view-history-btn">View History</button>
</div>
</div>
<div id="ticket-history" style="display: none;">
    <h3>Ticket History</h3>
    <table id="history-table">
        <thead>
            <tr>
                <th>Ticket ID</th>
                <th>Name</th>
                <th>Seat No</th>
                <th>Date</th>
                <th>From Location</th>
                <th>To Location</th>
                <th>Action</th>
            </tr>
        </thead>
        <tbody id="history-table-body">
            <!-- Ticket history rows will be dynamically added here -->
        </tbody>
    </table>
</div>

<script>
  


document.getElementById("ticket-form").addEventListener("submit", function(event) {
    event.preventDefault();
    
    // Gather user input
    var name = document.getElementById("name").value;
    var seat = document.getElementById("seat").value;
    var date = document.getElementById("date").value;
    var from = document.getElementById("from").value;
    var to = document.getElementById("to").value;
    
    // Generate ticket ID (simple demonstration)
    var ticketId = "T" + Math.floor(Math.random() * 10000);
    
    // Add ticket details to history table
    var tableBody = document.getElementById("history-table-body");
    var newRow = tableBody.insertRow();
    newRow.innerHTML = "<td>" + ticketId + "</td><td>" + name + "</td><td>" + seat + "</td><td>" + date + "</td><td>" + from + "</td><td>" + to + "</td><td>Booked</td><td><button class='delete-btn' data-ticket-id='" + ticketId + "'>Delete</button></td>";

    // Display alert for successful booking and generated ticket ID
    alert("Ticket with ID " + ticketId + " has been booked successfully.");
    document.getElementById("ticket-form").reset();
});

document.getElementById("view-history-btn").addEventListener("click", function() {
    document.getElementById("ticket-history").style.display = "block";
});

document.getElementById("ticket-history").addEventListener("click", function(event) {
    if (event.target.classList.contains('delete-btn')) {
        var ticketIdToDelete = event.target.getAttribute('data-ticket-id');
        // Delete ticket logic (for demonstration, we'll remove the row from table)
        event.target.closest('tr').remove();
        alert("Ticket with ID " + ticketIdToDelete + " has been deleted.");
    }
});



</script>

</body>
</html>
