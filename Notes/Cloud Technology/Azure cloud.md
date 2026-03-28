
```bash
(venv) cytech@Charles-laptop:~/CloudCourse$ az policy assignment list --query "[].parameters" -o json
[
  {
    "listOfAllowedLocations": {
      "value": [
        "polandcentral",
        "germanywestcentral",
        "spaincentral",
        "norwayeast",
        "switzerlandnorth"
      ]
    }
  }
]

```



#### Launch the azure web app
```
az webapp up --location germanywestcentral --sku F1
```

`--sku F1` : ensure stay on free tier
