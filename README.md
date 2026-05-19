Here's a bunch of setups I use on my PC for serving local LLM models via llama.cpp docker (Vulkan acceleration).

Hardware:
```
XFX Radeon RX 6600 (8GB GDDR6)
AMD Ryzen 5 5600 (6C/12T, 32MB L3 Cache, 3MB L2 Cache, no iGPU)
64 GiB of RAM (DDR4, 2x Kingston KF3200C16D4/32GX @ 3200 MTS)
```

You can copy-paste example compose.yml file and point mounts on your models directory (my directory structure is done by LM Studio)

------

|file|model|tps|context|
|-|-|-|-|
|[qwen36_27b_q4_mtp_coding](qwen36_27b_q4_mtp_coding.yml)|[Qwen 3.6 27B Q4KM](https://huggingface.co/froggeric/Qwen3.6-27B-MTP-GGUF)|~ 3.40|150k|



Prompt I paste into llama.cpp chat to measure inference speed:

--------
I have 3 problems that need solving:

Problem 1:

I have tables:
```
departments(DepartmentId, DepartmentName)
students(DepartmentId, StudentId, StudentName)
```
Write a MySQL query to list all students in the Computer Science department.

Problem 2:

Write a bash script that moves all files from directory `/mnt/stuff_for_sorting/` to `/mnt/sorted_by_filetype/$filetype/` where $filetype can be 'mp3', 'jpg' and so on

Problem 3:

Optimize this script:
```php
<?php
$users = [
    ['name' => 'Alice', 'age' => 30, 'city' => 'New York'],
    ['name' => 'Bob',   'age' => 25, 'city' => 'London'],
    ['name' => 'Charlie','age' => 35, 'city' => 'Tokyo'],
    // ... hundreds or thousands of entries
];

$output = "";
$totalAge = 0;
$count = 0;

foreach ($users as $user) {
    $output .= "<p>Name: " . $user['name'] . ", Age: " . $user['age'] . ", City: " . $user['city'] . "</p>";
    $totalAge += $user['age'];
    $count++;
}

$averageAge = $totalAge / $count;
$output .= "<p>Average Age: " . $averageAge . "</p>";

echo $output;
?>

```