# DisSlack
A Serverless AWS Lambda function that runs once an hour, checks for new Disqus comments on your site and posts them to whatever Slack channel you specified when setting up your Slack incoming webhook.

It uses one DynamoDB table to simply store the timestamp of the last time it ran so it avoids repeated posting.

## Setup

(Assuming you have your AWS access credentials already setup)

1. Setup webhook [here](https://my.slack.com/services/new/incoming-webhook)
2. Setup Disqus App [here](https://disqus.com/api/applications/)
3. Then:

```bash
git clone git@github.com:conoro/disslack.git
cd disslack
```

4. Rename disslack-sample.env.yml to disslack.env.yml
5. Edit disslack.env.yml and save the values from step 1 and 2
6. Then:

```bash
npm install -g serverless
npm install
serverless deploy
```


Notes: 
1. You can also invoke it manually by accessing the GET URL returned by the successful serverless deploy
2. You can check logs with: 

```bash
serverless logs -f check
```

3. If you make minor changes to just the function code, you can do a quick re-deploy with: 

```bash
serverless deploy function -f check
```


LICENSE Apache-2.0



Copyright Conor O'Neill 2017, conor@conoroneill.com
