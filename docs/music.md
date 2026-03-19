# 🎵 Music

24/7 music streaming powered by yt-dlp. The bot joins your voice channel on the first `/play` and stays until restarted or stopped with `/stop`.

***

## Playback

| Command | Description |
| ------- | ----------- |
| `/play <query>` | Play a song or playlist — accepts a song name, YouTube video URL, or YouTube playlist URL |
| `/pause` | Pause the current song |
| `/resume` | Resume a paused song |
| `/skip [amount]` | Skip the current song, or skip multiple songs at once |
| `/stop` | Stop playback and clear the queue (bot stays in the voice channel) |
| `/nowplaying` | Show what is currently playing with duration, loop mode, and volume |

***

## Queue

| Command | Description |
| ------- | ----------- |
| `/queue [page]` | Show the current song queue (paginated, 10 songs per page) |
| `/remove <position>` | Remove a song from the queue by its position number |
| `/shuffle` | Randomly shuffle all songs in the queue |
| `/clear` | Clear all queued songs (keeps the current song playing) |

***

## Playback Settings

| Command | Description |
| ------- | ----------- |
| `/loop <mode>` | Set loop mode — `off`, `track` (repeat current song), or `queue` (repeat entire queue) |
| `/volume <1–100>` | Set the playback volume |
| `/seek <time>` | Jump to a specific position in the current song (e.g. `1:30` or `90`) |

***

## Notes

- The bot joins when someone uses `/play` and stays in the voice channel until `/stop` is used or the bot restarts
- Supports YouTube video URLs, YouTube playlist URLs, and search queries
- YouTube playlists are capped at 50 tracks when loaded via the yt-dlp fallback
- Audio streams at the best available quality (`bestaudio/best`)
