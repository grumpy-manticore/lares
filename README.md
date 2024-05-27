# lares

[The Lares](https://en.wikipedia.org/wiki/Lares) are guardian deities, broadly speaking, of a place.

`lares` is my collection of Docker Compose files for self-hosted services. This repo serves as documentation for those resources and, hopefully, a useful reference for other folks.

## prod

`prod` contains services running on my "production" servers. These services are intended to be stable so that other people could potentially use them.

## lab

`lab` contains services that I'm trying out or messing with. They aren't in a production setting and might not actually be deployed (and thus, not updated).

## environment variables

Most services require some level of configuration via `.env` files or related configurations. Obviously, Some of these might even be secrets.

Obviously, I'm not going to commit those secrets to a public repo - I'm already a little nervous about publishing compose files.

Instead, a `.env.example` will exist for each service. The README for each service will tell you how to set up your `.env` secrets.
