# pmt5_api
Description of the api methods

## all_active_spare_parts()
Get all active spares parts of the current user

|URL|Auth|Description|
|----|----|----|
|`/api/v1/user/{hashed_user_id}/{user_token}/all_active_spare_parts?per_page=100&page=1`|`no`|returns an object|

```json
{
    "paginator" : { object },
    "spare_parts" : [{ object }, { object },...] 
}
```

#### Request params
|Param|Require|Description|
|----|----|----|
|`hashed_user_id`|`yes`|Uniq user Id that encoded for security reasons|
|`user_token`|`yes`|Uniq user token. Provided for access to the api methids|
|`per_page`|`[optional], default : 500, max:500`| Count of the spare parts per page|
|`page`|`[optional]`|Page number with results of the request|

#### Request example
```bash
$ curl https://pmt5.com/api/v1/user/{hashed_user_id}/{user_token}/all_active_spare_parts?per_page=100&page=1
```

#### Response object description
###### Paginator object
|Key|Value|Description|
|----|----|----|
|`total`|`int`|Total of active spares of the current user|
|`per_page`|`int`|How many spare parts shows on the page|
|`pages_count`|`int`|Total pages count|
|`current_page`|`int`|Current page|


###### Spare parts array of objects
|Key|Value|Description|
|----|----|----|
|`user_code`|`string`|Uniq identificator of the spare part|
|`price`|`decimal`|Price of the spare part|
|`width`|`decimal`|Width of the spare part|
|`height`|`decimal`|Height of the spare part|
|`weight`|`decimal`|Weight  of the spare part|
|`length`|`decimal`|Length of the spare part|
|`original_number`|`text`|Original number or numbers of the spare part|
|`description`|`text`|Description of the spare part|
|`defects`|`text`|Defects of the spare part|
|`youtube_link`|`string`|Link to youtube. Only prefix. For example: https://www.youtube.com/watch?v={yotube_link}|
|`part_name`|`string`|Name of the spare part|
|`store`|`string`|Store name in which the spare part was stored|
|`images`|`object`|Objects with links to inages of the spare part|
|`car`|``object``|Objects with car's params|
|`brand`|`string`|Brank of the car|
|`model`|`string`|Model of the car|
|`mod`|`string`|Modification of the car|
|`mod_years`|`string`|Years of production of the car modification|
|`params`|`object`|Parameters of the car|
|`year`|`string`|Year of production of the current car|
|`fuel`|`string`|Fuel type|
|`cubic`|`string`|Cubic capacity|
|`power`|`string`|Engine power (kW)|
|`gearbox`|`string`|Gearbox|
|`body`|`string`|Body type|
|`color`|`string`|Color of the body|
|`stearing_wheel`|`string`|Stearing wheel position|
|`driven_wheel`|`string`|Count of the doors|

#### Response example

```json
{
    "paginator":
        {
            "total":10731,
            "per_page":"500",
            "pages_count":22,
            "current_page":1
        },
    "spare_parts":
        [
            {
                "user_code":"11BY1-23",
                "price":"1600.00",
                "width":"0.00",
                "height":"0.00",
                "weight":"0.00",
                "length":"0.00",
                "original_number":"-",
                "description":"-",
                "defects":"-",
                "youtube_link":"-",
                "part_name":"\u041a\u0443\u043b\u0438\u0441\u0430 \u041a\u041f\u041f",
                "store":"Lida, Ostrovlya 1 > c > 3",
                "images":
                    {
                        "1":"https:\/\/pmt5.com\/img\/spares\/resized\/11BY1-spares-11BY1-23-e531ad999d.jpg"
                    },
                "car":
                    {
                        "brand":"VW",
                        "model":"PASSAT B4",
                        "mod":"PASSAT Variant (3A5, 35I)",
                        "mod_years":"c 1988 - \u043f\u043e 1997",
                        "params":
                            {
                                "year":"1996",
                                "fuel":"\u0414\u0438\u0437\u0435\u043b\u044c",
                                "cubic":"1.9",
                                "power":"66 kW",
                                "gearbox":"5-\u0438 \u0441\u0442\u0443\u043f\u0435\u043d\u0447\u0430\u0442\u0430\u044f \u041a\u041f\u041f",
                                "body":"\u0423\u043d\u0438\u0432\u0435\u0440\u0441\u0430\u043b",
                                "color":"\u0421\u0438\u043d\u0438\u0439 \/ \u0433\u043e\u043b\u0443\u0431\u043e\u0439",
                                "stearing_wheel":"-",
                                "driven_wheel":"-"
                        }
                }
        },
        { object },
        { object },
        ...
    ]
}
```
