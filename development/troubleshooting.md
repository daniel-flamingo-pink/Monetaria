# Troubleshooting

### Understanding Technical Support

It is important to note that Monetaria is to be used entirely at your own risk. Admins do not have special keys and cannot recover funds if they are sent improperly.

### I Cannot Connect to the Platform

If you are having trouble connecting to the platform, there are a few things you can try:

* Make sure you are selecting the correct network (Ethereum Mainnet). On your wallet provider, you should be able to switch networks in the settings option.
* If you are using Ledger natively or through Metamask:
  * Make sure you have unlocked and selected the Ethereum app.
  * Ensure that contract data is allowed in the Ethereum app settings.
* If you are using Coinbase:
  * Use the scan QR option to connect.
  * If you want to access the platform directly from Coinbase wallet, simply go to app.aave.com on the browser within the app.
* If you are using Wallet Connect:
  * Use the scan QR code to connect.
  * Make sure to enable contract data on your Ledger device as follows:
    1. Connect and unlock your Ledger device.
    2. Open the Ethereum application.
    3. Press the right button to navigate to Settings.
    4. Press both buttons to validate.
    5. In the Contract data settings, press both buttons to allow contract data in transactions. The device should display "Allowed".

### I Cannot Send Transactions

If you are unable to send transactions, it may be due to insufficient ETH in your account to communicate with the platform. Your wallet must have ETH to pay for transactions - without it, you will be unable to communicate. Transaction fees may vary based on the status of the network, but you may need at least 0.05 ETH to correctly communicate.

### The Site Does Not Load

If the site is not loading, you can try the following steps:

* If you are using Brave browser, try switching to another browser to see if the issue is coming from the browser. If the issue is related to Brave browser, you can try:
  * Clearing cache data and cookies for the site
  * Hard refreshing the site with `Control + F5` (or `Command + R` on a Mac)
  * Disabling Brave wallet (or the wallet not being used as default, e.g. Metamask, Dapper, etc.) or other extensions that might be interfering with proper connection with the wallet
* If the site still won't load after trying the above steps, you may need to use the platform in another browser.
* Make sure your internet connection is working and stable.
* Restart the browser and try to connect again.
* Try hard refreshing the site with `Control + F5`.
* Check if there are any updates for your browser or wallet provider and update if necessary.

### My Transaction is Stuck Pending Confirmation

If your transaction is stuck pending confirmation, do not continue to send transactions as each new transaction will hang, waiting for the confirmation of the earliest transaction. You can try to eliminate the pending transaction by accelerating or canceling it. This option may be available through your wallet provider - for example, Metamask or Trust Wallet may have options to reverse or accelerate transactions.

If your wallet provider does not have this option, you may still be able to remove the stuck transaction by sending a 0 ETH transaction to your own address with the same disposable number (number identifier) as the stuck transaction. You can check the one-time number in your transaction on Etherscan and then use interfaces like MEW and MyCrypto to submit a new transaction with a higher gas value and replace the stuck transaction.

Here are a few tutorials on the subject for [MEW](https://help.myetherwallet.com/en/) and [MyCrypto](https://support.mycrypto.com/how-to/sending/checking-or-replacing-a-transaction-after-it-has-been-sent/).

If you are still having issues, there are additional resources available to help you:

* This documentation contains common troubleshooting questions.
* The technical documentation is a comprehensive resource for coders.
* The Telegram and Discord channels have active support channels where you can ask for help.

Remember, most users use Monetaria without issue, but if you have questions or are experiencing issues, make sure to ask for help to avoid any potential problems.
