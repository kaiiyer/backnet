```
 ____             _    _   _      _   
| __ )  __ _  ___| | _| \ | | ___| |_ 
|  _ \ / _` |/ __| |/ /  \| |/ _ \ __|
| |_) | (_| | (__|   <| |\  |  __/ |_ 
|____/ \__,_|\___|_|\_\_| \_|\___|\__|

```

Backdoor+Botnet

![Python](https://alibahaari.github.io/Badge/Python.png)  ![HTML](https://alibahaari.github.io/Badge/HTML.png)   ![JS](https://alibahaari.github.io/Badge/CSS.png)    ![CSS](https://alibahaari.github.io/Badge/JavaScript.png)

![Git Actions](https://github.com/kaiiyer/backnet/workflows/Git%20Actions/badge.svg)
[![CircleCI](https://circleci.com/gh/kaiiyer/backnet/tree/master.svg?style=svg)](https://circleci.com/gh/kaiiyer/backnet/tree/master)
<a href="https://github.com/kaiiyer/backnet/issues"><img alt="GitHub issues" src="https://img.shields.io/github/issues/kaiiyer/backnet"></a>
<a href="https://github.com/kaiiyer/backnet/network"><img alt="GitHub forks" src="https://img.shields.io/github/forks/kaiiyer/backnet"></a>
<a href="https://github.com/kaiiyer/backnet/graphs/contributors" alt="Contributors">
<img src="https://img.shields.io/github/contributors/kaiiyer/backnet" /></a>

BackNet is a Python Remote Access Tool. It is made of two main programs:

- A Command and Control server, which is a Web interface to administer the agents
- An agent program, which is run on the compromised host, and ensures communication with the CNC

The Web interface can be run on any server running Python. The agent can be compiled to native executables using **pyinstaller**.

## Setup

Install the Python requirements:

```
pip install -r requirements.txt
```

Initialize the database:

```
cd server
./ares.py initdb
```

## Server

Run with the built-in server:

```
./ares.py runserver -h 0.0.0.0 -p 8080 --threaded
```

Or run using gunicorn:

```
gunicorn ares:app -b 0.0.0.0:8080 --threads 20
```

The server should start running on http://localhost:8080

## Agent

Run the Python agent (update config.py to suit your needs):

```
cd agent
./agent.py
```

Build a new agent to a standalone binary:

```
./builder.py -p Linux --server http://localhost:8080 -o agent
./agent
``` 

To see a list of supported options, run ./builder.py -h

```
./agent/builder.py -h
usage: builder.py [-h] -p PLATFORM --server SERVER -o OUTPUT
                  [--hello-interval HELLO_INTERVAL] [--idle_time IDLE_TIME]
                  [--max_failed_connections MAX_FAILED_CONNECTIONS]
                  [--persistent]

Builds an agent.

```
__Warning: Only use this software according to your current legislation. Misuse of this software can raise legal and ethical issues which I don't support nor can be held responsible for.__

Contributions are appreciated !
