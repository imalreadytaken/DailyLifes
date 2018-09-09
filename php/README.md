##Tips
- json_decode:
	- 如果assoc不设为true，返回的将是Object而不是array，而在Object中，是无法将数字键设置为属性的，只有通过访问key才能访问到数字key

			<?php
			$json = '{"1":a,"b":2,"c":3,"d":4,"e":5}';
			
			$obj = json_decode($json);
			$arr = json_decode($json, true);
			
			array_key_exists('1', $obj); // false
			array_key_exists('1', $arr); // true
		
			?>
