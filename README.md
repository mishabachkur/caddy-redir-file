# caddy-redir-file

Add Caddy plugin to load redirects from a CSV file

- Implemented a new Caddy middleware plugin that loads URL redirects from a specified CSV file.
- The plugin supports:
    - **`path`**: The path to the CSV file containing redirects.
    - **`type`**: The file type, which must be "csv".
    - **`csv_separator`** (optional): Custom CSV separator (default is comma).
    - **`preserve_query`** (optional): Option to keep query parameters during redirection.
- Added error handling for file reading and CSV parsing.
- Updated the Caddyfile syntax to configure the new plugin.
- Enhanced logging to track the number of redirects loaded from the CSV file.

## Installation

Build caddy with `xcaddy`:

```bash
xcaddy build --with github.com/mishabachkur/caddy-redir-file
```

## Configuration

#### Caddyfile
```
{
    order redir_file first
}

www.domain.com {
    redir_file {
        path "/path/to/redirects.csv"
        type "csv"
        csv_separator ";"
        preserve_query true
    }
}
```

#### /path/to/redirects.csv
```
from;to
/from-here;/to-here
/and-here;/to-here
```

## Development

## License

MIT