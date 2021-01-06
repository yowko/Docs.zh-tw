---
title: 自我裝載的 gRPC 應用程式-適用于 WCF 開發人員的 gRPC
description: 將 ASP.NET Core gRPC 應用程式部署為自我裝載服務。
ms.date: 12/15/2020
ms.openlocfilehash: a5e2316b8d76593f4eb53760d2609b5bbbc9d2c5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938529"
---
# <a name="self-hosted-grpc-applications"></a>自我裝載的 gRPC 應用程式

雖然 ASP.NET Core 5.0 應用程式可裝載于 Windows Server 上的 IIS 中，但目前無法在 IIS 中裝載 gRPC 應用程式，因為某些 HTTP/2 功能不受支援。 這項功能是 Windows Server 未來更新的目標。

您可以將應用程式當作 Windows 服務來執行。 或者，您也可以將它當作 [systemd](https://en.wikipedia.org/wiki/Systemd)所控制的 Linux 服務來執行，因為 .net 5.0 裝載延伸模組的新功能。

## <a name="run-your-app-as-a-windows-service"></a>以 Windows 服務的形式執行您的應用程式

若要將您的 ASP.NET Core 應用程式設定為以 Windows 服務形式執行，請從 NuGet 安裝 [WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) 套件。 然後，將呼叫新增至 `UseWindowsService` `CreateHostBuilder` 中的方法 `Program.cs` 。

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
> 如果應用程式不是以 Windows 服務的方式執行，則 `UseWindowsService` 方法不會執行任何動作。

現在請使用下列其中一種方法來發佈您的應用程式：

* 在 [Visual Studio] 中，以滑鼠右鍵按一下專案，然後選取快捷方式功能表上的 [ **發行** ]。
* 從 .NET CLI。

當您發行 .NET 應用程式時，您可以選擇建立與 *framework 相依* 的部署或 *獨立* 的部署。 Framework 相依部署需要在執行的主機上安裝 .NET 共用執行時間。 獨立的部署是以 .NET 執行時間和架構的完整複本發行，而且可以在任何主機上執行。 如需詳細資訊，包括每個方法的優點和缺點，請參閱 [.net 應用程式部署](../../core/deploying/index.md) 檔。

若要發行應用程式的獨立組建，而不需要在主機上安裝 .NET 5.0 執行時間，請指定要包含在應用程式中的執行時間。 使用 `-r` (或 `--runtime`) 旗標。

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

若要發行與 framework 相依的組建，請省略 `-r` 旗標。

```dotnetcli
dotnet publish -c Release -o ./publish
```

將目錄的完整內容複寫 `publish` 到安裝資料夾。 然後，使用 [sc 工具](/windows/desktop/services/controlling-a-service-using-sc) 來建立可執行檔的 Windows 服務。

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>記錄到 Windows 事件記錄檔

`UseWindowsService`方法會自動新增[記錄](/aspnet/core/fundamentals/logging/)提供者，以將記錄檔訊息寫入 Windows 事件記錄檔。 您可以藉由將 `EventLog` 專案加入至 `Logging` 或其他設定來源的區段，來設定此提供者的記錄 `appsettings.json` 。

您可以在這些設定中設定屬性，以覆寫事件記錄檔中使用的來源名稱 `SourceName` 。 如果您未指定名稱，預設的應用程式名稱 (通常會使用) 的可執行元件名稱。

有關記錄的詳細資訊位於本章結尾。

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>使用 systemd 以 Linux 服務的形式執行您的應用程式

若要將 ASP.NET Core 應用程式設定為以 Linux 服務的形式執行 (或 Linux 說法) 中的 *daemon* ，請從 NuGet 安裝 [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) 套件。 然後，將呼叫新增至 `UseSystemd` `CreateHostBuilder` 中的方法 `Program.cs` 。

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
> 如果應用程式不是以 Linux 服務的形式執行，則 `UseSystemd` 方法不會執行任何動作。

現在發佈您的應用程式。 應用程式可以是 framework 相依或獨立于相關 Linux 執行時間的 (例如 `linux-x64`) 。 您可以使用下列其中一種方法來發佈：

* 在 [Visual Studio] 中，以滑鼠右鍵按一下專案，然後選取快捷方式功能表上的 [ **發行** ]。
* 從 .NET CLI 使用下列命令：

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
將目錄的完整內容複寫 `publish` 到 Linux 主機上的安裝資料夾。 註冊服務需要將特殊檔案（稱為 *單位* 檔）新增至 `/etc/systemd/system` 目錄。 您將需要根許可權，才能在此資料夾中建立檔案。 使用您想要使用的識別碼和延伸模組來命名檔案 `systemd` `.service` 。 例如，使用 `/etc/systemd/system/myapp.service`。

服務檔案使用 INI 格式，如下列範例所示：

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

`Type=notify`屬性會指示 `systemd` 應用程式在啟動和關閉時通知它。 `WantedBy=multi-user.target`當 Linux 系統到達「runlevel 2」時，此設定會導致服務啟動，這表示非圖形化的多使用者 shell 為作用中。

在 `systemd` 辨識服務之前，它需要重載其設定。 您可以 `systemd` 使用命令來控制 `systemctl` 。 重載之後，請使用 `status` 子命令確認應用程式已成功註冊。

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

如果您已正確設定服務，將會取得下列輸出：

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
> `.service`當您使用時，此延伸模組是選擇性的 `systemctl start` 。

若要指示 `systemd` 在系統啟動時自動啟動服務，請使用 `enable` 命令。

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>記錄至 journald

Linux 對等的 Windows 事件記錄檔是的 `journald` 一部分，這是的結構化記錄系統服務 `systemd` 。 Linux daemon 寫入標準輸出的記錄訊息會自動寫入至 `journald` 。 若要設定記錄層級，請使用記錄設定的 `Console` 區段。 主機產生器 `UseSystemd` 方法會自動將主控台輸出格式設定為符合日誌。

因為 `journald` 是 Linux 記錄的標準，所以有各式各樣的工具會與它整合。 您可以輕鬆地將記錄從路由傳送 `journald` 至外部記錄系統。 您可以使用 `journalctl` 命令，從命令列查看記錄檔，以在主機本機上工作。

```console
sudo journalctl -u myapp
```

> [!TIP]
> 如果您的主機上有可用的 GUI 環境，則有幾個圖形化記錄檢視器可供 Linux 使用，例如 *QJournalctl* 和 *gnome 記錄*。

若要深入瞭解如何 `systemd` 使用從命令列查詢日誌 `journalctl` ，請參閱 [manpages](https://manpages.debian.org/buster/systemd/journalctl.1)。

## <a name="https-certificates-for-self-hosted-applications"></a>自我裝載應用程式的 HTTPS 憑證

當您在生產環境中執行 gRPC 應用程式時，您應該使用來自信任憑證授權單位單位的 TLS 憑證 (CA) 。 此 CA 可能是公用 CA，或您組織的內部 ca。

在 Windows 主機上，您可以使用類別從安全的 [憑證存放區](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) 載入憑證 <xref:System.Security.Cryptography.X509Certificates.X509Store> 。 您也可以 `X509Store` 在某些 Linux 主機上使用類別搭配 OpenSSL 金鑰存放區。

您也可以使用其中一個 [X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)的函式，從下列其中一個方法建立憑證：

* 檔案，例如 `.pfx` 強式密碼所保護的檔案
* 從安全的儲存體服務（例如[Azure Key Vault](https://azure.microsoft.com/services/key-vault/) ）取出的二進位資料

您可以使用兩種方式設定 Kestrel 來使用憑證：從設定或在程式碼中。

### <a name="set-https-certificates-by-using-configuration"></a>使用 configuration 設定 HTTPS 憑證

設定方法需要在 [Kestrel 設定] 區段中設定憑證檔案的路徑 `.pfx` 和密碼。 在中 `appsettings.json` ，這看起來像這樣：

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

使用安全設定來源（例如 Azure Key Vault 或 Hashicorp Vault）來提供密碼。

> [!IMPORTANT]
> 請勿將未加密的密碼儲存在設定檔中。

### <a name="set-https-certificates-in-code"></a>在程式碼中設定 HTTPS 憑證

若要在程式碼中設定 Kestrel 上的 HTTPS，請在 `ConfigureKestrel` 類別中使用的方法 `IWebHostBuilder` `Program` 。

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

同樣地，請務必將檔案的密碼儲存 `.pfx` 在中，並從安全的設定來源加以取出。

>[!div class="step-by-step"]
>[上一個](grpc-in-production.md) 
>[下一步](docker.md)
