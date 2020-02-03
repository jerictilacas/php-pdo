# PHP Data Objects

This file shows the simple implementation on how does PDO works including the basics prepared statements. 

## Getting Started

1.  What is PDO ?

    ` is a lean, consistent way to access databases. `
    
2.  Simple Code that connects to database
    
    ```php
    <?php
    	$host = 'localhost';
    	$user = 'root';
    	$password = '123456';
    	$dbname = 'pdo';
    
    	// Set DSN
    	$dsn = 'mysql:host=' . $host . ';dbname=' . $dbname;
    
    	// Create a PDO instance
    	$pdo = new PDO($dsn, $user, $password);
    	$pdo->setAttribute(PDO::ATTR_DEFAULT_FETCH_MODE, PDO::FETCH_OBJ);
    
    	 $status = 'admin';
    
    	 $sql = 'SELECT * FROM users WHERE status = :status';
    	 $stmt = $pdo->prepare($sql);
    	 $stmt->execute(['status' => $status]);
    	 $users = $stmt->fetchAll();
    
    	 foreach($users as $user){
    	 	echo $user->name.'<br>';
    	 }
    
    	 // Insert Data
    
    	$name = 'Jerico Tilacas';
    	$email = 'jericotilacas@gmail.com';
    	$status = 'guest';
    
    	$sql = 'INSERT INTO users(name, email, status) VALUES(:name, :email, :status)';
    	$stmt = $pdo->prepare($sql);
    	$stmt->execute(['name'=> $name, 'email' => $email, 'status' => $status]);
    	echo 'Added User';
    ```
