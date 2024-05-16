## [Docker Hub](https://hub.docker.com/repository/docker/daremarvel/aarogya_coin_repository/general)

# AarogyaCoin : Health Records Management Using Blockchain


## Introduction
The aim of this framework is firstly to implement blockchain technology for EHR and secondly to provide secure storage of electronic records by defining granular access rules for the users of the proposed framework. Moreover, this framework also discusses the scalability problem faced by the blockchain technology in general via use of off-chain storage of the records. This framework provides the EHR system with the benefits of having a scalable, secure and integral blockchain-based solution.
<!-- TABLE OF CONTENTS -->

## Installation

The projects requires NodeJS and npm to work. Instructions to install all other dependencies are given below.
### Node modules

1. Move to the project directory and open it in your terminal.
2. Run `npm install` to install project dependenccties.

### Ganache

1. Go to [Ganache homepage](https://truffleframework.com/ganache) and download. 
2. If you are on Linux, you must have received an _.appimage_ file. Follow installation instructions available [here.](https://itsfoss.com/use-appimage-linux/)

### IPFS

# Install IPFS in Windows

## Install Go

- Head to the [download website](https://golang.org/dl/)
- Click the latest version and download the `.msi` file

## Create Paths

- Create `GOROOT` system variable if it doesn't exist in `C:\Go`
- Create a `PATH` environment variable at `C:\Go\bin`
- Create a working environment system variable called `GOPATH` at a location where you want your Go projects install
	+ If you check around github, this is referred to as `$GOPATH` in Mac/Linux or `%GOPATH%` in Windows
	+ Don't be confused, it's just a convenient shortcut
		* For example: we'll create a new system variable called `GOPATH` at `C:\OpenBazaar\Go`
		* Here `%GOPATH%` is `C:\OpenBazaar\Go`
		* So `%GOPATH%\src\github.com` is the same as writing `C:\OpenBazaar\Go\src\github.com`
	+ Check to see if this worked by opening a new terminal and typing `echo %GOPATH%`
		* The output should the path you set in the system variable (i.e. `C:\OpenBazaar\Go` in our example)
- Close and reopen the terminal to ensure the paths are set 

## Install Dependencies

- Install `gx`
	+ Open the terminal and type `go get -u github.com/whyrusleeping/gx`
		* This will install `gx` in `%GOPATH%\src\github.com\whyrusleeping/gx`
- Install `gx-go`
	+ Open the terminal and type `go get -u github.com/whyrusleeping/gx-go`
		* This will install `gx-go` in `%GOPATH%\src\github.com\whyrusleeping/gx-go`
- Close and reopen the terminal to ensure the paths are set 

## Install IPFS

- Download _without_ installing `ipfs`
	+ Open the terminal and type `go get -d github.com/ipfs/go-ipfs`
		* This will install `ipfs` in `%GOPATH%\src\github.com\ipfs\go-ipfs\`
	+ Then type `cd %GOPATH%\src\github.com\ipfs\go-ipfs`
	+ Install with `gx` with the following command `gx --verbose install --global`
	+ Then type `cd cmd/ipfs && go build`
	+ IPFS should now be installed, test to see if you get a response by typing `ipfs` in the terminal
- Add `ipfs.exe` to your environment variables path
  + `%GOPATH%\src\github.com\ipfs\go-ipfs\cmd\ipfs` (use the full file path, don't write in `%GOPATH`)

### Local server

1. Install Node lite-server by running the following command on your terminal `npm install -g lite-server`

### Metamask

1. Metamask is a browser extension available for Google Chrome, Mozilla Firefox and Brave Browser.
2. Go to the this [link](http://metamask.io/) and add Metamask to your browser.

## Getting the dApp running

### Configuration

#### 1. Ganache
  - Open Ganache and click on settings in the top right corner.
  - Under **Server** tab:
    - Set Hostname to 127.0.0.1 -lo
    - Set Port Number to 8545
    - Enable Automine
  - Under **Accounts & Keys** tab:
    - Enable Autogenerate HD Mnemonic

#### 2. IPFS
  - Fire up your terminal and run `ipfs init`
  - Then run 
    ```
    ipfs config --json API.HTTPHeaders.Access-Control-Allow-Origin "['*']"
    ipfs config --json API.HTTPHeaders.Access-Control-Allow-Credentials "['true']"
    ipfs config --json API.HTTPHeaders.Access-Control-Allow-Methods "['PUT', 'POST', 'GET']"
    ```

    > Note: If you face any issues with the above command on windows, try using command prompt and escape sequences or git bash.
#### 3. Metamask
  - After installing Metamask, click on the metamask icon on your browser.
  - Click on __TRY IT NOW__, if there is an announcement saying a new version of Metamask is available.
  - Click on continue and accept all the terms and conditions after reading them.
  - Stop when Metamask asks you to create a new password. We will come back to this after deploying the contract in the next section.
  
### Smart Contract

1. Install Truffle using `npm install truffle -g`
2. Compile Contracts using `truffle compile`

#### 1. Starting your local development blockchain
  - Open Ganache.
  - Make sure to configure it the way mentioned above.
  
1. Open new Terminal and deploy contracts using `truffle migrate`
2. Copy deployed contract address to src/app.js 
![alt text](https://raw.githubusercontent.com/SuyashMore/SwasthyaChain/master/images/ganace-contracct.png)

```js
// app/src/app.js  line number 11
var agentContractAddress = '0x75E115394aacC7c6063E593B9292CB9417E4cbeC';
```

3. If you change contents of any contract , replace existing deployment using `truffle migrate --reset`
> Note :  reset of the contract will change the contract Address which needs to be updated in src/app.js

### Running the dApp

#### 1. Connecting Metamask to our local blockchain
  - Connect metamask to localhost:8485
  - Click on import account
  ![alt text](https://raw.githubusercontent.com/SuyashMore/SwasthyaChain/master/images/meta-1.png)
  - Select any account from ganache and copy the private key to import account into metaMask
  ![alt text](https://raw.githubusercontent.com/SuyashMore/SwasthyaChain/master/images/con-g1.png)

#### 2. Starting IPFS
- Go in command prompt and start IPFS application by going to the appropriate directory:
```
cd C:\Users\<username>\go\pkg\mod\github.com\ipfs\kubo@v0.28.0\cmd\ipfs>
```
- Start IPFS Daemon
```
ipfs daemon
```

  
#### 3. Start a local server
  - Open a new terminal window and navigate to `/YOUR_PROJECT_DIRECTORY/app/`.
  - Run `npm start`.
  - Open `localhost:3000` on your browser.
  - That's it! The dApp is up and running locally.
