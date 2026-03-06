# x-twitter

33-command Claude Code skill for X/Twitter. Post, search, engage, moderate, discover communities — all from your terminal.

## Installation

### Via Claude Code marketplace (recommended)

```bash
/plugin install x-twitter
```

### Manual installation

```bash
# 1. Clone the repo
git clone https://github.com/alberduris/claude-code-marketplace
cd claude-code-marketplace/plugins/x-twitter

# 2. Install dependencies
npm install

# 3. Build
npm run build

# 4. Add credentials (see Credentials section below)
cp .env.example .env.local
# then fill in your keys in .env.local
```

## Credentials

Go to [developer.x.com](https://developer.x.com) > Apps > create or select an app > Keys and tokens.

Required — set in `.env.local` or `.env` in your project root (or the plugin directory):

```
X_API_KEY=your_api_key
X_API_SECRET=your_api_secret
X_ACCESS_TOKEN=your_access_token
X_ACCESS_TOKEN_SECRET=your_access_token_secret
```

Enable **OAuth 1.0a with Read and Write** permissions on the app to use write commands.

Optional — needed for `search --all` (full archive back to 2006):

```
X_API_BEARER_TOKEN=your_bearer_token
```

## Usage

Once installed, invoke the skill in three ways:

- **Slash command:** `/x-twitter <command> [flags]`
- **Natural language:** Claude auto-detects X/Twitter intent and invokes the skill
- **Direct:** `node plugins/x-twitter/dist/x.js <command> [flags]`

Write commands (`post`, `delete`, `like`, `unlike`, `repost`, `unrepost`, `follow`, `unfollow`, `bookmark`, `unbookmark`, `mute`, `unmute`, `hide-reply`) will always ask for confirmation before executing.

## Commands

### Core
| Command | Description |
|---------|-------------|
| `me` | Your account data (profile, metrics, verification) |
| `search` | Search posts by query (recent or full archive) |
| `get` | Retrieve post(s) by ID |
| `post` | Create a tweet, reply, or quote tweet |
| `delete` | Delete a post |

### Engagement
| Command | Description |
|---------|-------------|
| `like` | Like a post |
| `unlike` | Remove a like |
| `repost` | Repost (retweet) a post |
| `unrepost` | Remove a repost |

### Social
| Command | Description |
|---------|-------------|
| `user` | Look up user(s) by username or ID |
| `follow` | Follow a user |
| `unfollow` | Unfollow a user |
| `followers` | List a user's followers |
| `following` | List accounts a user follows |

### Feed
| Command | Description |
|---------|-------------|
| `timeline` | Your home timeline (reverse chronological) |
| `mentions` | Posts that mention you |

> **Note (2026-02-14):** The X API returns heavily skewed timeline results — mostly own tweets. Use `--exclude replies,retweets` to improve signal.

### Bookmarks
| Command | Description |
|---------|-------------|
| `bookmark` | Bookmark a post |
| `unbookmark` | Remove a bookmark |
| `bookmarks` | List your bookmarks |

### Moderation
| Command | Description |
|---------|-------------|
| `mute` | Mute a user |
| `unmute` | Unmute a user |
| `muted` | List muted accounts |
| `blocked` | List blocked accounts |
| `hide-reply` | Hide a reply to your post |

### Analytics
| Command | Description |
|---------|-------------|
| `likers` | Users who liked a post |
| `reposters` | Users who reposted a post |
| `quotes` | Quote tweets of a post |
| `count` | Count posts matching a query over time |
| `reposts-of-me` | Reposts of your posts by others |

### Discovery
| Command | Description |
|---------|-------------|
| `search-users` | Search users by query |
| `trending` | Trending topics (worldwide or personalized) |

### Communities
| Command | Description |
|---------|-------------|
| `search-communities` | Search communities by keyword |
| `community` | Look up a community by ID |

## Requirements

- Node.js 18+
- X Developer account with OAuth 1.0a credentials
- (Optional) Bearer Token for full archive search

## License

MIT
