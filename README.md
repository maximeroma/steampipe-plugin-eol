![](https://git.sk5.io/skale-5/run/steampipe/steampipe-plugin-eol/-/raw/main/docs/usage.gif)

# endoflife.date Plugin for Steampipe

Use SQL to query EOL dates for major softwares and middlewares. 

## Quick start

Recommended: use `mise` to install the project Go version.

Install `mise`, then from the project root:

```shell
mise use go@1.24
go version
```

A `mise.toml` file is provided in this repository:

```toml
[tools]
go = "1.24"
```

Install the plugin locally:

```shell
git clone git@git.sk5.io:skale-5/run/steampipe/steampipe-plugin-eol.git
cd steampipe-plugin-eol/
mise install
mkdir -p ~/.steampipe/plugins/local/steampipe-plugin-eol
mise exec go -- go build -ldflags='-linkmode=external' -o ~/.steampipe/plugins/local/steampipe-plugin-eol/steampipe-plugin-eol.plugin
cp config/* ~/.steampipe/config
steampipe service restart
```

Run a query:

```sql
select
    cycle,
    eol,
    days_to_eol
from
    eol_redis;
```

## Engines

This plugin is available for the following engines:

| Engine        | Description
|---------------|------------------------------------------
| [Steampipe](https://steampipe.io/docs) | The Steampipe CLI exposes APIs and services as a high-performance relational database, giving you the ability to write SQL-based queries to explore dynamic data. Mods extend Steampipe's capabilities with dashboards, reports, and controls built with simple HCL. The Steampipe CLI is a turnkey solution that includes its own Postgres database, plugin management, and mod support.

Try it!

```
steampipe query
> .inspect eol
```

Further reading:

- [Writing plugins](https://steampipe.io/docs/develop/writing-plugins)
