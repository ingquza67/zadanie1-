<?php

$conn = mysqli_connect("localhost","root","","hotel");  <- *tutaj jest połączenie z bazą danych*

?>
<style>
    th, td {
        border: 1px solid black;                                   <- *w tym miejscu jest dodany styl żeby tabelka była czytelniejsza*
        
    }
</style>                                            


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> <link rel="stylesheet" href="style.css">
    <title>Document</title>
</head>
<body>
<table>
    <tr>
        <th>Numer Pokoju</th>
        <th>ilość Łóżek</th>                                   <- tutaj się zaczyna się tabela
        <th>Zakaz Zwierząt</th>



    </tr>

<?php

$query = "SELECT numer_pokoju,ilosc_miejsc,zakaz_zwierzat FROM `pokoje` WHERE ilosc_miejsc > 2;";                    <- zapytanie

$result = mysqli_query($conn, $query);
 
if($result){
    while($wiersz = mysqli_fetch_assoc($result)){
        echo "<tr>";
        echo "<td>" , $wiersz ['numer_pokoju'] ,"</td>";
        echo "<td>" , $wiersz ['ilosc_miejsc'] ,"</td>";          <- pętla tworząca nowe rzędy tabelki
        echo "<td>" , $wiersz ['zakaz_zwierzat'] , "</td>";
        echo "</tr>";
    }
}

?>


</table> <- zamknięcie tabeli                                                                                                                                                                                             
    
</body>
</html>-->


Ogólnie zadanie było proste
