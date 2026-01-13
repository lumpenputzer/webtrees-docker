# Docker image for webtrees

This is a Docker image for [webtrees](https://webtrees.net/) using the [FrankenPHP App Server](https://frankenphp.dev/). Heavily inspired by [NathanVaughn's image](https://github.com/NathanVaughn/webtrees-docker).

It is tailored to my personal requirements, as such it offers limited customizability:
- It deploys the webserver with TLS using a custom certificate on a non-system port (i.e. port number > 1023), because it's intended to be used behind a reverse proxy (The TLS is only used to secure the communication between this server and the reverse proxy).
- It assumes usage of a PostgreSQL database.
- PHP configuration is set to options suitable for production usage following [webtree's recommendations](https://webtrees.net/admin/performance/).
- ImageMagick is installed.
- webtrees' configuration needs to be done manually in its `config.ini.php`.
- webtrees' update function is not tempered with (you will receive update notifications from webtrees). HOWEVER, webtrees' files within the container are set to read-only, so [automatic upgrades](https://webtrees.net/upgrade/automatic/) will fail. Upgrade by pulling/rebuilding the image.
- I have only ever used this with an existing webtrees install, but the setup wizard _should_ work. Your mileage may vary.
- It's always based on the latest stable release of webtrees and uses the latest supported version of PHP and the latest stable version of FrankenPHP.\*

\* I make no guarantees for how quickly I'll update the image when webtrees releases an update.
