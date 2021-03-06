# ACTV8 API v4

## Environment Setup
Please refer to the https://github.com/ACTV8meInc/actv8-backend-environment-setup for instructions in how to setup the ACTV8 Backend Environment

## Setup your environment variables (.env)
The values for the environment variables are provided by the system administrator. If you have not received them yet, please contact marco.godoy@actv8me.com.

1. Open the .env file using text editor (i.e. "vim", "Sublime", etc...)
```
vim ~/act8-backend/api/v4/.env
```
2. Update all the variables with the values provided by the system administrator
3. Make sure the AWS_CREDENTIALS_PROFILE constant matches to the name of the profile you have set within your ~/.aws/credentials file
4. Save the .env file

## Initialize the application
Once all the environments have been set (previous step), you can initialze the application by running the following steps:
1. Launch your Vagrant box:
```
cd ~/actv8-backend/Homestead
vagrant up
```
2. SSH into your Vagrant box:
```
vagrant ssh
```
3. Navigate to the ACTV API root directory (within your Vagrant box):
```
cd ~/act8-backend/api/v4
```
4. Switch to the "master" branch
```
git checkout master
```
5. Install depencies via Composer
```
composer install
```
6. Initialize the application using the Artisan actv8-api:init command
```
php artisan actv8-api:init
```
7. Write down the credentials displayed at the end of the initialization process. 

## Verify installation
At this point you should be able to login to the system by using the credentials generated by the system during the initialization process.

To verify, you can make the following request through the command line within the Vagrant box:
```
curl -XPOST localhost/user/login -H "Content-Type: application/json" -H "X-Api-Key: [the api key you got during the installation process]" -H "X-Api-Version: 4.0" -d '{"email":"superadmin@app.com", "password":"password", "login_method":"email"}'
```

If everything is installed correctly, you should get the following response:
```
{"id":1,"legacy_id":null,"migrated_at":null,"application_id":3,"name":"Superadmin","username":"superadmin@app.com","login_method":"email","email":"superadmin@app.com","created_by":null,"first_name":null,"last_name":null,"phone_number":null,"job_title":null,"gender":0,"birthdate":null,"remember_token":null,"last_login_at":"2018-02-08 01:49:11","created_at":"2018-02-08 01:47:34","updated_at":"2018-02-08 01:49:11","deleted_at":null,"validate_token":"","validated":null,"validated_at":null,"state":null,"zipcode":null,"support_pin":null,"privacy_enabled":false,"token":{"type":"Bearer","access":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjZkZWFlZjMzZjk5MmQyZmQ5MzE2N2I2ZjkzZWU3Yzg2ODRkYmQxN2E3NjYzNjNmYTc0Y2JmNjhkNGJlMWU3OTk1ZmExZWM1YmJiNGY2MDIxIn0.eyJhdWQiOiIyIiwianRpIjoiNmRlYWVmMzNmOTkyZDJmZDkzMTY3YjZmOTNlZTdjODY4NGRiZDE3YTc2NjM2M2ZhNzRjYmY2OGQ0YmUxZTc5OTVmYTFlYzViYmI0ZjYwMjEiLCJpYXQiOjE1MTgwNTQ1NTIsIm5iZiI6MTUxODA1NDU1MiwiZXhwIjoxNTQ5NTkwNTUyLCJzdWIiOiIxIiwic2NvcGVzIjpbIioiXX0.mWahWw5CRNfNofSztIoRB-qNzTH1cYLGKWlAUP1_519LBjQRiWYv_zDBMb08Ti6ZEWrlrgndTabkl-L4EC3RiwjB6yniAr6nOisWRqUE8g8GYhzNgaaKBKzK19uzdFR1K5YrKrir0qZtuOrN80CKwSwuwOty4b0rrvYoxcaOrMkvyZwYrtrMKuu9ZoVhJeMLRXGuWd-PccyEdjUppktcwZRdVLGJEvjiHgX9I9N9Ix-0fMQUnC9LkicSke8VGMR8wgUWQddfwGfhsMm0OIdYef1agbE8XpolsEcb749XEfv6H2T72S2RmbSjB8_yPz5s0cBtWEWCePrvangVlNJZnLx7LSe_tmH0Q07EGVABtgHIGeWWEknU137Npaz3S8vv5Kt3ext6aPbzgq8ZcYMQVTzTli2VAxO9o3-92JjP9yqM_H91O-3jXz2ij6CVpz6IdDYOxwl3K0fhrQBmoZAZlpuL7hODQJcf26-bdwTe4tXSXOo-z2_pbuYeQJ6xUbdai6gg9aCKCEZDRR9BPkZTGfsf3awp2Vj9IukvTp6XA-Th0cPsI7iq4tCz_bd7nxd0ewrn04BnepVWRlNx4LHYaV2tNnNcYHWz9pIvwnR1qU4ion2GLfuFroe3a6pSZW9vza-yWgh6uaaMVw1fbWdv-w_I82NClWl68wW2oWTxbyE","expires_in":31536000,"refresh":"def50200e7f66e6ad02a15a2fcf8a683d68dfe0e0870638b60203099081095a93f9996e48fb0c6ba9fba0355df935929a32924d52655a09821767156edc5862e3d36dc96897dba62c5bf6a9116e81738e000b1776b23b5881a672f2a74ed449eaef6c97ee0b691b6c989af5226c82cf2e3355b96c227d12a8c2651e2bc30a6f268ec552b4b0dc2ce9ff57314e8d7d2f214faa6374a29946f93272e1db75427ac6f733663fb884089f5584d06d2c29d1928e317d4e0ffad976026db01b46090752604056336f209febd719b463ff55d0c093eef72886675a96d6db277cf440e0c443deb68e71487c17c9dfadcea3e43438e2b89dac27c02c004bf6e4ebe0a4dec3b2b4722dd977549474d8363dc62898efbc6b777b7189b067a1c8f2aa2a6638c70f82206dcc7e99d8ec285e2a8d9b4ec348ac0550b185b8a6b4ab5a673492621de7883991c212549a7aded915a90fc04d3ed933282a0b4fe0e87251f9bc0d97232f8c666"},"role":[{"id":1,"name":"superadmin","display_name":"Superadmin","description":"Superadmin","created_at":"2018-02-08 01:47:34","updated_at":"2018-02-08 01:47:34","pivot":{"user_id":1,"role_id":1}}]}
```

___Note: We recommend using Postman while developing / testing the API (refer to "Next Steps" for more information)___

This concludes the initialization process for the ACTV8 API v4!

## Next Steps
1. For more information on how to interact with the API, refer to the ACTV8 API v4 Official Documentation in Swagger:
https://app.swaggerhub.com/apis/ACTV8me/ACTV8_API_v4_0_1/4.0
2. Install Postman for API development / testing: https://www.getpostman.com/ 

