<!DOCTYPE htphml>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Leaderboard</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.6/dist/css/bootstrap.min.css">
</head>
<body>
    <div class="container layer-4">
        <h2>list of Players</h2>
    <a class="btn btn-primary" href = "/players/create.php" role="button">New Player</a>
    <br>
    <table class="table">
        <thead>
            <tr>
                <th>id</th>
                <th>username</th>
                <th>email_addres</th>
                <th>phone_number</th>
                <th>Created At</th>
                <th>Action</th>
            </tr>
        </thead>
        <tbody>
            <?php
            $servername = "localhost";
            $username = "root";
            $password = "";
            $database = "players";

            //create connection
        

            // checking.. connection
            if ($connection->connect_error) {
                die("Connection failed: " . $connection->connect_error);
            }

            // read all row database tables
            $sql = "SELECT * FROM clients";
            $result = $connection->query($sql);

            if (!$result) {
                die("Connection failed: " . $connection->error);
            }
            
            // read data of each row
            while($row = $result->fetch_assoc()) {
                echo "
                <tr>
                 <td>$row[id]</td>
                 <td>$row[username]</td>
                 <td>$row[email_address]</td>
                 <td>$row[phone_number]</td>
                 <td>$row[created_at]</td>

                    <td>
                        <a class='btn btn-primary btn-sm' href='/players/edit.php?id=$row[id]'>Edit</a>
                        <a class='btn btn-primary btn-sm' href='/players/delete.php?id$row[id]'>Delete</a>
                    </td>
                </tr>
                ";
            }
            ?>
       
        </tbody>
    </table>
    </div>
</body>
</html>
