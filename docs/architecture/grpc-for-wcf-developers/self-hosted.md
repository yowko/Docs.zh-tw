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
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="23d77-103">自我裝載的 gRPC 應用程式</span><span class="sxs-lookup"><span data-stu-id="23d77-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="23d77-104">雖然 ASP.NET Core 5.0 應用程式可裝載于 Windows Server 上的 IIS 中，但目前無法在 IIS 中裝載 gRPC 應用程式，因為某些 HTTP/2 功能不受支援。</span><span class="sxs-lookup"><span data-stu-id="23d77-104">Although ASP.NET Core 5.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="23d77-105">這項功能是 Windows Server 未來更新的目標。</span><span class="sxs-lookup"><span data-stu-id="23d77-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="23d77-106">您可以將應用程式當作 Windows 服務來執行。</span><span class="sxs-lookup"><span data-stu-id="23d77-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="23d77-107">或者，您也可以將它當作 [systemd](https://en.wikipedia.org/wiki/Systemd)所控制的 Linux 服務來執行，因為 .net 5.0 裝載延伸模組的新功能。</span><span class="sxs-lookup"><span data-stu-id="23d77-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET 5.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="23d77-108">以 Windows 服務的形式執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="23d77-108">Run your app as a Windows service</span></span>

<span data-ttu-id="23d77-109">若要將您的 ASP.NET Core 應用程式設定為以 Windows 服務形式執行，請從 NuGet 安裝 [WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) 套件。</span><span class="sxs-lookup"><span data-stu-id="23d77-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="23d77-110">然後，將呼叫新增至 `UseWindowsService` `CreateHostBuilder` 中的方法 `Program.cs` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="23d77-111">如果應用程式不是以 Windows 服務的方式執行，則 `UseWindowsService` 方法不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="23d77-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="23d77-112">現在請使用下列其中一種方法來發佈您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="23d77-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="23d77-113">在 [Visual Studio] 中，以滑鼠右鍵按一下專案，然後選取快捷方式功能表上的 [ **發行** ]。</span><span class="sxs-lookup"><span data-stu-id="23d77-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="23d77-114">從 .NET CLI。</span><span class="sxs-lookup"><span data-stu-id="23d77-114">From the .NET CLI.</span></span>

<span data-ttu-id="23d77-115">當您發行 .NET 應用程式時，您可以選擇建立與 *framework 相依* 的部署或 *獨立* 的部署。</span><span class="sxs-lookup"><span data-stu-id="23d77-115">When you publish a .NET application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="23d77-116">Framework 相依部署需要在執行的主機上安裝 .NET 共用執行時間。</span><span class="sxs-lookup"><span data-stu-id="23d77-116">Framework-dependent deployments require the .NET Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="23d77-117">獨立的部署是以 .NET 執行時間和架構的完整複本發行，而且可以在任何主機上執行。</span><span class="sxs-lookup"><span data-stu-id="23d77-117">Self-contained deployments are published with a complete copy of the .NET runtime and framework and can be run on any host.</span></span> <span data-ttu-id="23d77-118">如需詳細資訊，包括每個方法的優點和缺點，請參閱 [.net 應用程式部署](../../core/deploying/index.md) 檔。</span><span class="sxs-lookup"><span data-stu-id="23d77-118">For more information, including the advantages and disadvantages of each approach, see the [.NET application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="23d77-119">若要發行應用程式的獨立組建，而不需要在主機上安裝 .NET 5.0 執行時間，請指定要包含在應用程式中的執行時間。</span><span class="sxs-lookup"><span data-stu-id="23d77-119">To publish a self-contained build of the application that does not require the .NET 5.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="23d77-120">使用 `-r` (或 `--runtime`) 旗標。</span><span class="sxs-lookup"><span data-stu-id="23d77-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="23d77-121">若要發行與 framework 相依的組建，請省略 `-r` 旗標。</span><span class="sxs-lookup"><span data-stu-id="23d77-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="23d77-122">將目錄的完整內容複寫 `publish` 到安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="23d77-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="23d77-123">然後，使用 [sc 工具](/windows/desktop/services/controlling-a-service-using-sc) 來建立可執行檔的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="23d77-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="23d77-124">記錄到 Windows 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="23d77-124">Log to the Windows event log</span></span>

<span data-ttu-id="23d77-125">`UseWindowsService`方法會自動新增[記錄](/aspnet/core/fundamentals/logging/)提供者，以將記錄檔訊息寫入 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="23d77-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="23d77-126">您可以藉由將 `EventLog` 專案加入至 `Logging` 或其他設定來源的區段，來設定此提供者的記錄 `appsettings.json` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="23d77-127">您可以在這些設定中設定屬性，以覆寫事件記錄檔中使用的來源名稱 `SourceName` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="23d77-128">如果您未指定名稱，預設的應用程式名稱 (通常會使用) 的可執行元件名稱。</span><span class="sxs-lookup"><span data-stu-id="23d77-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="23d77-129">有關記錄的詳細資訊位於本章結尾。</span><span class="sxs-lookup"><span data-stu-id="23d77-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="23d77-130">使用 systemd 以 Linux 服務的形式執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="23d77-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="23d77-131">若要將 ASP.NET Core 應用程式設定為以 Linux 服務的形式執行 (或 Linux 說法) 中的 *daemon* ，請從 NuGet 安裝 [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) 套件。</span><span class="sxs-lookup"><span data-stu-id="23d77-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="23d77-132">然後，將呼叫新增至 `UseSystemd` `CreateHostBuilder` 中的方法 `Program.cs` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="23d77-133">如果應用程式不是以 Linux 服務的形式執行，則 `UseSystemd` 方法不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="23d77-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="23d77-134">現在發佈您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="23d77-134">Now publish your application.</span></span> <span data-ttu-id="23d77-135">應用程式可以是 framework 相依或獨立于相關 Linux 執行時間的 (例如 `linux-x64`) 。</span><span class="sxs-lookup"><span data-stu-id="23d77-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="23d77-136">您可以使用下列其中一種方法來發佈：</span><span class="sxs-lookup"><span data-stu-id="23d77-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="23d77-137">在 [Visual Studio] 中，以滑鼠右鍵按一下專案，然後選取快捷方式功能表上的 [ **發行** ]。</span><span class="sxs-lookup"><span data-stu-id="23d77-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="23d77-138">從 .NET CLI 使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="23d77-138">From the .NET CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="23d77-139">將目錄的完整內容複寫 `publish` 到 Linux 主機上的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="23d77-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="23d77-140">註冊服務需要將特殊檔案（稱為 *單位* 檔）新增至 `/etc/systemd/system` 目錄。</span><span class="sxs-lookup"><span data-stu-id="23d77-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="23d77-141">您將需要根許可權，才能在此資料夾中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="23d77-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="23d77-142">使用您想要使用的識別碼和延伸模組來命名檔案 `systemd` `.service` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="23d77-143">例如，使用 `/etc/systemd/system/myapp.service`。</span><span class="sxs-lookup"><span data-stu-id="23d77-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="23d77-144">服務檔案使用 INI 格式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="23d77-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="23d77-145">`Type=notify`屬性會指示 `systemd` 應用程式在啟動和關閉時通知它。</span><span class="sxs-lookup"><span data-stu-id="23d77-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="23d77-146">`WantedBy=multi-user.target`當 Linux 系統到達「runlevel 2」時，此設定會導致服務啟動，這表示非圖形化的多使用者 shell 為作用中。</span><span class="sxs-lookup"><span data-stu-id="23d77-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical, multi-user shell is active.</span></span>

<span data-ttu-id="23d77-147">在 `systemd` 辨識服務之前，它需要重載其設定。</span><span class="sxs-lookup"><span data-stu-id="23d77-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="23d77-148">您可以 `systemd` 使用命令來控制 `systemctl` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="23d77-149">重載之後，請使用 `status` 子命令確認應用程式已成功註冊。</span><span class="sxs-lookup"><span data-stu-id="23d77-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="23d77-150">如果您已正確設定服務，將會取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="23d77-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="23d77-151">使用 `start` 命令來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="23d77-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="23d77-152">`.service`當您使用時，此延伸模組是選擇性的 `systemctl start` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="23d77-153">若要指示 `systemd` 在系統啟動時自動啟動服務，請使用 `enable` 命令。</span><span class="sxs-lookup"><span data-stu-id="23d77-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="23d77-154">記錄至 journald</span><span class="sxs-lookup"><span data-stu-id="23d77-154">Log to journald</span></span>

<span data-ttu-id="23d77-155">Linux 對等的 Windows 事件記錄檔是的 `journald` 一部分，這是的結構化記錄系統服務 `systemd` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="23d77-156">Linux daemon 寫入標準輸出的記錄訊息會自動寫入至 `journald` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="23d77-157">若要設定記錄層級，請使用記錄設定的 `Console` 區段。</span><span class="sxs-lookup"><span data-stu-id="23d77-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="23d77-158">主機產生器 `UseSystemd` 方法會自動將主控台輸出格式設定為符合日誌。</span><span class="sxs-lookup"><span data-stu-id="23d77-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="23d77-159">因為 `journald` 是 Linux 記錄的標準，所以有各式各樣的工具會與它整合。</span><span class="sxs-lookup"><span data-stu-id="23d77-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="23d77-160">您可以輕鬆地將記錄從路由傳送 `journald` 至外部記錄系統。</span><span class="sxs-lookup"><span data-stu-id="23d77-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="23d77-161">您可以使用 `journalctl` 命令，從命令列查看記錄檔，以在主機本機上工作。</span><span class="sxs-lookup"><span data-stu-id="23d77-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="23d77-162">如果您的主機上有可用的 GUI 環境，則有幾個圖形化記錄檢視器可供 Linux 使用，例如 *QJournalctl* 和 *gnome 記錄*。</span><span class="sxs-lookup"><span data-stu-id="23d77-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="23d77-163">若要深入瞭解如何 `systemd` 使用從命令列查詢日誌 `journalctl` ，請參閱 [manpages](https://manpages.debian.org/buster/systemd/journalctl.1)。</span><span class="sxs-lookup"><span data-stu-id="23d77-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="23d77-164">自我裝載應用程式的 HTTPS 憑證</span><span class="sxs-lookup"><span data-stu-id="23d77-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="23d77-165">當您在生產環境中執行 gRPC 應用程式時，您應該使用來自信任憑證授權單位單位的 TLS 憑證 (CA) 。</span><span class="sxs-lookup"><span data-stu-id="23d77-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="23d77-166">此 CA 可能是公用 CA，或您組織的內部 ca。</span><span class="sxs-lookup"><span data-stu-id="23d77-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="23d77-167">在 Windows 主機上，您可以使用類別從安全的 [憑證存放區](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) 載入憑證 <xref:System.Security.Cryptography.X509Certificates.X509Store> 。</span><span class="sxs-lookup"><span data-stu-id="23d77-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="23d77-168">您也可以 `X509Store` 在某些 Linux 主機上使用類別搭配 OpenSSL 金鑰存放區。</span><span class="sxs-lookup"><span data-stu-id="23d77-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="23d77-169">您也可以使用其中一個 [X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)的函式，從下列其中一個方法建立憑證：</span><span class="sxs-lookup"><span data-stu-id="23d77-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="23d77-170">檔案，例如 `.pfx` 強式密碼所保護的檔案</span><span class="sxs-lookup"><span data-stu-id="23d77-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="23d77-171">從安全的儲存體服務（例如[Azure Key Vault](https://azure.microsoft.com/services/key-vault/) ）取出的二進位資料</span><span class="sxs-lookup"><span data-stu-id="23d77-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="23d77-172">您可以使用兩種方式設定 Kestrel 來使用憑證：從設定或在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="23d77-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="23d77-173">使用 configuration 設定 HTTPS 憑證</span><span class="sxs-lookup"><span data-stu-id="23d77-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="23d77-174">設定方法需要在 [Kestrel 設定] 區段中設定憑證檔案的路徑 `.pfx` 和密碼。</span><span class="sxs-lookup"><span data-stu-id="23d77-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="23d77-175">在中 `appsettings.json` ，這看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="23d77-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="23d77-176">使用安全設定來源（例如 Azure Key Vault 或 Hashicorp Vault）來提供密碼。</span><span class="sxs-lookup"><span data-stu-id="23d77-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23d77-177">請勿將未加密的密碼儲存在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="23d77-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="23d77-178">在程式碼中設定 HTTPS 憑證</span><span class="sxs-lookup"><span data-stu-id="23d77-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="23d77-179">若要在程式碼中設定 Kestrel 上的 HTTPS，請在 `ConfigureKestrel` 類別中使用的方法 `IWebHostBuilder` `Program` 。</span><span class="sxs-lookup"><span data-stu-id="23d77-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="23d77-180">同樣地，請務必將檔案的密碼儲存 `.pfx` 在中，並從安全的設定來源加以取出。</span><span class="sxs-lookup"><span data-stu-id="23d77-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="23d77-181">[上一個](grpc-in-production.md) 
>[下一步](docker.md)</span><span class="sxs-lookup"><span data-stu-id="23d77-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
