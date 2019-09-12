# mozvr-blog

## Development

1. Export the JSON file containing the blog settings and data by clicking the **`Export`** button on the [`Settings > Lab` page](https://mozvr.ghost.io/ghost/settings/labs/)
2. Run these commands locally from your command-line prompt:
    ```sh
    # Create a directory for the blog.
    mkdir -p ghost-blog
    cd ghost-blog

    # Locally install the latest version of Ghost.
    npm install -g ghost-cli@latest
    ghost install local

    # Stop the Ghosts server.
    ghost stop

    git clone git@github.com:slightlyoffbeat/mixed-reality-blog.git content/themes/mixed-reality-blog

    cd content/data

    sqlite3 ghost-local.db
    # When the SQLite database prompt appears, enter these commands:
    #
    #     select * from settings where key = 'active_theme';
    #
    #     update settings set value = 'mixed-reality-blog' where key = 'active_theme';
    #
    
    # Run the local server (watching changes to the theme).
    nodemon current/index.js --watch content/themes/mixed-reality-blog --ext hbs,js,css
    ```
