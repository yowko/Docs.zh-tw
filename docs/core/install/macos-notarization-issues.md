---
title: 使用 macOS Catalina 公證
description: 安裝 .NET Core 運行時、SDK 和使用 .NET Core 構建的應用程式時，如何處理 macOS 的公證和證書問題。
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: be39c1ea56699f84736a2b37bc958507b16e826b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146745"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a><span data-ttu-id="fabeb-103">macOS Catalina 公證及其對 .NET 核心下載和專案的影響</span><span class="sxs-lookup"><span data-stu-id="fabeb-103">macOS Catalina Notarization and the impact on .NET Core downloads and projects</span></span>

<span data-ttu-id="fabeb-104">從 macOS Catalina（版本 10.15）開始，所有在 2019 年 6 月 1 日之後構建且使用開發人員 ID 分發的軟體都必須經過公證。</span><span class="sxs-lookup"><span data-stu-id="fabeb-104">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019, and distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="fabeb-105">此要求適用于 .NET 核心運行時、.NET 核心 SDK 和使用 .NET Core 創建的軟體。</span><span class="sxs-lookup"><span data-stu-id="fabeb-105">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span> <span data-ttu-id="fabeb-106">本文介紹了使用 .NET Core 和 macOS 公證可能面臨的常見方案。</span><span class="sxs-lookup"><span data-stu-id="fabeb-106">This article describes the common scenarios you may face with .NET Core and macOS notarization.</span></span>

## <a name="installing-net-core"></a><span data-ttu-id="fabeb-107">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="fabeb-107">Installing .NET Core</span></span>

<span data-ttu-id="fabeb-108">自 2020 年 2 月 18 日起，對 .NET Core（運行時和 SDK）版本 3.1、3.0 和 2.1 的安裝程式進行了公證。</span><span class="sxs-lookup"><span data-stu-id="fabeb-108">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="fabeb-109">未對以前發佈的版本進行公證。</span><span class="sxs-lookup"><span data-stu-id="fabeb-109">Prior released versions aren't notarized.</span></span> <span data-ttu-id="fabeb-110">您可以手動安裝未經公證版本的 .NET Core，首先下載安裝程式，然後使用 命令`sudo installer`。</span><span class="sxs-lookup"><span data-stu-id="fabeb-110">You can manually install a non-notarized version of .NET Core by first downloading the installer, and then using the `sudo installer` command.</span></span> <span data-ttu-id="fabeb-111">有關詳細資訊，請參閱為[macOS 下載和手動安裝](sdk.md?pivots=os-macos#download-and-manually-install)。</span><span class="sxs-lookup"><span data-stu-id="fabeb-111">For more information, see [Download and manually install for macOS](sdk.md?pivots=os-macos#download-and-manually-install).</span></span>

<span data-ttu-id="fabeb-112">從以下版本開始，對 .NET Core 安裝程式進行了公證：</span><span class="sxs-lookup"><span data-stu-id="fabeb-112">Beginning with the following versions, the .NET Core installers are notarized:</span></span>

- <span data-ttu-id="fabeb-113">.NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="fabeb-113">.NET Core Runtime</span></span>
  - <span data-ttu-id="fabeb-114">2.1.16</span><span class="sxs-lookup"><span data-stu-id="fabeb-114">2.1.16</span></span>
  - <span data-ttu-id="fabeb-115">3.0.3</span><span class="sxs-lookup"><span data-stu-id="fabeb-115">3.0.3</span></span>
  - <span data-ttu-id="fabeb-116">3.1.2</span><span class="sxs-lookup"><span data-stu-id="fabeb-116">3.1.2</span></span>

- <span data-ttu-id="fabeb-117">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="fabeb-117">.NET Core SDK</span></span>
  - <span data-ttu-id="fabeb-118">2.1.512</span><span class="sxs-lookup"><span data-stu-id="fabeb-118">2.1.512</span></span>
  - <span data-ttu-id="fabeb-119">3.0.103</span><span class="sxs-lookup"><span data-stu-id="fabeb-119">3.0.103</span></span>
  - <span data-ttu-id="fabeb-120">3.1.102</span><span class="sxs-lookup"><span data-stu-id="fabeb-120">3.1.102</span></span>

## <a name="apphost-is-disabled-by-default"></a><span data-ttu-id="fabeb-121">預設情況下禁用應用主機</span><span class="sxs-lookup"><span data-stu-id="fabeb-121">appHost is disabled by default</span></span>

<span data-ttu-id="fabeb-122">預設情況下，在專案編譯、發佈或運行時，.NET Core SDK 3.0 及以上的非公證版本將生成本機 Mach-O 可執行檔（稱為**appHost）。**</span><span class="sxs-lookup"><span data-stu-id="fabeb-122">By default, non-notarized versions of the .NET Core SDK 3.0 and above produce a native Mach-O executable (known as the **appHost**) when your project compiles, publishes, or is run.</span></span> <span data-ttu-id="fabeb-123">此可執行檔是運行應用的便捷方式。</span><span class="sxs-lookup"><span data-stu-id="fabeb-123">This executable is a convenient way to run your app.</span></span> <span data-ttu-id="fabeb-124">否則，你的應用必須通過運行`dotnet <filename.dll>`啟動。</span><span class="sxs-lookup"><span data-stu-id="fabeb-124">Otherwise, your app must be started by running `dotnet <filename.dll>`.</span></span> <span data-ttu-id="fabeb-125">啟用應用Host後，將在`dotnet run`應用Host 的上下文中調用該命令。</span><span class="sxs-lookup"><span data-stu-id="fabeb-125">When the appHost is enabled, the `dotnet run` command is invoked in the context of the appHost.</span></span> <span data-ttu-id="fabeb-126">有關詳細資訊，請參閱[應用Host 的上下文](#context-of-the-apphost)。</span><span class="sxs-lookup"><span data-stu-id="fabeb-126">For more information, see [Context of the appHost](#context-of-the-apphost).</span></span>

<span data-ttu-id="fabeb-127">從 .NET Core SDK 3.0 及以上公證版本開始，預設情況下不會生成 appHost 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="fabeb-127">Starting with the notarized versions of the .NET Core SDK 3.0 and above, the appHost executable isn't generated by default.</span></span> <span data-ttu-id="fabeb-128">您可以使用專案檔案中的[`UseAppHost`](../project-sdk/msbuild-props.md#useapphost)布林設置打開 appHost 生成。</span><span class="sxs-lookup"><span data-stu-id="fabeb-128">You can turn on appHost generation with the [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) boolean setting in the project file.</span></span> <span data-ttu-id="fabeb-129">您還可以在命令列上切換應用Host，`-p:UseAppHost`以進行運行的特定`dotnet`命令：</span><span class="sxs-lookup"><span data-stu-id="fabeb-129">You can also toggle the appHost with the `-p:UseAppHost` parameter on the command line for the specific `dotnet` command you run:</span></span>

- <span data-ttu-id="fabeb-130">專案檔</span><span class="sxs-lookup"><span data-stu-id="fabeb-130">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="fabeb-131">命令列參數</span><span class="sxs-lookup"><span data-stu-id="fabeb-131">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="fabeb-132">發佈應用[自包含](../deploying/index.md#publish-self-contained)時，始終會創建應用Host。</span><span class="sxs-lookup"><span data-stu-id="fabeb-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="fabeb-133">有關該`UseAppHost`設置的詳細資訊，請參閱[Microsoft.NET.Sdk 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。</span><span class="sxs-lookup"><span data-stu-id="fabeb-133">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="context-of-the-apphost"></a><span data-ttu-id="fabeb-134">應用主機的上下文</span><span class="sxs-lookup"><span data-stu-id="fabeb-134">Context of the appHost</span></span>

<span data-ttu-id="fabeb-135">在專案中啟用 appHost 並使用`dotnet run`該命令運行應用時，將在 appHost 的上下文中而不是預設主機（預設主機是`dotnet`命令）中調用應用。</span><span class="sxs-lookup"><span data-stu-id="fabeb-135">When the appHost is enabled in your project, and you use the `dotnet run` command to run your app, the app is invoked in the context of the appHost and not the default host (the default host is the `dotnet` command).</span></span> <span data-ttu-id="fabeb-136">如果在專案中禁用了 appHost，該命令將在`dotnet run`預設主機的上下文中運行應用。</span><span class="sxs-lookup"><span data-stu-id="fabeb-136">If the appHost is disabled in your project, the `dotnet run` command runs your app in the context of the default host.</span></span> <span data-ttu-id="fabeb-137">即使禁用了 appHost，將應用發佈為自包含將生成一個 AppHost 可執行檔，並且使用者使用該可執行檔來運行你的應用。</span><span class="sxs-lookup"><span data-stu-id="fabeb-137">Even if the appHost is disabled, publishing your app as self-contained generates an appHost executable, and users use that executable to run your app.</span></span> <span data-ttu-id="fabeb-138">使用`dotnet <filename.dll>`預設主機（共用運行時）調用應用運行應用。</span><span class="sxs-lookup"><span data-stu-id="fabeb-138">Running your app with `dotnet <filename.dll>` invokes the app with the default host, the shared runtime.</span></span>

<span data-ttu-id="fabeb-139">調用使用 appHost 的應用時，應用訪問的證書分區與經公證的預設主機不同。</span><span class="sxs-lookup"><span data-stu-id="fabeb-139">When an app using the appHost is invoked, the certificate partition accessed by the app is different from the notarized default host.</span></span> <span data-ttu-id="fabeb-140">如果應用必須訪問通過預設主機安裝的證書，請使用 命令`dotnet run`從其專案檔案運行應用，或使用 該`dotnet <filename.dll>`命令直接啟動應用。</span><span class="sxs-lookup"><span data-stu-id="fabeb-140">If your app must access the certificates installed through the default host, use the `dotnet run` command to run your app from its project file, or use the `dotnet <filename.dll>` command to start the app directly.</span></span>

<span data-ttu-id="fabeb-141">有關此方案的詳細資訊，ASP.NET[核心和 macOS 和證書](#aspnet-core-and-macos-and-certificates)部分提供。</span><span class="sxs-lookup"><span data-stu-id="fabeb-141">More information about this scenario is provided in the [ASP.NET Core and macOS and certificates](#aspnet-core-and-macos-and-certificates) section.</span></span>

## <a name="aspnet-core-and-macos-and-certificates"></a><span data-ttu-id="fabeb-142">ASP.NET核心和 macOS 和證書</span><span class="sxs-lookup"><span data-stu-id="fabeb-142">ASP.NET Core and macOS and certificates</span></span>

<span data-ttu-id="fabeb-143">.NET Core 提供使用<xref:System.Security.Cryptography.X509Certificates>類管理 macOS 鑰匙串中的證書的能力。</span><span class="sxs-lookup"><span data-stu-id="fabeb-143">.NET Core provides the ability to manage certificates in the macOS Keychain with the <xref:System.Security.Cryptography.X509Certificates> class.</span></span> <span data-ttu-id="fabeb-144">在決定要考慮哪個分區時，對 macOS 鑰匙串的訪問使用應用程式標識作為主鍵。</span><span class="sxs-lookup"><span data-stu-id="fabeb-144">Access to the macOS Keychain uses the applications identity as the primary key when deciding which partition to consider.</span></span> <span data-ttu-id="fabeb-145">例如，未簽名的應用程式在未簽名的分區中存儲機密，但簽名的應用程式僅將其機密存儲在分區中，他們才能訪問。</span><span class="sxs-lookup"><span data-stu-id="fabeb-145">For example, unsigned applications store secrets in the unsigned partition, but signed applications store their secrets in partitions only they can access.</span></span> <span data-ttu-id="fabeb-146">調用應用的執行源決定要使用的分區。</span><span class="sxs-lookup"><span data-stu-id="fabeb-146">The source of execution that invokes your app decides which partition to use.</span></span>

<span data-ttu-id="fabeb-147">.NET Core 提供三個執行源[：appHost、](#apphost-is-disabled-by-default)預設主機`dotnet`（命令）和自訂主機。</span><span class="sxs-lookup"><span data-stu-id="fabeb-147">.NET Core provides three sources of execution: [appHost](#apphost-is-disabled-by-default), default host (the `dotnet` command), and a custom host.</span></span> <span data-ttu-id="fabeb-148">每個執行模型可能具有不同的標識（簽名身份或未簽名身份），並且有權訪問鑰匙串中的不同分區。</span><span class="sxs-lookup"><span data-stu-id="fabeb-148">Each execution model may have different identities, either signed or unsigned, and has access to different partitions within the Keychain.</span></span> <span data-ttu-id="fabeb-149">一種模式導入的證書可能無法從另一種模式訪問。</span><span class="sxs-lookup"><span data-stu-id="fabeb-149">Certificates imported by one mode may not be accessible from another.</span></span> <span data-ttu-id="fabeb-150">例如，.NET Core 的公證版本具有已簽名的預設主機。</span><span class="sxs-lookup"><span data-stu-id="fabeb-150">For example, the notarized versions of .NET Core have a default host that is signed.</span></span> <span data-ttu-id="fabeb-151">證書根據其標識導入到安全分區中。</span><span class="sxs-lookup"><span data-stu-id="fabeb-151">Certificates are imported into a secure partition based on its identity.</span></span> <span data-ttu-id="fabeb-152">這些證書無法從生成的應用Host訪問，因為應用Host是無符號的。</span><span class="sxs-lookup"><span data-stu-id="fabeb-152">These certificates aren't accessible from a generated appHost, as the appHost is unsigned.</span></span>

<span data-ttu-id="fabeb-153">另一個示例，預設情況下，ASP.NET核心通過預設主機導入預設 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="fabeb-153">Another example, by default, ASP.NET Core imports a default SSL certificate through the default host.</span></span> <span data-ttu-id="fabeb-154">ASP.NET使用 appHost 的酷睿應用程式將無法訪問此證書，並且當 .NET Core 檢測到證書不可訪問時，將收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="fabeb-154">ASP.NET Core applications that use an appHost won't have access to this certificate and will receive an error when .NET Core detects the certificate isn't accessible.</span></span> <span data-ttu-id="fabeb-155">錯誤訊息提供有關如何解決此問題的說明。</span><span class="sxs-lookup"><span data-stu-id="fabeb-155">The error message provides instructions on how to fix this problem.</span></span>

<span data-ttu-id="fabeb-156">如果需要證書共用，macOS 會為`security`實用程式提供配置選項。</span><span class="sxs-lookup"><span data-stu-id="fabeb-156">If certificate sharing is required, macOS provides configuration options with the `security` utility.</span></span>

<span data-ttu-id="fabeb-157">有關如何解決ASP.NET核心證書問題的詳細資訊，請參閱[ASP.NET核心中強制實施 HTTPS。](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems)</span><span class="sxs-lookup"><span data-stu-id="fabeb-157">For more information on how to troubleshoot ASP.NET Core certificate issues, see [Enforce HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).</span></span>

## <a name="default-entitlements"></a><span data-ttu-id="fabeb-158">預設權利</span><span class="sxs-lookup"><span data-stu-id="fabeb-158">Default entitlements</span></span>

<span data-ttu-id="fabeb-159">.NET Core 的預設主機（`dotnet`命令）具有一組預設許可權。</span><span class="sxs-lookup"><span data-stu-id="fabeb-159">.NET Core’s default host (the `dotnet` command) has a set of default entitlements.</span></span> <span data-ttu-id="fabeb-160">這些權利是 .NET Core 正常運行所必需的。</span><span class="sxs-lookup"><span data-stu-id="fabeb-160">These entitlements are required for proper operation of .NET Core.</span></span> <span data-ttu-id="fabeb-161">您的應用程式可能需要其他授權，在這種情況下，您需要生成和使用[appHost，](#apphost-is-disabled-by-default)然後在本地添加必要的授權。</span><span class="sxs-lookup"><span data-stu-id="fabeb-161">It's possible that your application may need additional entitlements, in which case you'll need to generate and use an [appHost](#apphost-is-disabled-by-default) and then add the necessary entitlements locally.</span></span>

<span data-ttu-id="fabeb-162">.NET Core 的預設許可權集：</span><span class="sxs-lookup"><span data-stu-id="fabeb-162">Default set of entitlements for .NET Core:</span></span>

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a><span data-ttu-id="fabeb-163">公證 .NET 核心應用</span><span class="sxs-lookup"><span data-stu-id="fabeb-163">Notarize a .NET Core app</span></span>

<span data-ttu-id="fabeb-164">如果希望應用程式在 macOS Catalina（版本 10.15）或更高版本上運行，則需要對應用進行公證。</span><span class="sxs-lookup"><span data-stu-id="fabeb-164">If you want your application to run on macOS Catalina (version 10.15) or higher, you'll want to notarize your app.</span></span> <span data-ttu-id="fabeb-165">與應用程式一起提交的用於公證的應用Host 應至少與 .NET Core 相同的[預設許可權](#default-entitlements)一起使用。</span><span class="sxs-lookup"><span data-stu-id="fabeb-165">The appHost you submit with your application for notarization should be used with at least the same [default entitlements](#default-entitlements) for .NET Core.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fabeb-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fabeb-166">Next steps</span></span>

- <span data-ttu-id="fabeb-167">[.NET 核心依賴項和要求](dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="fabeb-167">[.NET Core dependencies and requirements](dependencies.md).</span></span>
- <span data-ttu-id="fabeb-168">[安裝 .NET 核心 SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="fabeb-168">[Install the .NET Core SDK](sdk.md).</span></span>
- [<span data-ttu-id="fabeb-169">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="fabeb-169">Install the .NET Core Runtime</span></span>](runtime.md)
