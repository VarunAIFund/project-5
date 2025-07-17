# Spotify MCP Server

A Model Context Protocol (MCP) JSON-RPC server that exposes Spotify's Web API as callable tools for AI assistants.

## Features

- **search_tracks**: Search Spotify's catalog for tracks
- **get_artist_info**: Get detailed artist information and top tracks  
- **get_track_features**: Get audio analysis features for a track

## Setup

1. Install dependencies:
```bash
npm install
```

2. Copy the environment template and add your Spotify credentials:
```bash
cp .env.example .env
```

Then edit `.env` with your actual credentials:
```
SPOTIFY_CLIENT_ID=your_client_id_here
SPOTIFY_CLIENT_SECRET=your_client_secret_here
```

3. Run the server:
```bash
npm start
```

## Testing

Run the test suite:
```bash
node test-server.js
```

## Usage

The server implements the MCP protocol and communicates via JSON-RPC over stdin/stdout. All tools handle rate limiting (100 requests/minute) and include proper error handling.

### Tools

#### search_tracks
- **Parameters**: `query` (string), `limit` (integer, optional, default: 10)
- **Returns**: Array of track objects with name, artist, album, popularity, preview_url, spotify_url

#### get_artist_info  
- **Parameters**: `artist_id` (string)
- **Returns**: Object with name, genres, popularity, follower_count, top_tracks

#### get_track_features
- **Parameters**: `track_id` (string)  
- **Returns**: Object with danceability, energy, valence, tempo, loudness

## Note

The `get_track_features` tool requires additional permissions that may not be available with client credentials flow. For full functionality, consider implementing user authorization flow.# project-5
# project-5
