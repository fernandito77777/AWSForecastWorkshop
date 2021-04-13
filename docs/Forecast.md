# Create Forecast using AWS Forecast

1. Go to [AWS Console](https://ap-southeast-1.console.aws.amazon.com/console/home?region=ap-southeast-1)
2. Type `Forecast` at the top search bar and click `Amazon Forecast` service
3. click `Create dataset group`
    ![](../images/Forecast/3.png)

4. in Dataset group details, fill `DemandDatasetGroup`
5. Choose `Retail` for forecasting domain.

On forecasting domain, each of the options only affecting the data schema, and not affecting the model algorithm and hyperparameters. Please take a look at [this documentation](https://docs.aws.amazon.com/forecast/latest/dg/howitworks-domains-ds-types.html) for more information.

6. click `Next`
    ![](../images/Forecast/6.png)

7. in Dataset detail page, fill the dataset name with `DemandRetailDataset`
8. change the frequency of your data to `Week`
9. on Data Schema, change it to `JSON schema`
    ![](../images/Forecast/9.png)

10. Paste this JSON code to the data schema

```
{
	"Attributes": [
		{
			"AttributeName": "item_id",
			"AttributeType": "string"
		},
		{
			"AttributeName": "timestamp",
			"AttributeType": "timestamp"
		},
		{
			"AttributeName": "demand",
			"AttributeType": "float"
		},
		{
			"AttributeName": "Workday",
			"AttributeType": "string"
		}
	]
}
```

11. Change the timestamp format to `yyyy-MM-dd`
    ![](../images/Forecast/11.png)

12. in Dataset import name, fill it with `DemandRetailDatasetImport`
13. in time zone, select `Do not use time zone`
14. in data location, click `Browse S3`
15. click your S3 bucket name `yourname-forecast-test`
16. click the radio button on the left side of your data `DataDemand.csv` and click `Choose`
17. in IAM role, choose `Crete a new role`
18. in Create IAM Role page, click `Create role`
19. click `Start`
    ![](../images/Forecast/19.png)

This process might take around 15 minutes to process.
Once it's ready, it will display the `Active` status.
    ![](../images/Forecast/19-2.png)

Let's try to create the predictor.

20. in dashboard page, click `Start` on Predictor training
    ![](../images/Forecast/20.png)

21. in predictor name, fill with `DemandRetailPredictor`
22. fill the forecast horizon as `8`

Forecast horizon is a predicted result that will be displayed on the forecast. Assume you choose `Week` for forecast frequency and `8` as forecast horizon. The forecast will predict the result up to 8 weeks ahead.

23. change the forecast frequency to `Week`
    ![](../images/Forecast/23.png)
24. For Predictor details, please choose `Manual` and choose `NPTS`
    ![](../images/Forecast/24.png)

There is an option called `AutoML` meaning that it will try for every algorithm possible, and choose the best result of all of the algorithms.

25. scroll down and click `Start`

This process might take around 15 minutes to process.
Once it's done, we need to create the forecasts.

26. Click `Start` on generate forecast
    ![](../images/Forecast/26.png)

27. in forecast name, fill with `DemandRetailForecast`
28. Choose `DemandRetailPredictor` as your predictor
29. for forecast types, fill it with `0.1,0.5,0.9,mean`
30. click `Start`
    ![](../images/Forecast/30.png)

It will create a forecast around 15 minutes.
Once it's done, we can now take a look at the prediction

31. Click "Lookup Forecast"
    ![](../images/Forecast/31.png)

32. In forecast lookup page, choose the forecast as "DemandRetailForecast"
33. In start date, fill it with "2017/12/15"
34. In end date, fill it with 2018/01/31"
35. fill the Value of item_id as "1"
36. Click "Get Forecast"
    ![](../images/Forecast/36.png)
    

[BACK TO WORKSHOP GUIDE](../README.md)