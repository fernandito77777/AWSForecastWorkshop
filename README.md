# AWS Forecast Workshop

Introduction to AWS Forecast, and how to implement forecast prediction on AWS Forecast

For current workshop, we are going to estimate demand forecast for weekly demand, including the workdays of the week. To get workdays, simply find the built-in custom calendar (example for python, it has [pytanggalmerah](https://pypi.org/project/Pytanggalmerah/) to generate holiday for indonesia's calendar. Also, you can consider using excel and find the calendar on the internet, and use "NETWORKDAYS" function to get the difference of the holiday)

### Agenda
* [Setup S3 for Storing Data](docs/S3.md)
* [Create Forecast using AWS Forecast](docs/Forecast.md)

### Prerequisites
* AWS Account
* The workshop has been tested on Singapore Region (ap-southeast-1)