---
title: "Build an Algorithmic Trading Bot in 7 Steps"
published: true
---
---

Build an Algorithmic Trading Bot in 7 Steps
Learn step-by-step how to build a trading bot using python, Alpaca API, Google Cloud Platform, and email notifications.


---

The purpose of this article is to provide a step-by-step process of how to automate one's algorithmic trading strategies using alpaca, python, and google cloud. For this particular example, I will be using the strategy of pairs trading. Please reference the following GitHub Repo to access the python script.
Step 1: Create accounts for Alpaca and Google Cloud Platform
Alpaca is a commission-free brokerage platform that allows users to trade via an API. Once you have created an account you will be given an API Key ID and a secret key which you will reference in the python script. This creates the bridge to automate your trading strategy. Here is the link to get started with Alpaca.
Google Cloud Platform is a top-tier cloud computing service. They offer hundreds of cloud products. However, for the purpose of this project, we will only be using two of their services. Google Cloud offers a free trial for new users that comes with $300 credit, which is more than you will need to automate this process. Leveraging a cloud service, such as Google, makes it so that you don't have to manually run your script daily - or be worried about your computer being on at the correct time each day. It alleviates the stress and runs seamlessly. Here is the link to get started with the Google Cloud Platform.
Once you have created your account - start the free trial. You can do this by clicking on Activate in the top right corner.
Fill out the needed information. Once you have completed this step. Go ahead and create a New Project. I labeled mine, Algo-trading.
Step 2: The python script.
The next few steps will go over how to structure the python script and how to attach the Alpaca API, how to send an email notification and how I built my trading logic. The first thing to remember with the python script is that you will need to create only one function. That function will then be called in Google Cloud. This is crucial to automate the script.
def pairs_trading_algo(self):
'''All the code necessary to connect to API, trading logic and sending email notification will go in here'''
return done
Step 3: Connect Alpaca API
Once you have created an account with Alpaca you can access your API keys. I will be using the paper trading keys for this example. On the right side of the Alpaca Dashboard, you will find this section. Below API Key ID you will find your secret key.
You will need to import the following packages, os, and alpaca_trade_api as tradeapi. Follow Alpaca's documentation on how to download the alpaca_trade_api package. Below is a snippet of the code found in the GitHub Repo.
The os.environ allows you to specify which environment you are wanting to connect to - paper trading or live trading.
The first blacked out area is where you will place your API Key ID, the second is where you will place your secret key.
The account variable is making sure that you have an account with Alpaca and that it is active. This variable will be used later on.


Step 4: Create a new email account and add email notification functionality to python function.
The first time I automated my trading script I didn't include an email notification. I have since added this capability and it is awesome. This enables me to know when my script ran and what the outcome was based on my trading strategy. I referenced this article written by Samuel Sam to get me started.
I created a new Gmail account for security reasons. I named the account Trading Bot. The most important step, whether you create a new account or use a different account is turning on access to less secure sites. Account Settings → Security → Less Secure app access ON


The snippet below includes the packages needed for sending emails. The subject of the email is the trading strategy, allowing me to know which strategy did what, on what day - allowing me to have the capability of running multiple trading strategies.


Step 5: Build a trading strategy into the script and add certain messages to email.
The following snippets show a very sloppy way of accessing the free data on Alpaca through IEX Exchange. We create the needed variables for the trading logic, such as 5-day moving averages and certain spreads. This example is using ADBE and AAPL. Once again, this code is available in the GitHub Repo.
Next is adding the trading logic with the desired text for the email. The portfolio variable checks to see what my current position is, which is important to the trading algo logic.


The clock variable allows me to check and see if the market is open. If it isn't, I will receive an email that says, "The Market is Closed". In the future, It would be beneficial to run a script prior to this to check if it is open or closed. If it open, I would then have this script run in the cloud - therefore, saving computing time and money.
The mail_content variable is written throughout the trading algorithm so that it catches whatever occurs dependent on the day. This is then placed in the email, the information for the login is fulfilled and the email is sent.
The last variable is created which is "done" and that is what the function spits out. Your script is created and ready to go.
Step 6: Create a Google Cloud Function
You will then open up the Google Cloud console. Make sure you are in your algo-trading project and then navigate to Cloud Functions on the left side panel, found under compute. I have pinned it for ease.
You will then click on Create Function at the top. This will take you to a page that looks like this.
Name the function whatever you would like. I kept all the pre-set settings but changed the Runtime to Python 3.7. You will then copy and paste the python script you have created into the main.py. Make sure to put the name of the function in the Function to Execute box.
The last step is to add the packages needed in the requirements.txt. This makes it so the cloud knows what packages you need for your python script to run. **Note: You may need to add other packages to this list if you add them to your main.py. Your function will not deploy if there are any packages missing from the requirements.txt. Go ahead and deploy the function.
To test the function, navigate to the Trigger tab within the function.
Click the URL and see what happens. If it runs correctly, the window should display, "Mail Sent" and you should have received an email. If this worked properly, copy the URL.
Step 7: Create a Google Scheduler Job
You will then navigate to the Google Scheduler on the left panel. It is located under tools. I have also pinned this for ease.
You will then create a new job.
This is what the screen looks like.
You will name it whatever you would like. For frequency, I have my function running every weekday at 8:30 AM MST, which puts it running an hour after the market opens.
You will paste the URL that you copied from the Cloud Function. After this, you are set. This will run, as you have specified, on its own. You can test the job, by clicking on Run Now.
If it runs successfully, you will have a nice email sitting in your inbox similar to the one below and money-making trades in Alpaca.
Conclusion
I hope that this step-by-step outline has helped you automate your favorite algo trading strategies and that you enjoy the email notifications. If you have any suggestions on how to improve this process or the trading strategy itself, send me a message.
Cheers.

# Highlighter
## Ruby
```ruby
def show
  puts "Outputting a very lo-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-ong lo-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-ong line"
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
```

## Php
```php
<?php
  print("Hello {$world}");
?>
```

## Java
```java
public class java {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

## HTML
```html
<html>
  <head><title>Title!</title></head>
  <body>
    <p id="foo">Hello, World!</p>
    <script type="text/javascript">var a = 1;</script>
    <style type="text/css">#foo { font-weight: bold; }</style>
  </body>
</html>
```

## Console
```console
# prints "hello, world" to the screen
~# echo Hello, World
Hello, World

# don't run this
~# rm -rf --no-preserve-root /
```

## Css
```css
body {
    font-size: 12pt;
    background: #fff url(temp.png) top left no-repeat;
}
```

## Yaml
```yaml
---
one: Mark McGwire
two: Sammy Sosa
three: Ken Griffey
```
