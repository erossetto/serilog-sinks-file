# Serilog.Sinks.File [![Build status](https://ci.appveyor.com/api/projects/status/hh9gymy0n6tne46j?svg=true)](https://ci.appveyor.com/project/serilog/serilog-sinks-file) [![NuGet Version](http://img.shields.io/nuget/v/Serilog.Sinks.File.svg?style=flat)](https://www.nuget.org/packages/Serilog.Sinks.File/) [![Documentation](https://img.shields.io/badge/docs-wiki-yellow.svg)](https://github.com/serilog/serilog/wiki) [![Join the chat at https://gitter.im/serilog/serilog](https://img.shields.io/gitter/room/serilog/serilog.svg)](https://gitter.im/serilog/serilog)

Writes [Serilog](https://serilog.net) events to a text file.

```csharp
var log = new LoggerConfiguration()
    .WriteTo.File("log.txt")
    .CreateLogger();
```

To avoid bringing down apps with runaway disk usage the file sink **limits file size to 1GB by default**. The limit can be increased or removed using the `fileSizeLimitBytes` parameter.

```csharp
    .WriteTo.File("log.txt", fileSizeLimitBytes: null)
```

> **Important:** Only one process may write to a log file at a given time. For multi-process scenarios, either use separate files or one of the non-file-based sinks.

### `<appSettings>` configuration

The sink can be configured in XML [app-settings format](https://github.com/serilog/serilog/wiki/AppSettings) if the _Serilog.Settings.AppSettings_ package is in use:

```xml
<add key="serilog:write-to:File.path" value="log.txt" />
<add key="serilog:write-to:File.fileSizeLimitBytes" value="" />
```

### JSON formatting

To emit JSON, rather than plain text, a formatter can be specified:

```csharp
    .WriteTo.File(new JsonFormatter(), "log.txt")
```

To configure an alternative formatter in XML `<appSettings>`, specify the formatter's assembly-qualified type name as the setting `value`.

_Copyright &copy; 2016 Serilog Contributors - Provided under the [Apache License, Version 2.0](http://apache.org/licenses/LICENSE-2.0.html)._
