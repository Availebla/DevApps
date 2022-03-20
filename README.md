# DevApps

DevApps is a simple app created to send a notification to a telegram channel, DevApps, when changes are committed to this repository: [Availebla/DevApps](https://github.com/Availebla/DevApps).

## Getting Started

### Apps Used

* Github Actions Workflow
* Webhooks integrations: https://ifttt.com/maker_webhooks
* IFTTT: If This Then That service
* Telegram

### Executing program

1. Commit a change to this repository
2. Take a sip of coffee
3. Receive a telegram notification confirming that a change has been made

![Image](images/TelegramNotification.png)

## How it works

The app utilizes github actions which runs a workflow every time a change is committed onto the main branch. This worflow is documented here: (.github/workflows/CICD.yml). The key line of code performs a POST web request with a JSON payload that is recieved by webhooks with a predefined event trigger and a personal key to connect to the IFTTT applet. The IFTT applet then posts a message to telegram (as shown in the screenshot above) to confirm a change has been made.

### Github Actions Workflow: Essential Code
```
curl -X POST -H "Content-Type: application/json" -d '{"A change has been committed":"Kaboom!"}' https://maker.ifttt.com/trigger/commited/json/with/key/${{ secrets.WEBHOOKS_SECRET }}
```
Breaking down the code, there are few important components:
| Code Component | Description |
| ----------- | ----------- |
| '{"A change has been committed":"Kaboom!"}' | This is the JSON Payload which is delivered to our IFTTT applet using the POST command |
| trigger/commited/ | 'commited' is the pre-configured event name used to trigger our IFTTT applet |
| ${{ secrets.WEBHOOKS_SECRET }} | The IFTTT webhooks key is unique to your applet and should this repo be forked, will need to be replaced with your own Secret Key! |

The Unique Secret key can be found by visiting this page after you've created the applet on IFTTT: https://maker.ifttt.com/use
This is then added into the repository settings as a Key-Value pair as shown in the screenshot below
![Image](images/Secret.png)

![Image](images/WebhooksTrigger.png)

## Authors

Contributors names and contact info

ex. Dominique Pizzie  
ex. [@DomPizzie](https://twitter.com/dompizzie)

## Version History

* 0.2
    * Various bug fixes and optimizations
    * See [commit change]() or See [release history]()
* 0.1
    * Initial Release

## License

This project is licensed under the [NAME HERE] License - see the LICENSE.md file for details

## Acknowledgments

Inspiration, code snippets, etc.
* [ASCII ART](https://text-symbols.com/ascii-art/)
* [Github Actions secrets](https://www.youtube.com/watch?v=WuWsg0Ldess)
* [zenorocha](https://gist.github.com/zenorocha/4526327)
* [fvcproductions](https://gist.github.com/fvcproductions/1bfc2d4aecb01a834b46)
* Stress Relief: [Wordle 274 6/6](https://www.nytimes.com/games/wordle/index.html)

  ⬜⬜⬜🟩⬜

  ⬜⬜🟨🟩⬜

  ⬜⬜⬜🟩🟨

  ⬜🟨🟨🟩⬜

  🟩🟩⬜🟩⬜

  🟩🟩🟩🟩🟩
