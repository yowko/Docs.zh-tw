---
title: 自我裝載的 gRPC 應用程式-適用于 WCF 開發人員的 gRPC
description: 將 ASP.NET Core gRPC 應用程式部署為自我裝載的服務。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1269137b58f4d25f407a6a04327c51bc9f069c1b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184103"
---
# <a name="self-hosted-grpc-applications"></a>自我裝載的 gRPC 應用程式

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雖然 ASP.NET Core 3.0 應用程式可以裝載在 Windows Server 上的 IIS 中，但目前無法在 IIS 中託管 gRPC 應用程式，因為尚未支援某些 HTTP/2 功能。 在未來的 Windows Server 更新中，預期會有這項功能。

由於 .NET Core 3.0 裝載延伸模組的一些新功能，您可以將應用程式當做 Windows 服務或由[systemd](https://en.wikipedia.org/wiki/Systemd)控制的 Linux 服務來執行。

## <a name="run-your-app-as-a-windows-service"></a>以 Windows 服務的形式執行您的應用程式

若要將您的 ASP.NET Core 應用程式設定為以 Windows 服務的身分執行，請從 NuGet 安裝[WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices)套件。 然後，將對的`UseWindowsService`呼叫加入`CreateHostBuilder`至中`Program.cs`的方法。

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
> 如果應用程式不是以 Windows 服務的形式執行`UseWindowsService` ，方法就不會進行任何動作。

現在從 Visual Studio 發行應用程式，方法是以滑鼠右鍵按一下專案，然後從操作功能表中選擇 [*發佈*]，或從 [.NET Core CLI]。

當您發行 .NET Core 應用程式時，您可以選擇建立與*framework 相依*的部署或*獨立*的部署。 架構相依部署需要在執行的主機上安裝 .NET Core 共用執行時間。 獨立式部署是透過 .NET Core 執行時間和架構的完整複本發佈，而且可以在任何主機上執行。 如需詳細資訊，包括每種方法的優缺點，請參閱[.Net Core 應用程式部署](https://docs.microsoft.com/dotnet/core/deploying/)檔。

若要發行不需要在主機上安裝 .net Core 3.0 執行時間之應用程式的獨立組建，請使用`-r` （或`--runtime`）旗標來指定要包含在應用程式中的執行時間。

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

若要發行與 framework 相依的組建，請`-r`省略旗標。

```console
dotnet publish -c Release -o ./publish
```

將`publish`目錄的完整內容複寫到安裝資料夾，並使用[sc 公用程式](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc)來建立可執行檔的 Windows 服務。

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a>記錄到 Windows 事件記錄檔

方法會自動新增[記錄](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0)提供者，將記錄訊息寫入 Windows 事件記錄檔。`UseWindowsService` 您可以藉由將`EventLog`專案新增`Logging`至`appsettings.json`或其他設定來源的區段，來設定此提供者的記錄。 事件記錄檔中使用的來源名稱可以藉由在這些`SourceName`設定中設定屬性來覆寫; 如果您未指定名稱，則會使用預設的應用程式名稱（通常是可執行檔元件名稱）。

如需有關記錄的詳細資訊，請到本章的結尾。

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>以 systemd 的 Linux 服務身分執行您的應用程式

若要將您的 ASP.NET Core 應用程式設定為以 Linux 服務（或 Linux 用語中中的*daemon* ）執行，請從 NuGet 安裝[Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd)套件。 然後，將對的`UseSystemd`呼叫加入`CreateHostBuilder`至中`Program.cs`的方法。

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
> 如果應用程式不是以 Linux 服務的身分執行`UseSystemd` ，方法就不會進行任何動作。

現在，從 Visual Studio，以滑鼠右鍵按一下專案，然後從操作功能表中選擇 [*發佈*]，或`linux-x64`從 .net，發佈您的應用程式（與 framework 相依，或獨立的 Linux 執行時間，例如）：使用下列命令的核心 CLI。

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

將`publish`目錄的完整內容複寫到 Linux 主機上的安裝資料夾。 註冊服務需要一個稱為「單位檔案」的特殊檔案，才能新增至`/etc/systemd/system`目錄。 您需要根許可權，才能在此資料夾中建立檔案。 以您想`systemd`要使用的識別碼`.service`和副檔名來命名檔案。 例如，`/etc/systemd/system/myapp.service`。

服務檔會使用 INI 格式，如下列範例所示。

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

屬性會告知`systemd`應用程式會在啟動和關閉時通知它。 `Type=notify` 此`WantedBy=multi-user.target`設定會在 Linux 系統到達 "runlevel 2" 時啟動服務，這表示非圖形化的多使用者 shell 正在作用中。

在`systemd`辨識服務之前，必須先重載其設定。 您可以`systemd` `systemctl`使用命令來控制。 重載之後，使用`status`子命令確認應用程式已成功註冊。

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

如果您已正確設定服務，則會顯示下列輸出：

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

`start`使用命令來啟動服務。

```console
sudo systemctl start myapp.service
```

> [!TIP]
> `.service` 使用`systemctl start`時，延伸模組是選擇性的。

若要`systemd`指示在系統啟動時自動啟動服務，請`enable`使用命令。

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>記錄至 journald

Windows 事件記錄檔的 Linux 對等專案`journald`是，屬於的`systemd`結構化記錄系統服務。 Linux daemon 寫入標準輸出的記錄訊息會自動寫入`journald`，因此若要設定記錄層級，請`Console`使用記錄設定的區段。 `UseSystemd`主機產生器方法會自動設定主控台輸出格式，以符合日誌。

因為`journald`是 Linux 記錄檔的標準，所以有各種與它整合的工具，而且您可以輕鬆地將記錄從`journald`路由傳送至外部記錄系統。 在主機本機上工作，您可以使用`journalctl`命令，從命令列中查看記錄。

```console
sudo journalctl -u myapp
```

> [!TIP]
> 如果您的主機上有可用的 GUI 環境，則有幾個圖形化記錄檢視器可供 Linux 使用，例如*QJournalctl*和*gnome 記錄*。

若要深入瞭解如何從命令列使用`journalctl`查詢 systemd 日誌，請參閱[man 頁面](https://manpages.debian.org/buster/systemd/journalctl.1)。

## <a name="https-certificates-for-self-hosted-applications"></a>自我裝載應用程式的 HTTPS 憑證

在生產環境中執行 gRPC 應用程式時，您應該使用來自受信任憑證授權單位單位（CA）的 TLS 憑證。 此 CA 可以是公用 CA，也可以是您組織的內部帳戶。

在 Windows 主機上，您可以使用[system.security.cryptography.x509certificates.x509store 類別](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0)，從安全的[憑證存放區](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores)載入憑證。 `X509Store`類別也可以與某些 Linux 主機上的 OpenSSL 金鑰存放區搭配使用。

您也可以使用其中一個[X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0)的處理常式來建立憑證，不論是從檔案（例如`.pfx`，受強式密碼保護的檔案），或是從從安全儲存體服務（例如 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)）取得的二進位資料。

Kestrel 可設定為使用憑證的方式有兩種：從設定，或在程式碼中。

### <a name="set-https-certificates-using-configuration"></a>使用 configuration 設定 HTTPS 憑證

設定方法需要將憑證`.pfx`檔案的路徑和 Kestrel 設定區段中的密碼。 在`appsettings.json`中看起來像這樣。

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

您應該使用 Azure KeyVault 或 Hashicorp Vault 之類的安全設定來源來提供密碼。

您不應該將未加密的密碼儲存在設定檔中。

### <a name="set-https-certificates-in-code"></a>在程式碼中設定 HTTPS 憑證

若要在程式碼的 Kestrel 上設定 HTTPS `ConfigureKestrel` ，請`IWebHostBuilder`在`Program`類別中的上使用方法。

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

同樣地，檔案的密碼`.pfx`應該儲存在安全的設定來源並從中取出。

>[!div class="step-by-step"]
>[上一頁](grpc-in-production.md)
>[下一頁](docker.md)
