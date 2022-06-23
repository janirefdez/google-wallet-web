# Google Wallet Codelab

This project contains sample code used for the [Google Wallet Codelab](https://codelabs.developers.google.com/save-to-wallet-web)

## Requirements

### Create service account

The Google Wallet APIs use service accounts for authentication.

You will first need to create a service account and download its service account key file. You can do that with the `gcloud` [command-line tool](https://cloud.google.com/sdk/docs/install), so make sure to install it, if you haven't before.

- Open up your terminal, and define a `PROJECT_ID` variable. For example if your project ID was my-cloud-project

    `export PROJECT_ID=my-cloud-project`

- Run the following command to create a service account:

    `gcloud iam service-accounts create wallet-codelab --project=$PROJECT_ID`

- Run the following command, which will create and download a service account key file:

    `gcloud iam service-accounts keys create ./key.json --iam-account=wallet-codelab@$PROJECT_ID.iam.gserviceaccount.com --project=$PROJECT_ID`

- Note the path to the key.json file in the current directory. You will need to include it [here](https://github.com/janirefdez/google-wallet-web/blob/f826c7de7e5b47611b6324799f1bb61f578d88c9/app.js#L23) (the following command will display it)

    `echo $(pwd)/key.json`

- Enable the Wallet API using the following command:

    `gcloud services enable walletobjects.googleapis.com --project=$PROJECT_ID` 

### Create a temporary issuer account

To create passes for your user, you first need to create an issuer account, enable the Wallet API, and then create a class, all of which can be done via the Google Pay Business Console. However, access to this is only granted once the approval process is complete. But you can create a temporary issuer account, and a pass class for you.

NOTE: The email address that you use to generate the temporary issuer account, has to be the same as the one that is created for the service account. In the codelab, that is `wallet-codelab@$PROJECT_ID.iam.gserviceaccount.com`.

Click [Create a temporary issuer account](https://wallet-lab-tools.web.app/issuers) and a sample class. Take note of the issuer ID and class ID.

## Run this project

### Install project dependencies

This sample app consists of a simple Node.js app. Install the dependencies with the following command:

`npm install .`

### Run Node.js
You should now be able to run the Node.js app with the following command:

`node app.js`

Open `http://localhost:3000/` in your browser. You should be able to see something like this:
<img width="596" alt="image" src="https://user-images.githubusercontent.com/20024632/175397910-71f422c2-523e-4ac7-9011-a85e4c71baef.png">

### Test App 

First make sure you have included the correct key location in [code](https://github.com/janirefdez/google-wallet-web/blob/f826c7de7e5b47611b6324799f1bb61f578d88c9/app.js#L23). 
Then in the browser you should include the email, issuer ID and class ID obtained when creating the temporary issuer account. 

In case you are not using a temporary account you can take those details from Google Wallet API Dashboard
<img width="571" alt="image" src="https://user-images.githubusercontent.com/20024632/175398485-931a6dfd-ddaa-447b-8835-5c287e8e294c.png">

### Demo

https://user-images.githubusercontent.com/20024632/175398982-6a976b3c-a3fe-4174-bdad-e925f1bffd29.mov






