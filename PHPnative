<?php    

$mysqlhost = 'localhost'; 

$mysqlusr = 'root'; 

$database = 'nama database'; 

$mysqlpass = 'password';  

mysql_connect($mysqlhost,$mysqlusr,$mysqlpass);   

?>    

<!DOCTYPE html>
<html>   

	<head>
		<title>MySQL Command Line - iBacor.com</title>
	</head>	  

	<body>

<?php    

if (isset($_POST['submitquery'])) {   

	if (get_magic_quotes_gpc()) $_POST['query'] = stripslashes($_POST['query']);   

	echo('<p><b>Query:</b><br />'.nl2br($_POST['query']).'</p>');
	
//  mysql_select_db($_POST['query']);  bila ingin menggunakan list database yang akan dieksekusi
	mysql_select_db($database);  

	$result = mysql_query($_POST['query']); 

	if ($result) {    

		if (@mysql_num_rows($result)) {
		
?>

			<p><b>Result Set:</b></p>   

			<table border="1">   

				<thead>   

					<tr>   
					
<?php

						for ($i=0;$i<mysql_num_fields($result);$i++) {   

							echo('<th>'.mysql_field_name($result,$i).'</th>');   

						}
						
?>

					</tr>   

				</thead>
				
				<tbody>   
				
<?php

					while ($row = mysql_fetch_row($result)) {   

						echo('<tr>');   

						for ($i=0;$i<mysql_num_fields($result);$i++) {   

							echo('<td>'.htmlentities($row[$i], ENT_QUOTES).'</td>');   

						}   

						echo('</tr>');   

					}   

?>   

				</tbody>   

			</table>
			
<?php			  

		} else {    

			echo('<p><b>Query OK:</b> '.mysql_affected_rows().' rows affected.</p>');
		 
		}    

	} else {    

		echo('<p><b>Query Failed</b> '.mysql_error().'</p>');  

	}    

}    

?>    

		<form action="<?=$_SERVER['PHP_SELF']?>" method="post">     

<?php /* Aktifkan bila ingin menggunakan list database yang akan dieksekusi
				
	echo'	<p>Target Database: 

				<select name="db">';	

					$dbs = mysql_list_dbs(); 

					for ($i=0;$i<mysql_num_rows($dbs);$i++) { 

						$dbname = mysql_db_name($dbs,$i); 

						echo("<option>$dbname</option>"); 

					}

		echo'	</select> 
					
			</p>'; */ 
					
?>	
		
			<p>SQL Query:<br />    

				<textarea onFocus="this.select()" cols="60" rows="5" name="query">show tables</textarea>   

			</p>    

			<p><input type="submit" name="submitquery" value="Run" accesskey="S" /></p>  

		</form>
		
		<p><a href="http://ibacor.com/media/">Free Online Tools</a>
		
	</body>    

</html>
