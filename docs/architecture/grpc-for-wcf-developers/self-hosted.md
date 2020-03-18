---
title: 自託管 gRPC 應用程式 - 適用于 WCF 開發人員的 gRPC
description: 將 ASP.NET核心 gRPC 應用程式部署為自託管服務。
ms.date: 09/02/2019
ms.openlocfilehash: 00fb1453e19a02469f80af79672e0c1f72c7280f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147798"
---
# <a name="self-hosted-grpc-applications"></a>自託管 gRPC 應用程式

儘管 ASP.NET Core 3.0 應用程式可以在 Windows 伺服器上的 IIS 中託管，但當前無法在 IIS 中託管 gRPC 應用程式，因為某些 HTTP/2 功能不受支援。 此功能是將來更新到 Windows 伺服器的目標。

您可以將應用程式作為 Windows 服務運行。 或者，由於 .NET Core 3.0 託管擴展中的新功能，您可以將它作為由[系統控制的](https://en.wikipedia.org/wiki/Systemd)Linux 服務運行。

## <a name="run-your-app-as-a-windows-service"></a>將應用作為 Windows 服務運行

要將ASP.NET核心應用程式佈建為 Windows 服務運行，請安裝來自 NuGet 的[Microsoft.擴展.託管.Windows服務](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices)包。 然後向`UseWindowsService`中`CreateHostBuilder``Program.cs`的方法添加調用。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> 如果應用程式未作為 Windows 服務運行，則`UseWindowsService`該方法不執行任何操作。

現在使用以下方法之一發布應用程式：

* 通過按右鍵專案並在快顯功能表上選擇 **"發佈"，** 從視覺化工作室開始。
* 從 .NET 核心 CLI。

發佈 .NET Core 應用程式時，可以選擇創建*與框架相關的*部署或*自包含*部署。 與框架相關的部署要求在運行它們的主機上安裝 .NET Core 共用運行時。 自包含部署使用 .NET Core 運行時和框架的完整副本發佈，可在任何主機上運行。 有關詳細資訊（包括每種方法的優缺點），請參閱[.NET Core 應用程式部署](../../core/deploying/index.md)文檔。

要發佈不需要在主機上安裝 .NET Core 3.0 運行時的應用程式的自包含生成，請指定要包含在應用程式中的運行時。 使用`-r`（或`--runtime`） 標誌。

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

要發佈與框架相關的生成，省略該`-r`標誌。

```dotnetcli
dotnet publish -c Release -o ./publish
```

將`publish`目錄的完整內容複寫到安裝資料夾。 然後，使用[sc 工具](/windows/desktop/services/controlling-a-service-using-sc)為可執行檔創建 Windows 服務。

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>登錄到 Windows 事件日誌

該方法`UseWindowsService`會自動添加將日誌消息寫入 Windows 事件日誌的[日誌記錄](/aspnet/core/fundamentals/logging/)提供程式。 您可以通過向 的 分區或其他配置源添加`EventLog`條目來配置`Logging`此提供程式`appsettings.json`的日誌記錄。

可以通過在這些設置中設置`SourceName`屬性來覆蓋事件日誌中使用的源名稱。 如果不指定名稱，將使用預設應用程式名稱（通常是可執行程式集名稱）。

有關日誌記錄的詳細資訊，在本章的末尾。

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>使用系統運行應用作為 Linux 服務

要將ASP.NET核心應用程式佈建為以 Linux 服務（或 Linux 術語中的*守護進程*）運行，請安裝[Microsoft.擴展.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd)套裝程式（ NuGet）。 然後向`UseSystemd`中`CreateHostBuilder``Program.cs`的方法添加調用。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> 如果應用程式未作為 Linux 服務運行，則`UseSystemd`該方法不執行任何操作。

現在發佈應用程式。 對於相關的 Linux 運行時（例如，）。`linux-x64`應用程式可以是依賴于框架的，也可以是自包含的。 可以使用以下方法之一進行發佈：

* 通過按右鍵專案並在快顯功能表上選擇 **"發佈"，** 從視覺化工作室開始。
* 從 .NET 核心 CLI，通過使用以下命令：

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
將`publish`目錄的完整內容複寫到 Linux 主機上的安裝資料夾。 註冊服務需要將一個特殊的檔（稱為*單中繼檔*）添加到`/etc/systemd/system`目錄中。 您需要根許可權才能在此資料夾中創建檔。 使用要使用的`systemd`識別碼和副檔名`.service`命名檔。 例如，使用 `/etc/systemd/system/myapp.service`。

服務檔使用 INI 格式，如以下示例所示：

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

該`Type=notify`屬性告訴`systemd`應用程式將在啟動和關閉時通知它。 當`WantedBy=multi-user.target`Linux 系統達到"執行層級 2"時，該設置將導致服務啟動，這意味著非圖形多使用者外殼處於活動狀態。

在`systemd`識別服務之前，它需要重新載入其配置。 您可以使用`systemd`命令`systemctl`進行控制。 重新載入後，`status`使用子命令確認應用程式已成功註冊。

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

如果配置的服務正確，您將獲得以下輸出：

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

使用`start`命令啟動服務。

```console
sudo systemctl start myapp.service
```

> [!TIP]
> 使用`.service``systemctl start`時，擴展是可選的。

要告訴`systemd`在系統啟動時自動啟動服務，請使用 命令`enable`。

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>日誌

與 Windows 事件日誌等效的`journald`Linux 是 ，是 中的`systemd`結構化日誌記錄系統服務。 Linux 守護進程寫入標準輸出的日誌消息將自動寫入`journald`。 要配置日誌記錄級別，`Console`請使用日誌記錄配置的部分。 主機`UseSystemd`產生器方法自動設定主控台輸出格式以適應日誌。

因為它是`journald`Linux 日誌的標準，因此各種工具都集成在一起。 您可以輕鬆地將日誌從`journald`外部日誌記錄系統路由到外部日誌記錄系統。 在主機的本地工作，可以使用 命令`journalctl`查看命令列中的日誌。

```console
sudo journalctl -u myapp
```

> [!TIP]
> 如果您的主機上有可用的 GUI 環境，則一些圖形日誌檢視器可用於 Linux，例如*QJournalctl*和*gnome 日誌*。

要瞭解有關使用`journalctl`從 命令`systemd`行查詢日誌的更多內容，請參閱[man 頁](https://manpages.debian.org/buster/systemd/journalctl.1)。

## <a name="https-certificates-for-self-hosted-applications"></a>用於自託管應用程式的 HTTPS 證書

在生產中運行 gRPC 應用程式時，應使用來自受信任的憑證授權單位 （CA） 的 TLS 證書。 此 CA 可能是公共 CA，也可以是組織的內部 CA。

在 Windows 主機上，可以使用<xref:System.Security.Cryptography.X509Certificates.X509Store>類從安全[憑證存放區載入](/windows/win32/seccrypto/managing-certificates-with-certificate-stores)證書。 您還可以在某些 Linux`X509Store`主機上將該類與 OpenSSL 金鑰存儲一起使用。

還可以通過使用[X509 證書2建構函式](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)之一從以下任一創建證書：

* 檔，`.pfx`如受強式密碼保護的檔
* 從安全存儲服務（如[Azure 金鑰保存庫](https://azure.microsoft.com/services/key-vault/)）檢索的二進位資料

您可以將 Kestrel 配置為以兩種方式使用證書：從配置或代碼中。

### <a name="set-https-certificates-by-using-configuration"></a>使用配置設置 HTTPS 證書

配置方法要求在 Kestrel 配置部分`.pfx`中設置證書檔和密碼的路徑。 在`appsettings.json`中，如下所示：

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

通過使用安全配置源（如 Azure 金鑰保存庫或 Hashicorp 保存庫）提供密碼。

> [!IMPORTANT]
> 不要在設定檔中存儲未加密的密碼。

### <a name="set-https-certificates-in-code"></a>在代碼中設置 HTTPS 證書

要在代碼中配置 Kestrel 上的`ConfigureKestrel`HTTPS，`IWebHostBuilder`請使用`Program`類 中 的方法。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

同樣，請確保將`.pfx`檔的密碼存儲在安全配置源中並從中檢索。

>[!div class="step-by-step"]
>[上一個](grpc-in-production.md)
>[下一個](docker.md)
