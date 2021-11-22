# KoBoToSheet
Function to export data collected from KoBo Toolbox to google sheet

Step 1:
Open a google spreadsheet.
I strongly suggest creating a new spreadsheet first.


Step 2:
Open Google Apps Script by clicking **Extensions** -> **Apps Script**.
You will be forwarded to another tab containing the attached GAS.
![Open GAS](https://github.com/markbenedictmortera/KoBoToSheet/blob/main/extension.JPG)

Step 3:
Paste the code below into your google script. **Save.**

```{js}
function getData(token_id, url) {
  var scriptProperties = PropertiesService.getScriptProperties();

  var params = {
    "method" : "Get",
    "headers": {"Authorization" : token_id}
   };
  
  const response = UrlFetchApp.fetch(url, headers = params);
  const csv = Utilities.parseCsv(response);
  \\Logger.log(csv);
  return(csv);
}
```
![Save](https://github.com/markbenedictmortera/KoBoToSheet/blob/main/save.JPG)

If google asks permission, accept.

Step 4:
Your spreadsheet now has the function: **getData**.\
Call the function in the spread with the required inputs:\
**token_url:** the API key as string. To get your API key, go to your KoBo account, select **Account Settings** -> copy **API Token**. \
                                    **DO NOT SHARE** this API key to anyone. Use the string: "Token copied_api_key" as the first input. \
                                      For example "Token 1234567890ABCDE". \
**url:** The API v1 URL to your data. To obtain, log in to your KoBo account and go to "https://kc.kobotoolbox.org/api/v1/data" in another tab. \
                                      Find the url of your chosen sheet. Attach a **".csv** at the end of the url. For example "https://kc.kobotoolbox.org/api/v1/data/123456.csv"

![The list of sheets should look like this.](https://github.com/markbenedictmortera/KoBoToSheet/blob/main/csv_url.png)
                                     
                                      
                                  
                                  
                                  




