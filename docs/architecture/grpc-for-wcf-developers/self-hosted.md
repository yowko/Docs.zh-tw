---
title: 自我裝載的 gRPC 應用程式-適用于 WCF 開發人員的 gRPC
description: 將 ASP.NET Core gRPC 應用程式部署為自我裝載的服務。
ms.date: 09/02/2019
ms.openlocfilehash: 2244f161ad4b5d60138ae0f7b4d6a9c8c8829aa8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503396"
---
# <a name="self-hosted-grpc-applications"></a>自我裝載的 gRPC 應用程式

雖然 ASP.NET Core 3.0 應用程式可以裝載在 Windows Server 上的 IIS 中，但目前無法在 IIS 中裝載 gRPC 應用程式，因為某些 HTTP/2 功能不受支援。 此功能是 Windows Server 未來更新的目標。

您可以將應用程式當做 Windows 服務來執行。 或者，您可以透過[systemd](https://en.wikipedia.org/wiki/Systemd)所控制的 Linux 服務來執行它，因為 .net Core 3.0 裝載延伸模組的新功能。

## <a name="run-your-app-as-a-windows-service"></a>以 Windows 服務的形式執行您的應用程式

若要將您的 ASP.NET Core 應用程式設定為以 Windows 服務的身分執行，請從 NuGet 安裝[WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices)套件。 然後將 `UseWindowsService` 的呼叫新增至 `Program.cs`中的 `CreateHostBuilder` 方法。

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
> 如果應用程式不是以 Windows 服務的形式執行，`UseWindowsService` 方法就不會進行任何動作。

現在，請使用下列其中一種方法來發佈您的應用程式：

* 在 Visual Studio 中，以滑鼠右鍵按一下專案，然後選取快捷方式功能表上的 [**發佈**]。
* 從 .NET Core CLI。

當您發行 .NET Core 應用程式時，您可以選擇建立與*framework 相依*的部署或*獨立*的部署。 架構相依部署需要在執行的主機上安裝 .NET Core 共用執行時間。 獨立式部署是透過 .NET Core 執行時間和架構的完整複本發佈，而且可以在任何主機上執行。 如需詳細資訊，包括每種方法的優缺點，請參閱[.Net Core 應用程式部署](../../core/deploying/index.md)檔。

若要發行不需要在主機上安裝 .NET Core 3.0 執行時間之應用程式的獨立組建，請指定要包含在應用程式中的執行時間。 使用 `-r` （或 `--runtime`）旗標。

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

若要發行與 framework 相依的組建，請省略 `-r` 旗標。

```dotnetcli
dotnet publish -c Release -o ./publish
```

將 `publish` 目錄的完整內容複寫到安裝資料夾。 然後，使用[sc 工具](/windows/desktop/services/controlling-a-service-using-sc)來建立可執行檔的 Windows 服務。

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>記錄到 Windows 事件記錄檔

`UseWindowsService` 方法會自動新增[記錄](/aspnet/core/fundamentals/logging/)提供者，將記錄訊息寫入 Windows 事件記錄檔。 您可以藉由將 `EventLog` 專案新增至 `appsettings.json` 或其他設定來源的 `Logging` 區段，來設定此提供者的記錄。 

您可以藉由在這些設定中設定 `SourceName` 屬性，來覆寫事件記錄檔中使用的來源名稱。 如果您未指定名稱，則會使用預設的應用程式名稱（通常是可執行檔元件名稱）。

如需有關記錄的詳細資訊，請到本章的結尾。

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>以 systemd 的 Linux 服務身分執行您的應用程式

若要將您的 ASP.NET Core 應用程式設定為以 Linux 服務（或 Linux 用語中中的*daemon* ）執行，請從 NuGet 安裝[Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd)套件。 然後將 `UseSystemd` 的呼叫新增至 `Program.cs`中的 `CreateHostBuilder` 方法。

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
> 如果應用程式不是以 Linux 服務的身分執行，`UseSystemd` 方法就不會進行任何動作。

現在發佈您的應用程式。 應用程式可以是架構相依或獨立的相關 Linux 執行時間（例如 `linux-x64`）。 您可以使用下列其中一種方法來發行：

* 在 Visual Studio 中，以滑鼠右鍵按一下專案，然後選取快捷方式功能表上的 [**發佈**]。 
* 從 .NET Core CLI，使用下列命令：

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
將 `publish` 目錄的完整內容複寫到 Linux 主機上的安裝資料夾。 註冊服務需要一個特殊的檔案（稱為*單位*檔案），才能新增至 `/etc/systemd/system` 目錄。 您需要根許可權，才能在此資料夾中建立檔案。 以您想要 `systemd` 使用的識別碼和 `.service` 延伸模組來命名檔案。 例如，使用 `/etc/systemd/system/myapp.service`。

服務檔會使用 INI 格式，如下列範例所示：

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

`Type=notify` 屬性會告訴 `systemd` 應用程式會在啟動和關閉時通知它。 當 Linux 系統到達 "runlevel 2" 時，`WantedBy=multi-user.target` 設定會使服務啟動，這表示非圖形化的多使用者 shell 正在作用中。

在 `systemd` 可以辨識服務之前，它必須重載其設定。 您可以使用 `systemctl` 命令來控制 `systemd`。 重載之後，請使用 `status` 子命令來確認應用程式已成功註冊。

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

如果您已正確設定服務，您會得到下列輸出：

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

使用 `start` 命令來啟動服務。

```console
sudo systemctl start myapp.service
```

> [!TIP]
> 當您使用 `systemctl start`時，`.service` 延伸模組是選擇性的。

若要告知 `systemd` 在系統啟動時自動啟動服務，請使用 `enable` 命令。

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>記錄至 journald

Windows 事件記錄檔的 Linux 對等專案是 `journald`，這是屬於 `systemd`的結構化記錄系統服務。 Linux daemon 寫入標準輸出的記錄訊息會自動寫入 `journald`。 若要設定記錄層級，請使用記錄設定的 [`Console`] 區段。 `UseSystemd` 主機產生器方法會自動設定主控台輸出格式，以符合日誌。

因為 `journald` 是 Linux 記錄檔的標準，所以有各種不同的工具可與其整合。 您可以輕鬆地將記錄從 `journald` 路由傳送至外部記錄系統。 在主機本機上工作，您可以使用 `journalctl` 命令，從命令列中查看記錄。

```console
sudo journalctl -u myapp
```

> [!TIP]
> 如果您的主機上有可用的 GUI 環境，則有幾個圖形化記錄檢視器可供 Linux 使用，例如*QJournalctl*和*gnome 記錄*。

若要深入瞭解如何使用 `journalctl`從命令列查詢 `systemd` 日誌，請參閱[man 頁面](https://manpages.debian.org/buster/systemd/journalctl.1)。

## <a name="https-certificates-for-self-hosted-applications"></a>自我裝載應用程式的 HTTPS 憑證

當您在生產環境中執行 gRPC 應用程式時，您應該使用來自受信任憑證授權單位單位（CA）的 TLS 憑證。 此 CA 可能是公用 CA，或是貴組織的內部帳戶。

在 Windows 主機上，您可以使用 <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別，從安全的[憑證存放區](/windows/win32/seccrypto/managing-certificates-with-certificate-stores)載入憑證。 您也可以使用 `X509Store` 類別，搭配某些 Linux 主機上的 OpenSSL 金鑰存放區。

您也可以使用其中一個[X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)的函式來建立憑證，從下列其中一個：

* 檔案，例如受到強式密碼保護的 `.pfx` 檔案
* 從安全儲存體服務（例如[Azure Key Vault](https://azure.microsoft.com/services/key-vault/) ）取出的二進位資料

您可以透過兩種方式設定 Kestrel 以使用憑證：從設定或在程式碼中。

### <a name="set-https-certificates-by-using-configuration"></a>使用 configuration 設定 HTTPS 憑證

設定方法需要將憑證 `.pfx` 檔案的路徑，以及在 [Kestrel 設定] 區段中的密碼。 在 `appsettings.json`中，如下所示：

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

使用安全設定來源（例如 Azure Key Vault 或 Hashicorp 保存庫）來提供密碼。

> [!IMPORTANT]
> 請勿將未加密的密碼儲存在設定檔中。

### <a name="set-https-certificates-in-code"></a>在程式碼中設定 HTTPS 憑證

若要在程式碼的 Kestrel 上設定 HTTPS，請在 `Program` 類別的 `IWebHostBuilder` 上使用 `ConfigureKestrel` 方法。

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

同樣地，請務必將 `.pfx` 檔案的密碼儲存在中，並從安全的設定來源加以取出。

>[!div class="step-by-step"]
>[上一頁](grpc-in-production.md)
>[下一頁](docker.md)
