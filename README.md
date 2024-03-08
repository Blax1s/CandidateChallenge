# CandidateChallenge

## Workflow Details
- The workflow retrieves the SSH key from Github secrets and uses it to connect to the VM.
- After the connection is established, it clones the github repository into the appropriate directory.
- The node server is then started as background process on PORT 80 using nohup.
- [Deployement Link](http://20.2.74.69/sayHello)

## Challenges Faced
- Had to learn how to use/setup Github Secrets for the SSH key.
- Initially had trouble starting the node server (index.js) since running it on PORT 80 required root (sudo) priviliges.
- Had to run the node process in the background using pm2 so that the Github Action does not keep running.