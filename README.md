# lnav-formats

Custom file formats for the [lnav] log viewer.

[lnav]: https://lnav.org

## Installation

```bash
git clone https://github.com/hg/lnav-formats ~/.config/lnav/formats/remote
```

## `aspnet_serilog.json`

- ASP.NET web application
- using the [Serilog][serilog] logging library
- logging to JSON [through][compact] `CompactJsonFormatter`

Setup:

```cs
  public static void Main(string[] args) {
    Host
      // ...
      .UseSerilog((context, services, conf) => {
        conf
          .Enrich.FromLogContext()
          .ReadFrom.Services(services)
          .WriteTo.File(
            formatter: new CompactJsonFormatter(),
            path: "log.json",
            // ...
          );
      })
      // ...
  }
```

[serilog]: https://github.com/serilog/serilog
[compact]: https://github.com/serilog/serilog-formatting-compact
