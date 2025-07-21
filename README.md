> [!NOTE]
> Want to learn more about Mastodon?
> Click below to find out more in a video.

<p align="center">
  <a style="text-decoration:none" href="https://www.youtube.com/watch?v=IPSbNdBmWKE">
    <img alt="Mastodon hero image" src="https://github.com/user-attachments/assets/ef53f5e9-c0d8-484d-9f53-00efdebb92c3" />
  </a>
</p>

<p align="center">
  <a style="text-decoration:none" href="https://github.com/mastodon/mastodon/releases">
    <img src="https://img.shields.io/github/release/mastodon/mastodon.svg" alt="Release" /></a>
  <a style="text-decoration:none" href="https://github.com/mastodon/mastodon/actions/workflows/test-ruby.yml">
    <img src="https://github.com/mastodon/mastodon/actions/workflows/test-ruby.yml/badge.svg" alt="Ruby Testing" /></a>
  <a style="text-decoration:none" href="https://crowdin.com/project/mastodon">
    <img src="https://d322cqt584bo4o.cloudfront.net/mastodon/localized.svg" alt="Crowdin" /></a>
</p>

Mastodon is a **free, open-source social network server** based on ActivityPub where users can follow friends and discover new ones. On Mastodon, users can publish anything they want: links, pictures, text, and video. All Mastodon servers are interoperable as a federated network (users on one server can seamlessly communicate with users from another one, including non-Mastodon software that implements ActivityPub!)

Click below to **learn more** in a video:

[![Screenshot](https://blog.joinmastodon.org/2018/06/why-activitypub-is-the-future/ezgif-2-60f1b00403.gif)][youtube_demo]

[youtube_demo]: https://www.youtube.com/watch?v=IPSbNdBmWKE

## Tristan's Fork

This is Tristan's (@trisweb) fork of Mastodon, for storing my modifications and specific configuration for my server. Since Mastodon's configuration is often intertwined with the code itself, keeping a separate branch is a decent way to ensure my setup is saved properly and kept up to date systematically.

Primary modifications and changes:

* Update the docker-compose.yaml configuration to suit my server capacity and needs.
* Change the default SSL setting and implementation to disable SSL (as my server is in front of a proxy that handles SSL)
* Add the `MAX_POST_CHARS` environment variable via PR mastodon/mastodon#27629 [from shleeable/mastodon-aussocial](https://github.com/shleeable/mastodon-aussocial/tree/patch-1)

### Instructions for Updating This Fork

**To update and merge in upstream changes:**

```sh
git checkout main # Ensure we're on the main branch
git fetch upstream
git merge upstream/main
git push origin main
```

**To pull latest tags:**

```sh
git fetch --tags upstream
git push origin --tags
```

**To pull in changes from a tag (uograde)**

```sh
git checkout trisweb-v4.2.3  # Example
git merge v4.2.4 # Merge in new changes
```

Resolve any conflicts and push changes.

Once pulled on the server, the new code will need to be built for the container. This can
be made more efficient by only building the web container, as it's where tne only changes are.

```sh
docker compose build web
docker compose down && docker compose up -d
```

## Navigation

- [Project homepage 🐘](https://joinmastodon.org)
- [Support the development via Patreon][patreon]
- [View sponsors](https://joinmastodon.org/sponsors)
- [Blog](https://blog.joinmastodon.org)
- [Documentation](https://docs.joinmastodon.org)
- [Roadmap](https://joinmastodon.org/roadmap)
- [Official Docker image](https://github.com/mastodon/mastodon/pkgs/container/mastodon)
- [Browse Mastodon servers](https://joinmastodon.org/communities)
- [Browse Mastodon apps](https://joinmastodon.org/apps)

[patreon]: https://www.patreon.com/mastodon

## Features

<img src="/app/javascript/images/elephant_ui_working.svg?raw=true" align="right" width="30%" />

**No vendor lock-in: Fully interoperable with any conforming platform** - It doesn't have to be Mastodon; whatever implements ActivityPub is part of the social network! [Learn more](https://blog.joinmastodon.org/2018/06/why-activitypub-is-the-future/)

**Real-time, chronological timeline updates** - updates of people you're following appear in real-time in the UI via WebSockets. There's a firehose view as well!

**Media attachments like images and short videos** - upload and view images and WebM/MP4 videos attached to the updates. Videos with no audio track are treated like GIFs; normal videos loop continuously!

**Safety and moderation tools** - Mastodon includes private posts, locked accounts, phrase filtering, muting, blocking, and all sorts of other features, along with a reporting and moderation system. [Learn more](https://blog.joinmastodon.org/2018/07/cage-the-mastodon/)

**OAuth2 and a straightforward REST API** - Mastodon acts as an OAuth2 provider, so 3rd party apps can use the REST and Streaming APIs. This results in a rich app ecosystem with a lot of choices!

## Deployment

### Tech stack

- **Ruby on Rails** powers the REST API and other web pages
- **React.js** and **Redux** are used for the dynamic parts of the interface
- **Node.js** powers the streaming API

### Requirements

- **PostgreSQL** 13+
- **Redis** 6.2+
- **Ruby** 3.2+
- **Node.js** 20+

The repository includes deployment configurations for **Docker and docker-compose** as well as specific platforms like **Heroku**, and **Scalingo**. For Helm charts, reference the [mastodon/chart repository](https://github.com/mastodon/chart). The [**standalone** installation guide](https://docs.joinmastodon.org/admin/install/) is available in the documentation.

## Contributing

Mastodon is **free, open-source software** licensed under **AGPLv3**.

You can open issues for bugs you've found or features you think are missing. You
can also submit pull requests to this repository or translations via Crowdin. To
get started, look at the [CONTRIBUTING] and [DEVELOPMENT] guides. For changes
accepted into Mastodon, you can request to be paid through our [OpenCollective].

**IRC channel**: #mastodon on [`irc.libera.chat`](https://libera.chat)

## License

Copyright (c) 2016-2025 Eugen Rochko (+ [`mastodon authors`](AUTHORS.md))

Licensed under GNU Affero General Public License as stated in the [LICENSE](LICENSE):

```
Copyright (c) 2016-2025 Eugen Rochko & other Mastodon contributors

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU Affero General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option) any
later version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE. See the GNU Affero General Public License for more
details.

You should have received a copy of the GNU Affero General Public License along
with this program. If not, see https://www.gnu.org/licenses/
```

[CONTRIBUTING]: CONTRIBUTING.md
[DEVELOPMENT]: docs/DEVELOPMENT.md
[OpenCollective]: https://opencollective.com/mastodon
