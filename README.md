# Hotel – PHP + MySQL

## Opis projektu
Ten plik łączy się z bazą danych i wyświetla pokoje hotelowe w tabeli HTML.

Pokazuje tylko pokoje, które mają więcej niż 2 miejsca.

---

## Kod

```php
<?php

$conn = mysqli_connect("localhost","root","","hotel");

?>
<style>
    th, td {
        border: 1px solid black;
    }
</style>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Hotel</title>
</head>
<body>

<table>
    <tr>
        <th>Numer Pokoju</th>
        <th>Ilość Łóżek</th>
        <th>Zakaz Zwierząt</th>
    </tr>

<?php

$query = "SELECT numer_pokoju, ilosc_miejsc, zakaz_zwierzat 
          FROM pokoje 
          WHERE ilosc_miejsc > 2;";

$result = mysqli_query($conn, $query);

if($result){
    while($wiersz = mysqli_fetch_assoc($result)){
        echo "<tr>";
        echo "<td>".$wiersz['numer_pokoju']."</td>";
        echo "<td>".$wiersz['ilosc_miejsc']."</td>";
        echo "<td>".$wiersz['zakaz_zwierzat']."</td>";
        echo "</tr>";
    }
}

?>

</table>

</body>
</html>
