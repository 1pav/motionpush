## Intro

This script is intended to be used together with motionEye to provide support for push notifications on various platforms. Currently, the following platforms are supported:

- Telegram
- Pushover
- Gotify

As a bonus, the script can be configured to not send notifications or to send 
high-priority notifications during specified time intervals. High-priority notifications can bypass the recipient device's do not disturb settings, where supported.

## Installation

After downloading this repository, copy the script and its configuration, making sure to mark the script as executable:

```
git clone ${GIT_URL}
cd ./motionpush
cp motionpush /usr/local/bin
cp example.conf /etc/motionpush.conf
chmod +x /usr/local/bin/motionpush
```

## Configuration

Please see the comments in `example.conf`. They should provide enough information to understand which settings do what.

Edit the configuration file to suit your needs:

```
vim /etc/motionpush.conf
```

In motionEye's web interface, under `Motion Notifications`, enable `Run a Command` and put the path to the script in the `Command` field:

```
/usr/local/bin/motionpush %H:%M
```

Notice the argument `%H:%M`. This is required for do not disturb hours and high-priority hours settings to work.

## Usage

```
Usage:
  motionpush [OPTIONS] TIME

Description:
  Send motion notifications from motionEye to Pushover, Telegram and Gotify.
  TIME must be formatted as HH:MM.

Options:
  -c FILE path to configuration file (default: /etc/motionpush.conf)
  -v      explain what is being done
  -h      output usage and exit
```