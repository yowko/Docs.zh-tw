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
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="3f84d-103">自託管 gRPC 應用程式</span><span class="sxs-lookup"><span data-stu-id="3f84d-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="3f84d-104">儘管 ASP.NET Core 3.0 應用程式可以在 Windows 伺服器上的 IIS 中託管，但當前無法在 IIS 中託管 gRPC 應用程式，因為某些 HTTP/2 功能不受支援。</span><span class="sxs-lookup"><span data-stu-id="3f84d-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="3f84d-105">此功能是將來更新到 Windows 伺服器的目標。</span><span class="sxs-lookup"><span data-stu-id="3f84d-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="3f84d-106">您可以將應用程式作為 Windows 服務運行。</span><span class="sxs-lookup"><span data-stu-id="3f84d-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="3f84d-107">或者，由於 .NET Core 3.0 託管擴展中的新功能，您可以將它作為由[系統控制的](https://en.wikipedia.org/wiki/Systemd)Linux 服務運行。</span><span class="sxs-lookup"><span data-stu-id="3f84d-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="3f84d-108">將應用作為 Windows 服務運行</span><span class="sxs-lookup"><span data-stu-id="3f84d-108">Run your app as a Windows service</span></span>

<span data-ttu-id="3f84d-109">要將ASP.NET核心應用程式佈建為 Windows 服務運行，請安裝來自 NuGet 的[Microsoft.擴展.託管.Windows服務](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices)包。</span><span class="sxs-lookup"><span data-stu-id="3f84d-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="3f84d-110">然後向`UseWindowsService`中`CreateHostBuilder``Program.cs`的方法添加調用。</span><span class="sxs-lookup"><span data-stu-id="3f84d-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="3f84d-111">如果應用程式未作為 Windows 服務運行，則`UseWindowsService`該方法不執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="3f84d-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="3f84d-112">現在使用以下方法之一發布應用程式：</span><span class="sxs-lookup"><span data-stu-id="3f84d-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="3f84d-113">通過按右鍵專案並在快顯功能表上選擇 **"發佈"，** 從視覺化工作室開始。</span><span class="sxs-lookup"><span data-stu-id="3f84d-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="3f84d-114">從 .NET 核心 CLI。</span><span class="sxs-lookup"><span data-stu-id="3f84d-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="3f84d-115">發佈 .NET Core 應用程式時，可以選擇創建*與框架相關的*部署或*自包含*部署。</span><span class="sxs-lookup"><span data-stu-id="3f84d-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="3f84d-116">與框架相關的部署要求在運行它們的主機上安裝 .NET Core 共用運行時。</span><span class="sxs-lookup"><span data-stu-id="3f84d-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="3f84d-117">自包含部署使用 .NET Core 運行時和框架的完整副本發佈，可在任何主機上運行。</span><span class="sxs-lookup"><span data-stu-id="3f84d-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="3f84d-118">有關詳細資訊（包括每種方法的優缺點），請參閱[.NET Core 應用程式部署](../../core/deploying/index.md)文檔。</span><span class="sxs-lookup"><span data-stu-id="3f84d-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="3f84d-119">要發佈不需要在主機上安裝 .NET Core 3.0 運行時的應用程式的自包含生成，請指定要包含在應用程式中的運行時。</span><span class="sxs-lookup"><span data-stu-id="3f84d-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="3f84d-120">使用`-r`（或`--runtime`） 標誌。</span><span class="sxs-lookup"><span data-stu-id="3f84d-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="3f84d-121">要發佈與框架相關的生成，省略該`-r`標誌。</span><span class="sxs-lookup"><span data-stu-id="3f84d-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="3f84d-122">將`publish`目錄的完整內容複寫到安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f84d-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="3f84d-123">然後，使用[sc 工具](/windows/desktop/services/controlling-a-service-using-sc)為可執行檔創建 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="3f84d-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="3f84d-124">登錄到 Windows 事件日誌</span><span class="sxs-lookup"><span data-stu-id="3f84d-124">Log to the Windows event log</span></span>

<span data-ttu-id="3f84d-125">該方法`UseWindowsService`會自動添加將日誌消息寫入 Windows 事件日誌的[日誌記錄](/aspnet/core/fundamentals/logging/)提供程式。</span><span class="sxs-lookup"><span data-stu-id="3f84d-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="3f84d-126">您可以通過向 的 分區或其他配置源添加`EventLog`條目來配置`Logging`此提供程式`appsettings.json`的日誌記錄。</span><span class="sxs-lookup"><span data-stu-id="3f84d-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="3f84d-127">可以通過在這些設置中設置`SourceName`屬性來覆蓋事件日誌中使用的源名稱。</span><span class="sxs-lookup"><span data-stu-id="3f84d-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="3f84d-128">如果不指定名稱，將使用預設應用程式名稱（通常是可執行程式集名稱）。</span><span class="sxs-lookup"><span data-stu-id="3f84d-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="3f84d-129">有關日誌記錄的詳細資訊，在本章的末尾。</span><span class="sxs-lookup"><span data-stu-id="3f84d-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="3f84d-130">使用系統運行應用作為 Linux 服務</span><span class="sxs-lookup"><span data-stu-id="3f84d-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="3f84d-131">要將ASP.NET核心應用程式佈建為以 Linux 服務（或 Linux 術語中的*守護進程*）運行，請安裝[Microsoft.擴展.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd)套裝程式（ NuGet）。</span><span class="sxs-lookup"><span data-stu-id="3f84d-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="3f84d-132">然後向`UseSystemd`中`CreateHostBuilder``Program.cs`的方法添加調用。</span><span class="sxs-lookup"><span data-stu-id="3f84d-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="3f84d-133">如果應用程式未作為 Linux 服務運行，則`UseSystemd`該方法不執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="3f84d-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="3f84d-134">現在發佈應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f84d-134">Now publish your application.</span></span> <span data-ttu-id="3f84d-135">對於相關的 Linux 運行時（例如，）。`linux-x64`應用程式可以是依賴于框架的，也可以是自包含的。</span><span class="sxs-lookup"><span data-stu-id="3f84d-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="3f84d-136">可以使用以下方法之一進行發佈：</span><span class="sxs-lookup"><span data-stu-id="3f84d-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="3f84d-137">通過按右鍵專案並在快顯功能表上選擇 **"發佈"，** 從視覺化工作室開始。</span><span class="sxs-lookup"><span data-stu-id="3f84d-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="3f84d-138">從 .NET 核心 CLI，通過使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f84d-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="3f84d-139">將`publish`目錄的完整內容複寫到 Linux 主機上的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f84d-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="3f84d-140">註冊服務需要將一個特殊的檔（稱為*單中繼檔*）添加到`/etc/systemd/system`目錄中。</span><span class="sxs-lookup"><span data-stu-id="3f84d-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="3f84d-141">您需要根許可權才能在此資料夾中創建檔。</span><span class="sxs-lookup"><span data-stu-id="3f84d-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="3f84d-142">使用要使用的`systemd`識別碼和副檔名`.service`命名檔。</span><span class="sxs-lookup"><span data-stu-id="3f84d-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="3f84d-143">例如，使用 `/etc/systemd/system/myapp.service`。</span><span class="sxs-lookup"><span data-stu-id="3f84d-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="3f84d-144">服務檔使用 INI 格式，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="3f84d-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="3f84d-145">該`Type=notify`屬性告訴`systemd`應用程式將在啟動和關閉時通知它。</span><span class="sxs-lookup"><span data-stu-id="3f84d-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="3f84d-146">當`WantedBy=multi-user.target`Linux 系統達到"執行層級 2"時，該設置將導致服務啟動，這意味著非圖形多使用者外殼處於活動狀態。</span><span class="sxs-lookup"><span data-stu-id="3f84d-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="3f84d-147">在`systemd`識別服務之前，它需要重新載入其配置。</span><span class="sxs-lookup"><span data-stu-id="3f84d-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="3f84d-148">您可以使用`systemd`命令`systemctl`進行控制。</span><span class="sxs-lookup"><span data-stu-id="3f84d-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="3f84d-149">重新載入後，`status`使用子命令確認應用程式已成功註冊。</span><span class="sxs-lookup"><span data-stu-id="3f84d-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="3f84d-150">如果配置的服務正確，您將獲得以下輸出：</span><span class="sxs-lookup"><span data-stu-id="3f84d-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="3f84d-151">使用`start`命令啟動服務。</span><span class="sxs-lookup"><span data-stu-id="3f84d-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="3f84d-152">使用`.service``systemctl start`時，擴展是可選的。</span><span class="sxs-lookup"><span data-stu-id="3f84d-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="3f84d-153">要告訴`systemd`在系統啟動時自動啟動服務，請使用 命令`enable`。</span><span class="sxs-lookup"><span data-stu-id="3f84d-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="3f84d-154">日誌</span><span class="sxs-lookup"><span data-stu-id="3f84d-154">Log to journald</span></span>

<span data-ttu-id="3f84d-155">與 Windows 事件日誌等效的`journald`Linux 是 ，是 中的`systemd`結構化日誌記錄系統服務。</span><span class="sxs-lookup"><span data-stu-id="3f84d-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="3f84d-156">Linux 守護進程寫入標準輸出的日誌消息將自動寫入`journald`。</span><span class="sxs-lookup"><span data-stu-id="3f84d-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="3f84d-157">要配置日誌記錄級別，`Console`請使用日誌記錄配置的部分。</span><span class="sxs-lookup"><span data-stu-id="3f84d-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="3f84d-158">主機`UseSystemd`產生器方法自動設定主控台輸出格式以適應日誌。</span><span class="sxs-lookup"><span data-stu-id="3f84d-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="3f84d-159">因為它是`journald`Linux 日誌的標準，因此各種工具都集成在一起。</span><span class="sxs-lookup"><span data-stu-id="3f84d-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="3f84d-160">您可以輕鬆地將日誌從`journald`外部日誌記錄系統路由到外部日誌記錄系統。</span><span class="sxs-lookup"><span data-stu-id="3f84d-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="3f84d-161">在主機的本地工作，可以使用 命令`journalctl`查看命令列中的日誌。</span><span class="sxs-lookup"><span data-stu-id="3f84d-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="3f84d-162">如果您的主機上有可用的 GUI 環境，則一些圖形日誌檢視器可用於 Linux，例如*QJournalctl*和*gnome 日誌*。</span><span class="sxs-lookup"><span data-stu-id="3f84d-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="3f84d-163">要瞭解有關使用`journalctl`從 命令`systemd`行查詢日誌的更多內容，請參閱[man 頁](https://manpages.debian.org/buster/systemd/journalctl.1)。</span><span class="sxs-lookup"><span data-stu-id="3f84d-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="3f84d-164">用於自託管應用程式的 HTTPS 證書</span><span class="sxs-lookup"><span data-stu-id="3f84d-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="3f84d-165">在生產中運行 gRPC 應用程式時，應使用來自受信任的憑證授權單位 （CA） 的 TLS 證書。</span><span class="sxs-lookup"><span data-stu-id="3f84d-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="3f84d-166">此 CA 可能是公共 CA，也可以是組織的內部 CA。</span><span class="sxs-lookup"><span data-stu-id="3f84d-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="3f84d-167">在 Windows 主機上，可以使用<xref:System.Security.Cryptography.X509Certificates.X509Store>類從安全[憑證存放區載入](/windows/win32/seccrypto/managing-certificates-with-certificate-stores)證書。</span><span class="sxs-lookup"><span data-stu-id="3f84d-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="3f84d-168">您還可以在某些 Linux`X509Store`主機上將該類與 OpenSSL 金鑰存儲一起使用。</span><span class="sxs-lookup"><span data-stu-id="3f84d-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="3f84d-169">還可以通過使用[X509 證書2建構函式](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)之一從以下任一創建證書：</span><span class="sxs-lookup"><span data-stu-id="3f84d-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="3f84d-170">檔，`.pfx`如受強式密碼保護的檔</span><span class="sxs-lookup"><span data-stu-id="3f84d-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="3f84d-171">從安全存儲服務（如[Azure 金鑰保存庫](https://azure.microsoft.com/services/key-vault/)）檢索的二進位資料</span><span class="sxs-lookup"><span data-stu-id="3f84d-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="3f84d-172">您可以將 Kestrel 配置為以兩種方式使用證書：從配置或代碼中。</span><span class="sxs-lookup"><span data-stu-id="3f84d-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="3f84d-173">使用配置設置 HTTPS 證書</span><span class="sxs-lookup"><span data-stu-id="3f84d-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="3f84d-174">配置方法要求在 Kestrel 配置部分`.pfx`中設置證書檔和密碼的路徑。</span><span class="sxs-lookup"><span data-stu-id="3f84d-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="3f84d-175">在`appsettings.json`中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f84d-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="3f84d-176">通過使用安全配置源（如 Azure 金鑰保存庫或 Hashicorp 保存庫）提供密碼。</span><span class="sxs-lookup"><span data-stu-id="3f84d-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3f84d-177">不要在設定檔中存儲未加密的密碼。</span><span class="sxs-lookup"><span data-stu-id="3f84d-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="3f84d-178">在代碼中設置 HTTPS 證書</span><span class="sxs-lookup"><span data-stu-id="3f84d-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="3f84d-179">要在代碼中配置 Kestrel 上的`ConfigureKestrel`HTTPS，`IWebHostBuilder`請使用`Program`類 中 的方法。</span><span class="sxs-lookup"><span data-stu-id="3f84d-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="3f84d-180">同樣，請確保將`.pfx`檔的密碼存儲在安全配置源中並從中檢索。</span><span class="sxs-lookup"><span data-stu-id="3f84d-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3f84d-181">[上一個](grpc-in-production.md)
>[下一個](docker.md)</span><span class="sxs-lookup"><span data-stu-id="3f84d-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
