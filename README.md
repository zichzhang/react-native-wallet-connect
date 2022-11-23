### Pre-reqs: 

- Install node v14.21.1

```
$ brew install node@14
$ brew unlink node
$ brew link node@14
```

If error:

`$ brew link --force --overwrite node@14`

- Install python 

`$ brew install python`

 - Create symbiotic links:

`$ ln -s "$(brew --prefix)/bin/python"{3,}`


### Step 1:  Clone repo https://github.com/cawfree/create-react-native-dapp

```
$ git clone https://github.com/cawfree/create-react-native-dapp.git
```

### Step 2:  Install expo and create dapp

```
$ npm install -g expo-cli
$ npx create-react-native-dapp
```

### Step 3: Make modifications to files

If creation of dapp is successful, create folder called “frontend” at root, and add the `App.tsx` file in that folder
Inside of the root `package.json`, change ts-node version to “10.9.1”

```
"ts-node": "10.9.1"
```

### Step 4:  Run the dapp in expo

```
$ cd app-name
$ expo run:ios
```

### Step 5: Connect Wallet

Inside of App.tsx, first import the useWalletConnect library,

```
import { useWalletConnect } from '@walletconnect/react-native-dapp';
```

then,  instantiate a connector inside of the main App() function:

```
const connector = useWalletConnect();
```

and finally, create the connect wallet component inside of the render/return function:

```
return (
<View style={styles.container}>
      { !connector.connected ?
      	<Button
          	title="Connect Wallet"
          	onPress={() => connector.connect()}
        	/>
        	:
        	<Button
          	title="Disconnect Wallet"
          	onPress={() => connector.killSession()}
        	/>
      }
</View>
);
```
