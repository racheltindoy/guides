## CRUD

### INSERT

```
$data = array( 
   'roll_no' => ‘1’, 
   'name' => ‘Virat’ 
); 

$this->db->insert("stud", $data);
```

### SET WHERE UPDATE
```
$data = array( 
   'roll_no' => ‘1’, 
   'name' => ‘Virat’ 
); 

$this->db->set($data); 
$this->db->where("roll_no", ‘1’); 
$this->db->update("stud", $data);
```


### DELETE
```
$this->db->delete("stud", "roll_no = 1");
```

### SELECT

```
$query = $this->db->get("stud"); 
$data['records'] = $query->result();
```


### Close connection

```
$this->db->close(); 
```


==============

## 1. change the following:

> application > config > config.php
   ```
	$config['base_url'] = 'http://localhost/foldername';
  ```

> application > config > routes.php

```
$route['default_controller'] = 'welcome'; // Property/method

- application > config > database.php
	'hostname' => 'localhost',
	'username' => '',
	'password' => '',
```

## autoload the following libraries

```
$autoload['libraries'] = array('database', 'email', 'session');
$autoload['drivers'] = array('cache');
$autoload['helper'] = array('url', 'file');
```

### 2. Create header and footer at application/views/templates/

- copy templates folder
- paste to application/views/


### 3. Before start of controllers file

- paste:
```
<?php 
defined('BASEPATH') OR exit('No direct script access allowed');

class ChangeClassname extends CI_Controller {

	public function __construct()
	{
			parent::__construct();
			$this->load->model('ChangeModelName');
			$this->load->helper('url_helper');
	}

}
// dont copy this end ?>
```


### 4. Before start of models file
```
<?php

class ModelClassName extends CI_Model
{

	public function __construct()
	{
		$this->load->database();
	}

// dont copy this end ?>
```
