# Local Video Uploader

## Overview

Local Video Uploader is a macOS desktop application for uploading local videos to the authenticated user's YouTube channel.

The app combines a native SwiftUI desktop UI with a Python CLI backend. It is designed for personal use and all uploads, metadata changes, and deletions are initiated explicitly by the user.

## Main Features

- Google OAuth sign-in for YouTube Data API access
- Batch upload from local files and Photo Library derived files
- Shared metadata templates for `Location`, `Event`, `Participants`, `Playlist`, and `Camera`
- Metadata history with persistent manual additions
- History item deletion from the metadata picker UI
- Recent upload history screen
- History calendar with upload and deletion tracking
- Local configuration through `config.json`
- Local-only storage for tokens, upload history, and app support data

## Metadata History

The Shared Metadata section keeps reusable history for these fields:

- `Location`
- `Event`
- `Participants`
- `Playlist`
- `Camera`

History behavior:

- Manual input is saved when the field edit is committed.
- Existing values are backfilled from `upload_history.db`.
- History is shown in descending recency order.
- Items can be removed from the history popover.
- Removed items are suppressed even if they still exist in past upload history.

Related local files in the support directory:

- `./.iphoto2youtube/metadata_history.json`
- `./.iphoto2youtube/upload_history.db`
- `./.iphoto2youtube/history_calendar.db`
- `./.iphoto2youtube/ledger.csv`

## Configuration

The app reads user settings from `config.json` in the support directory.

Default path:

- `./.iphoto2youtube/config.json`

Key related files:

- `src/iphoto2youtube_cli/config.py`
- `config.example.json`
- `./.iphoto2youtube/config.json`

Example:

```json
{
  "youtube_api_daily_quota_limit": 50000
}
```

If `youtube_api_daily_quota_limit` is omitted, the built-in default from `src/iphoto2youtube_cli/config.py` is used.

## Documents

- [仕様書](%E4%BB%95%E6%A7%98%E6%9B%B8.md)
- [技術説明書](%E6%8A%80%E8%A1%93%E8%AA%AC%E6%98%8E%E6%9B%B8.md)
- [API Documentation](iPhoto2YouTube_API_Documentation.md)
- [Privacy Policy](Privacy%20Policy.md)
- [Terms of Service](Terms%20of%20Service.md)

## YouTube API Use

The application uses YouTube Data API for:

- Uploading videos
- Setting titles, descriptions, tags, visibility, and playlists
- Reading the authenticated channel and quota-related state needed for the UI

The application does not access data belonging to other users, and it does not perform background automation or unattended uploads.

## License

This project is licensed under the MIT License. See `LICENSE` for details.

## Author

Copyright (c) 2026 HiroPublic

This project was developed with assistance from generative AI.
