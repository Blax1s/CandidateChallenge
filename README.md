# CandidateChallenge
[Deployment Link](http://20.2.74.69/sayHello)

## Workflow Details

### Trigger
The workflow triggers whenever code is pushed to the main branch.

### Checkout 
The `actions/checkout` action is used to clone the repository into the GitHub Actions workspace.

### Install npm dependencies
Node.js dependencies are installed using the `npm install` command.

### Archive Repository
The `montudor/action-zip` action is used to create a zip archive of the repository contents, excluding hidden files.

### Set up SSH key
The `webfactory/ssh-agent` action is used to set up the SSH key for secure communication with the virtual machine.

### Copy bundle to VM
The `appleboy/scp-action` action is used to securely copy the deployment bundle to the virtual machine.

### Deploy to VM
- Connects to the virtual machine via SSH.
- Cleans up the previous bundle or active processes if any.
- Unzips the new bundle and deletes the zip file.
- Node.js dependencies are verified using `npm install`.
- Deploys the application on PORT 80 using PM2.

## Secrets
- `SSH_PRIVATE_KEY`: SSH private key for secure communication with the virtual machine.
- `VM_HOST`: IP address or hostname of the virtual machine.
- `VM_USERNAME`: Username for connecting to the virtual machine.

## Challenges Faced
- Had to learn how to use/setup Github Secrets for the SSH key.
- Initially had trouble starting the node server (index.js) since running it on PORT 80 required root (sudo) priviliges.
- Figured out `action-zip` action for creating the bundle at the Github Actions workspace.
- Learnt about SCP to securely copy the bundle from the Github Actions workspace to the VM.
- Had to run the node process in the background using pm2 so that the Github Action does not keep running.