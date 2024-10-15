
# ECO-Wallet.Plugin

##### _The ECO-Wallet.plugin should work in a manner that it would connect all the member/users of the iHunt4 with the users in sub-databases and vice versa._
####
####
> Example, 
> A developer used ECO-Wallet.plugin to create his gaming app called “Hit the Ball”,
> A user of iHunt4 app downloads “Hit the Ball” app, and went to SignUp/LogIn screen, here the user shouldn’t have to SignUp as new player, he/she should be able to Login using the same credentials as iHunt4 app.
<p align="center">
<img width="750" src="https://user-images.githubusercontent.com/15853904/139066247-78147552-3736-4754-901a-ff7ebe4b56d2.png" alt="iHuntDB logo">
</p>
If one would observe above flow, when a new developer signs up for iHunt4 Developer account. A new sub-database is created inside iHunt4 DB. Onwards, developer will be using his API-Key and API-Secret to make a call upon each and every Dynamic API Functions provided as following,


1.	**[signUp_to_ECO-Wallet]**, this API will signUp new user directly into iHunt4 database, as well as in the sub-database of the app developer. In addition, to call this API it requires to pass following values,
```yaml
{
   “name”: “Eric”,
   “email”: “eric@email.com”,
   “password”: “123123123”,
   “contact_no”: “000001111”, 	 
   “gender”: “n/a”, 		
   “date_of_birth”: “00-00-0000” 	
}
```
###### Providing correct values should return following outcome,

```yaml
{
   “status”: “200”,
   “message”: “user registration successful”
}
```

###### If user already exists in the system,

```yaml
{
   “status”: “200”,
   “message”: “user already registered”
}
```

_____________________________________________________________________

2.	**[login_to_ECO-Wallet]**, calling this API requires passing of following credentials,
```yaml
{
   “email”: “eric@email.com”,
   “password”: “123123123”
}
```
###### If the credentials are correct, the outcome should be as following,

```yaml
{
   “status”: 200,
   “message”: “user found”,
   “user_id”: “22”,
   “token”: “%$234wdsff1@”
} 
```
###### Otherwise, if the user is not found or credentials are not provided correctly, the outcome should be as following,

```yaml
{
   “status”: 200,
   “message”: “user not found”,
   “user_id”: “n/a”,
   “token”: “n/a”
}
```

_____________________________________________________________________

3.	**[get_user_profile]**, to make a call upon this API function, passing of the following values is required,
```yaml
{
   “user_id”: “22”,
   “token”: “%$234wdsff1@”
}
```
###### If the user has not yet logged into his/her xumm account, it should return the outcome as following, 

```yaml
{
   "status": 200,
   	 "data": 
       {
         “id”: “22”,
         “name”: “Eric”,
         “email”: “eric@email.com”,
         “contact_no”: “000001111”,
         “date_of_birth”: “00-00-0000”,
         “gender”: “n/a”,
         “delivery_address”: “n/a”,
         “xumm_account”: “n/a”,
         "assets": [],
         “date_created”: “2020-10-02 00:00:00”,
         “date_updated”: “n/a”,
         “last_login”: “2021-09-07 01:54:02”,
}
```
###### If the user has already logged into his/her xumm account, it should return the outcome as following,

```yaml
{
   "status": 200,
   "data": 
      {
         “id”: “22”,
         “name”: “Eric”,
         “email”: “eric@email.com”,
         “contact_no”: “000001111”,
         “date_of_birth”: “00-00-0000”,
         “gender”: “n/a”,
         “delivery_address”: “n/a”,
         “xumm_account”: “rDpw131ffoine34xxxxxxxxxxxxxxx43112a”,       
         "assets":
         [
            {
               "currency": "XRP",
               "balance": "12",
               "issuer": ""
            },
            {
               "currency": "ECO-Wallet",
               "balance": "200",
               "issuer": "raP6XZypcsSxxxxxxxxxxq24W89sDg"
            }
         ],
         “date_created”: “2020-10-02 00:00:00”,
         “date_updated”: “n/a”,
         “last_login”: “2021-09-07 01:54:02”,
}
```


## Developers Guide For ECO-Wallet Plugin Setup.

1.	A developer will go to www.ihunt4.com/developersPortal/register and signUp for new iHunt4-Developers-Account.

<p align="center">
<img width="450" src="https://user-images.githubusercontent.com/15853904/139068050-854c3f95-4702-4d47-a6e5-2ae6e4e7d6d1.png" alt="ECO-WalletP 1 logo">
</p>


2.	Developer will Login to www.ihunt4.com/developersPortal/LogIn 

<p align="center">
<img width="450" src="https://user-images.githubusercontent.com/15853904/139068403-060e351b-a16d-498a-9ce6-b99e59f2de8f.png" alt="ECO-WalletP 2 logo">
</p>

3.	Upon Login new API-key and API-Secret will be generated for the developer on the dashboard.

<p align="center">
<img width="450" src="https://user-images.githubusercontent.com/15853904/139068511-d449fd2a-2a03-4df6-bc13-7ff066a51885.png" alt="ECO-WalletP 3 logo">
</p>


###### NOTE: Developers will have the option to go with traditional points-system or they can choose to use ECO-Wallet point-system that would reward players as ECO-Wallet per point.

### ***1 Point = 1 ECO-Wallet***


4.	If the developer is interested in granting users ECO-Wallet tokens as rewards, he/she needs to “Login to ECO-Wallet wallet”. 
And upon successful login following UI will appear,
-	ECO-Wallet amount that developer holds in his/her wallet
-	Buy ECO-Wallet button - to top-up developers account with more ECO-Wallet.
-	Switch button - to switch to other ECO-Wallet wallets.
-	Settings button - that will take user to wallet settings screen. 

<p align="center">
<img width="450" src="https://user-images.githubusercontent.com/15853904/139068619-32cba570-b767-45b5-a709-90a3fe78233b.png" alt="ECO-WalletP 4 logo">
</p>

5.	Upon click to the settings button, following screen will appear, holding following options,
-	An option to put control of payment release.
-	An option to put certain players on the black-list/blocked-list. Devs can add or remove certain players.
-	A list that will show player waiting for their payments/rewards. Devs can add or remove certain players.
-	An Instant Pay button that would open up “Instant pay screen”, allowing devs to make instant pay.

<p align="center">
<img width="450" src="https://user-images.githubusercontent.com/15853904/139069061-86b8e6b3-305e-48b8-bab3-efa525482191.png" alt="ECO-WalletP 5 logo">
</p>

6.	Following is Instant pay screen that can be accessed by the developers, when clicked on “Instant Pay” button in the main Wallet settings.

<p align="center">
<img width="450" src="https://user-images.githubusercontent.com/15853904/139069153-4286d44c-59fd-46a5-91e1-e77f17c9de77.png" alt="ECO-WalletP 6 logo">
</p>

###### ***Also, a developer will be able to access web page containing “API Docs”, that would provide developer with the functions to connect their app with their backend.***

7.	Developer will go to www.github.com/treasureDev/ECO-Walletplugin and download the plugin for Unity games.

8.	Plugin will get installed and would provide developer with ready to implement components and code.


9.	Plugin will hold the following features,
a.	Demos.
b.	Xumm Login/Registration process.
c.	ECO-Wallet/XRP exchange.
d.	Various dynamic APIs that would assist devs to create and manage their games.
