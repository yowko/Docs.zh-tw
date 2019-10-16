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
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="bf70f-103">自我裝載的 gRPC 應用程式</span><span class="sxs-lookup"><span data-stu-id="bf70f-103">Self-hosted gRPC applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="bf70f-104">雖然 ASP.NET Core 3.0 應用程式可以裝載在 Windows Server 上的 IIS 中，但目前無法在 IIS 中託管 gRPC 應用程式，因為尚未支援某些 HTTP/2 功能。</span><span class="sxs-lookup"><span data-stu-id="bf70f-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't yet supported.</span></span> <span data-ttu-id="bf70f-105">在未來的 Windows Server 更新中，預期會有這項功能。</span><span class="sxs-lookup"><span data-stu-id="bf70f-105">This functionality is expected in a future update to Windows Server.</span></span>

<span data-ttu-id="bf70f-106">由於 .NET Core 3.0 裝載延伸模組的一些新功能，您可以將應用程式當做 Windows 服務或由[systemd](https://en.wikipedia.org/wiki/Systemd)控制的 Linux 服務來執行。</span><span class="sxs-lookup"><span data-stu-id="bf70f-106">You can run your application as a Windows Service, or as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), thanks to some new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="bf70f-107">以 Windows 服務的形式執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="bf70f-107">Run your app as a Windows service</span></span>

<span data-ttu-id="bf70f-108">若要將您的 ASP.NET Core 應用程式設定為以 Windows 服務的身分執行，請從 NuGet 安裝[WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices)套件。</span><span class="sxs-lookup"><span data-stu-id="bf70f-108">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="bf70f-109">然後，將對的`UseWindowsService`呼叫加入`CreateHostBuilder`至中`Program.cs`的方法。</span><span class="sxs-lookup"><span data-stu-id="bf70f-109">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="bf70f-110">如果應用程式不是以 Windows 服務的形式執行`UseWindowsService` ，方法就不會進行任何動作。</span><span class="sxs-lookup"><span data-stu-id="bf70f-110">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="bf70f-111">現在從 Visual Studio 發行應用程式，方法是以滑鼠右鍵按一下專案，然後從操作功能表中選擇 [*發佈*]，或從 [.NET Core CLI]。</span><span class="sxs-lookup"><span data-stu-id="bf70f-111">Now publish your application, either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI.</span></span>

<span data-ttu-id="bf70f-112">當您發行 .NET Core 應用程式時，您可以選擇建立與*framework 相依*的部署或*獨立*的部署。</span><span class="sxs-lookup"><span data-stu-id="bf70f-112">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="bf70f-113">架構相依部署需要在執行的主機上安裝 .NET Core 共用執行時間。</span><span class="sxs-lookup"><span data-stu-id="bf70f-113">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="bf70f-114">獨立式部署是透過 .NET Core 執行時間和架構的完整複本發佈，而且可以在任何主機上執行。</span><span class="sxs-lookup"><span data-stu-id="bf70f-114">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="bf70f-115">如需詳細資訊，包括每種方法的優缺點，請參閱[.Net Core 應用程式部署](https://docs.microsoft.com/dotnet/core/deploying/)檔。</span><span class="sxs-lookup"><span data-stu-id="bf70f-115">For more information, including the advantages and disadvantages of each approach, refer to the [.NET Core application deployment](https://docs.microsoft.com/dotnet/core/deploying/) documentation.</span></span>

<span data-ttu-id="bf70f-116">若要發行不需要在主機上安裝 .net Core 3.0 執行時間之應用程式的獨立組建，請使用`-r` （或`--runtime`）旗標來指定要包含在應用程式中的執行時間。</span><span class="sxs-lookup"><span data-stu-id="bf70f-116">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application using the `-r` (or `--runtime`) flag.</span></span>

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="bf70f-117">若要發行與 framework 相依的組建，請`-r`省略旗標。</span><span class="sxs-lookup"><span data-stu-id="bf70f-117">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```console
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="bf70f-118">將`publish`目錄的完整內容複寫到安裝資料夾，並使用[sc 公用程式](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc)來建立可執行檔的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="bf70f-118">Copy the complete contents of the `publish` directory to an installation folder, and use the [sc utility](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a><span data-ttu-id="bf70f-119">記錄到 Windows 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="bf70f-119">Log to Windows Event Log</span></span>

<span data-ttu-id="bf70f-120">方法會自動新增[記錄](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0)提供者，將記錄訊息寫入 Windows 事件記錄檔。`UseWindowsService`</span><span class="sxs-lookup"><span data-stu-id="bf70f-120">The `UseWindowsService` method automatically adds a [Logging](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) provider that writes log messages to the Windows Event Log.</span></span> <span data-ttu-id="bf70f-121">您可以藉由將`EventLog`專案新增`Logging`至`appsettings.json`或其他設定來源的區段，來設定此提供者的記錄。</span><span class="sxs-lookup"><span data-stu-id="bf70f-121">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or other configuration source.</span></span> <span data-ttu-id="bf70f-122">事件記錄檔中使用的來源名稱可以藉由在這些`SourceName`設定中設定屬性來覆寫; 如果您未指定名稱，則會使用預設的應用程式名稱（通常是可執行檔元件名稱）。</span><span class="sxs-lookup"><span data-stu-id="bf70f-122">The source name used in Event Log can be overridden by setting a `SourceName` property in these settings; if you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="bf70f-123">如需有關記錄的詳細資訊，請到本章的結尾。</span><span class="sxs-lookup"><span data-stu-id="bf70f-123">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="bf70f-124">以 systemd 的 Linux 服務身分執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="bf70f-124">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="bf70f-125">若要將您的 ASP.NET Core 應用程式設定為以 Linux 服務（或 Linux 用語中中的*daemon* ）執行，請從 NuGet 安裝[Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd)套件。</span><span class="sxs-lookup"><span data-stu-id="bf70f-125">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="bf70f-126">然後，將對的`UseSystemd`呼叫加入`CreateHostBuilder`至中`Program.cs`的方法。</span><span class="sxs-lookup"><span data-stu-id="bf70f-126">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="bf70f-127">如果應用程式不是以 Linux 服務的身分執行`UseSystemd` ，方法就不會進行任何動作。</span><span class="sxs-lookup"><span data-stu-id="bf70f-127">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="bf70f-128">現在，從 Visual Studio，以滑鼠右鍵按一下專案，然後從操作功能表中選擇 [*發佈*]，或`linux-x64`從 .net，發佈您的應用程式（與 framework 相依，或獨立的 Linux 執行時間，例如）：使用下列命令的核心 CLI。</span><span class="sxs-lookup"><span data-stu-id="bf70f-128">Now publish your application (either framework-dependent, or self-contained for the relevant Linux runtime, e.g. `linux-x64`), either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI using the following command.</span></span>

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

<span data-ttu-id="bf70f-129">將`publish`目錄的完整內容複寫到 Linux 主機上的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf70f-129">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="bf70f-130">註冊服務需要一個稱為「單位檔案」的特殊檔案，才能新增至`/etc/systemd/system`目錄。</span><span class="sxs-lookup"><span data-stu-id="bf70f-130">Registering the service requires a special file, called a "unit file", to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="bf70f-131">您需要根許可權，才能在此資料夾中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="bf70f-131">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="bf70f-132">以您想`systemd`要使用的識別碼`.service`和副檔名來命名檔案。</span><span class="sxs-lookup"><span data-stu-id="bf70f-132">Name the file with the identifier you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="bf70f-133">例如，`/etc/systemd/system/myapp.service`。</span><span class="sxs-lookup"><span data-stu-id="bf70f-133">For example, `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="bf70f-134">服務檔會使用 INI 格式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bf70f-134">The service file uses INI format, as shown in this example.</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="bf70f-135">屬性會告知`systemd`應用程式會在啟動和關閉時通知它。 `Type=notify`</span><span class="sxs-lookup"><span data-stu-id="bf70f-135">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="bf70f-136">此`WantedBy=multi-user.target`設定會在 Linux 系統到達 "runlevel 2" 時啟動服務，這表示非圖形化的多使用者 shell 正在作用中。</span><span class="sxs-lookup"><span data-stu-id="bf70f-136">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2", meaning a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="bf70f-137">在`systemd`辨識服務之前，必須先重載其設定。</span><span class="sxs-lookup"><span data-stu-id="bf70f-137">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="bf70f-138">您可以`systemd` `systemctl`使用命令來控制。</span><span class="sxs-lookup"><span data-stu-id="bf70f-138">You control `systemd` using the `systemctl` command.</span></span> <span data-ttu-id="bf70f-139">重載之後，使用`status`子命令確認應用程式已成功註冊。</span><span class="sxs-lookup"><span data-stu-id="bf70f-139">After reloading, use the `status` subcommand to confirm the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="bf70f-140">如果您已正確設定服務，則會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bf70f-140">If you've configured the service correctly, the following output will be shown:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="bf70f-141">`start`使用命令來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="bf70f-141">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="bf70f-142">`.service` 使用`systemctl start`時，延伸模組是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="bf70f-142">The `.service` extension is optional when using `systemctl start`.</span></span>

<span data-ttu-id="bf70f-143">若要`systemd`指示在系統啟動時自動啟動服務，請`enable`使用命令。</span><span class="sxs-lookup"><span data-stu-id="bf70f-143">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="bf70f-144">記錄至 journald</span><span class="sxs-lookup"><span data-stu-id="bf70f-144">Log to journald</span></span>

<span data-ttu-id="bf70f-145">Windows 事件記錄檔的 Linux 對等專案`journald`是，屬於的`systemd`結構化記錄系統服務。</span><span class="sxs-lookup"><span data-stu-id="bf70f-145">The Linux equivalent of the Windows Event Log is `journald`, a structured logging system service that is part of `systemd`.</span></span> <span data-ttu-id="bf70f-146">Linux daemon 寫入標準輸出的記錄訊息會自動寫入`journald`，因此若要設定記錄層級，請`Console`使用記錄設定的區段。</span><span class="sxs-lookup"><span data-stu-id="bf70f-146">Log messages written to the standard output by a Linux daemon are automatically written to `journald`, so to configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="bf70f-147">`UseSystemd`主機產生器方法會自動設定主控台輸出格式，以符合日誌。</span><span class="sxs-lookup"><span data-stu-id="bf70f-147">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="bf70f-148">因為`journald`是 Linux 記錄檔的標準，所以有各種與它整合的工具，而且您可以輕鬆地將記錄從`journald`路由傳送至外部記錄系統。</span><span class="sxs-lookup"><span data-stu-id="bf70f-148">Because `journald` is the standard for Linux logs, there are a variety of tools that integrate with it, and you can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="bf70f-149">在主機本機上工作，您可以使用`journalctl`命令，從命令列中查看記錄。</span><span class="sxs-lookup"><span data-stu-id="bf70f-149">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="bf70f-150">如果您的主機上有可用的 GUI 環境，則有幾個圖形化記錄檢視器可供 Linux 使用，例如*QJournalctl*和*gnome 記錄*。</span><span class="sxs-lookup"><span data-stu-id="bf70f-150">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="bf70f-151">若要深入瞭解如何從命令列使用`journalctl`查詢 systemd 日誌，請參閱[man 頁面](https://manpages.debian.org/buster/systemd/journalctl.1)。</span><span class="sxs-lookup"><span data-stu-id="bf70f-151">To learn more about querying the systemd journal from the command line with `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="bf70f-152">自我裝載應用程式的 HTTPS 憑證</span><span class="sxs-lookup"><span data-stu-id="bf70f-152">HTTPS Certificates for self-hosted applications</span></span>

<span data-ttu-id="bf70f-153">在生產環境中執行 gRPC 應用程式時，您應該使用來自受信任憑證授權單位單位（CA）的 TLS 憑證。</span><span class="sxs-lookup"><span data-stu-id="bf70f-153">When running a gRPC application in production, you should use a TLS certificate from a trusted Certificate Authority (CA).</span></span> <span data-ttu-id="bf70f-154">此 CA 可以是公用 CA，也可以是您組織的內部帳戶。</span><span class="sxs-lookup"><span data-stu-id="bf70f-154">This CA could be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="bf70f-155">在 Windows 主機上，您可以使用[system.security.cryptography.x509certificates.x509store 類別](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0)，從安全的[憑證存放區](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores)載入憑證。</span><span class="sxs-lookup"><span data-stu-id="bf70f-155">On Windows hosts, the certificate may be loaded from a secure [Certificate Store](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) using the [X509Store class](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0).</span></span> <span data-ttu-id="bf70f-156">`X509Store`類別也可以與某些 Linux 主機上的 OpenSSL 金鑰存放區搭配使用。</span><span class="sxs-lookup"><span data-stu-id="bf70f-156">The `X509Store` class can also be used with the OpenSSL key-store on some Linux hosts.</span></span>

<span data-ttu-id="bf70f-157">您也可以使用其中一個[X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0)的處理常式來建立憑證，不論是從檔案（例如`.pfx`，受強式密碼保護的檔案），或是從從安全儲存體服務（例如 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)）取得的二進位資料。</span><span class="sxs-lookup"><span data-stu-id="bf70f-157">Certificates may also be created using one of the [X509Certificate2 constructors](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), either from a file (for example a `.pfx` file protected by a strong password), or from binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="bf70f-158">Kestrel 可設定為使用憑證的方式有兩種：從設定，或在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="bf70f-158">Kestrel can be configured to use a certificate in two ways: from configuration, or in code.</span></span>

### <a name="set-https-certificates-using-configuration"></a><span data-ttu-id="bf70f-159">使用 configuration 設定 HTTPS 憑證</span><span class="sxs-lookup"><span data-stu-id="bf70f-159">Set HTTPS certificates using configuration</span></span>

<span data-ttu-id="bf70f-160">設定方法需要將憑證`.pfx`檔案的路徑和 Kestrel 設定區段中的密碼。</span><span class="sxs-lookup"><span data-stu-id="bf70f-160">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="bf70f-161">在`appsettings.json`中看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="bf70f-161">In `appsettings.json` that would look like this.</span></span>

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

<span data-ttu-id="bf70f-162">您應該使用 Azure KeyVault 或 Hashicorp Vault 之類的安全設定來源來提供密碼。</span><span class="sxs-lookup"><span data-stu-id="bf70f-162">The password should be provided using a secure configuration source such as Azure KeyVault or Hashicorp Vault.</span></span>

<span data-ttu-id="bf70f-163">您不應該將未加密的密碼儲存在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="bf70f-163">You SHOULD NOT store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="bf70f-164">在程式碼中設定 HTTPS 憑證</span><span class="sxs-lookup"><span data-stu-id="bf70f-164">Set HTTPS certificates in code</span></span>

<span data-ttu-id="bf70f-165">若要在程式碼的 Kestrel 上設定 HTTPS `ConfigureKestrel` ，請`IWebHostBuilder`在`Program`類別中的上使用方法。</span><span class="sxs-lookup"><span data-stu-id="bf70f-165">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="bf70f-166">同樣地，檔案的密碼`.pfx`應該儲存在安全的設定來源並從中取出。</span><span class="sxs-lookup"><span data-stu-id="bf70f-166">Again, the password for the `.pfx` file should be stored in and retrieved from a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bf70f-167">[上一頁](grpc-in-production.md)
>[下一頁](docker.md)</span><span class="sxs-lookup"><span data-stu-id="bf70f-167">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
