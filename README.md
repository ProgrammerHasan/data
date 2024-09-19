# Data | Master/Common Data | Bangladesh
A wide range of data, including all banks and districts of Bangladesh, is available in JSON format. More datasets will be added, and contributions to this project are highly encouraged! Feel free to contribute data in other formats as well. Thank you!

Bangladesh Districts, Bangladesh Bank List

# How to Import Data into a Laravel Project: Example
```
<?php

namespace Database\Seeders;

use App\Models\Bank;
use Illuminate\Database\Seeder;

class BanksTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        if (Bank::exists()) {
            return;
        }

        $banks = json_decode(file_get_contents('data/banks.json', true), true); //database/seeders/data
        foreach ($banks as $bank) {
            Bank::create([
                'type' => $bank['type'],
                'name' => $bank['name'],
                'code' => @$bank['code'],
                'formerly' => @$bank['formerly'],
                'founded' => @$bank['founded'],
                'founder' => @$bank['founder'],
                'headquarters' => @$bank['headquarters'],
                'website' => @$bank['website'],
            ]);
        }
    }
}

```
