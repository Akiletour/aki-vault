Aki's Vault is a simpler version of the amazing Yopass frontend. This version does not support file uploads or custom decryption key.

The sole purpose of Yopass is to minimize the amount of passwords floating around in ticket management systems, Slack messages and emails. The message is encrypted/decrypted locally in the browser and then sent to yopass without the decryption key which is only visible once during encryption, yopass then returns a one-time URL with specified expiry date.

![img](./public/preview.png)

## Getting Started

First, install dependencies and run the development server:

```bash
yarn install
yarn start
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Environment variables

You must define an environment variable to specify where the backend server is located.

Create an `.env.local` at the root of this project and define your variable :

```
REACT_APP_BACKEND_URL="https://vault.your-company.fr/backend"
```

Of course, replace the URL with your Yopass Server Backend URL.

You can check the section `Nginx configuration` if you want to hide the backend url from the public.

## Nginx configuration

If you don't want to expose your backend URL, you can easily create a proxy on your nginx vhost configuration like this : 

```nginx
server {
 [...]

 location /backend/ {
   proxy_pass http://127.0.0.1:1337/;
 }
}
```

## Build

Simply run the command bellow to build the frontend with React.

```bash
yarn build
```

A new `build` directory has now appeared, it's an static export of the react app, you can place it whereever you want.

## Build and install yopass-server
```bash
# sudo apt-get install golang
git clone https://github.com/jhaals/yopass.git
cd yopass
go build ./cmd/yopass-server
```
and then, [read the doc](https://github.com/jhaals/yopass#installation--configuration)

