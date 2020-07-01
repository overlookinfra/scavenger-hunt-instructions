# Scavenger Hunt Instructions

> 🔍 This repository contains instructions and support files for the Scavenger Hunt game
> played at the Virtual Puppet Camps.

*Imagine that you've started a new role and when you log in to the infrastructure for
the first time, something about it just doesn't feel right...*

Your job is to run through the scenarios and figure out what's wrong. For most scenarios
fixing the problems isn't required. Instead, you'll answer a trivia question describing the
fix. The last scenario--the Big Boss, if you will--is a bit trickier and you'll actually
have to manually resolve the issue before completing the game.


## Getting Started

You'll need to be a member of our Slack to play. Join at https://slack.puppet.com and
pop into the `#puppet-camps` channel.

The game facilitator will post & pin a welcome message. To start the game, simply add a
🔍 reaction (`:mag:`) to that message. You'll get a message with your machine login
details from Slackbot. Maybe you already did that and followed the link...


## Logging in to your environment

You can play on either or both of a Windows or Linux environment. The answers are the
same except for minor implementation details.

### Linux

1. Save the `student.pem` file from this repo to your local machine.
1. Fix its permissions with `chmod 600 student.pem`
1. Log into your machine:

    `ssh -i ~/.ssh/student.pem -l centos puppetcampnix<n>.classroom.puppet.com`

1. Switch to the `root` account using `sudo -i`.

### Windows

Use RDP to log in. Use PowerShell to run Puppet and Bolt commands.

* `rdp://puppetcampwin<n>.classroom.puppet.com`
* `Administrator`/`PuppetLabs!`


## Playing the game

Start off by running `puppet agent -t`. This will ensure that your machine's set up
and will provide you with instructions for getting started. To move through the game
you'll run a Bolt task and then run Puppet.

The value passed to the task is always a hash, so be careful with quoting. The value
must parse as JSON, which requires double quotes. In the example below, you see that
the outer quotes are single and then inner quotes are double.

```
# bolt task run --targets localhost scavenger_hunt::external_fact value='{"start": "true"}'
# puppet agent -t
```

In `/root` or on the Administrator's desktop, you'll find a directory named `clues`.
They will provide you with the storyline and instructions for completing the scenario.
You might have to run commands to explore the system and you might have to google a
bit to find configuration settings.

Chat with each other, ask each other or the facilitator for hints, laugh about how
campy it is! Just have fun :)

Note: you're totally welcome to collaboratively solve the puzzles, but please do that
in a DM so that you don't reveal the answers to others trying to solve it on their own!
