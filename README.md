# csv2sql
 
**csv2sql** is a Ruby script for importing CSV files into SQLite.

See [**csv2sql.org**](http://csv2sql.org/) for more information.

## Usage

**csv2sql** *[options]*

| Option                      | Description
------------------------------|-----------------------------
| -d, --database DATABASE     | Database to import into. Default is "csv2sql.db"
| -e, --encoding INPUT:OUTPUT | Input and output encoding. Default is "UTF-8:UTF-8"
| -f, --file FILENAME         | CSV file to import. You can alternately pipe CSV data into standard input
| -h, --help                  | Print this help message
| -t, --table TABLE           | Table to import into. Default is the name of the file being imported from or "stdin" if CSV data is from standard input. Periods in the filename are replaced with underscores
| -v, --verbose               | Print verbose output
| -V, --version               | Print version number

The destination table and database will automatically be created if they do not already exist.

If the destination table already exists, then **csv2sql** assumes that it contains the same number of columns as the input data. The column names do not need to match.

## Examples

1. Import widgets.csv into the default table (widgets\_csv) and database (csv2sql.db):

        csv2sql -f widgets.csv

2. Import standard input into the "foo" table within the "bar.db" database:

        cat widgets.csv | csv2sql -t foo -d bar.db

3. Import products.csv and more-products.csv into the "products" table within the default database (csv2sql.db):

        csv2sql -f products.csv -t products
        csv2sql -f more-products.csv -t products

4. Export data from SQLite sorted by the "ProductName" column to output.csv:

        sqlite3 -header -csv csv2sql.db "SELECT * FROM products ORDER BY ProductName" > output.csv

## Installation

1. Verify that you have [**Ruby**](https://www.ruby-lang.org/) 1.9.3 (released October 2011) or later installed:

        ruby --version

    Earlier versions may also work, but are untested.

2. Verify that you have [**SQlite**](https://sqlite.org/) 3.6.16 or later installed:

        sqlite3 -version

3. Verify that you have the [**sqlite3**](https://github.com/sparklemotion/sqlite3-ruby) Ruby module installed. For example, if you're using [RubyGems](https://rubygems.org/):

        gem list sqlite3

4. Download and extract the tarball:

        wget https://github.com/mrideout/csv2sql/archive/v0.1.tar.gz
        tar -xzf v0.1.tar.gz
        cd csv2sql-0.1

5. Make **csv2sql** executable:

        chmod 755 csv2sql

6. Optionally, move **csv2sql** into a directory that's in your PATH. For example:

        sudo mv csv2sql /usr/local/bin/
 
## Contributing
 
1. Fork it!

2. Create your feature branch:

        git checkout -b my-new-feature

3. Commit your changes:

        git commit -a -m 'Add some feature'

4. Push to the branch:

        git push origin my-new-feature

5. Submit a pull request.
 
## History

[Matt Rideout](https://www.mattrideout.com/) wrote and released **csv2sql** in March 2015. 
 
## License
 
**csv2sql** is open source software released under the [MIT License](http://www.opensource.org/licenses/MIT).

