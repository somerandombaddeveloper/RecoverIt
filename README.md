# RecoverIt
RecoverIt is a data recovery module for Roblox to help gain access to lost DataStores.

RecoverIt works by using a password system for accesing data stores.
# How it works
![chartforrecoverit](https://user-images.githubusercontent.com/106110368/184519521-5c918928-0a68-4d18-a269-922603725687.png)

When users join the game, their UserId is associated in a key, which has a password that the user can set.
In the event that a user's account has been lost or terminated, they can enter a password and RecoverIt can be used to recover the DataStore.
# Summary of Script
You can prevent banned players from accessing data by adding them to a table of UserIDs:
```
--Add banned player's userids into this table
bannedplayers = {}
```
You can also associate a TextBox or anything else to enter in the DataStore key and password:
```
--Assign a TextBox or anything that you can use as text input to enter the player's password
password = "insertpasswordhere"
key = "insertkeyhere"
```
You can assign the DataStores as so:
```
datastoreservice = game:GetService("DataStoreService")
--Assign the key as the player's UserId or DataStore key below
datastore = datastoreservice:GetDataStore("insertdatastorehere")
--Assign a password datastore to the player before hand and detect it with the if-statement
passdatastore = datastoreservice:GetDataStore("insertpassworddatastorehere")
```
Call the function RecoverData to start data recovery and add any code to run if successful:
```
function RecoverData()
	if (passdatastore:GetAsync(key) == password and key ~= bannedplayers)  then
		print("Data recovery successful!")
		--Add data recovery scripts to load in the data and anything else you want to do with it
	else
		print("Data recovery failed. Please try again with a different password.")
		--Trigger "Recovery Failed" messages here
	end

end
```
