# base-station

## How to run

1. In the client directory, run:

```
npm install
```

installs the necessary dependencies for the client app

2. In the server directory, run:

```
npm install
```

installs the necessary dependencies for the server app

3. In the server directory, you can run:

```
npm run dev
```

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

## Running with custom environment variables

In the root directory create a .env file

```
touch .env
```

Add the following values to the .env file

```
BROKER_URL=mqtt://<broker hostname or ip address>:<broker port>
PORT=<server port>
```

## Running with systemd

Suppose you are in the app directory `/home/$USER/foo`

1. Create file, let's call it foo.service

```
touch foo.service
```

2. In the file add

```
[Unit]
Description=Foo application

[Service]
User=<USER>
WorkingDirectory=/home/<USER>/foo
ExecStart=/usr/bin/npm run dev
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

4. Copy unit into systemd folder

```
cp foo.service /etc/systemd/system
```

5. Reload daemon

```
systemctl daemon-reload
```

6. Enable start on boot

```
systemctl enable foo.service
```

## systemd on raspberrypi example

Suppose you are in the app directory `/home/pi/Desktop/base-station`

1. Create file, let's call it bs.service

```
touch bs.service
```

2. In the file add

```
[Unit]
Description=Nakuja N2 base station software

[Service]
User=pi
WorkingDirectory=/home/Desktop/base-station/server
ExecStart=/usr/bin/npm run dev
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

4. Copy unit into systemd folder

```
sudo cp foo.service /etc/systemd/system
```

5. Reload daemon

```
sudo systemctl daemon-reload
```

6. Enable start on boot

```
sudo systemctl enable foo.service
```
