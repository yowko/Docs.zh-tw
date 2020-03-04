---
title: 使用 macOS Catalina Notarization
description: 當您安裝使用 .NET Core 建立的 .NET Core 執行時間、SDK 和應用程式時，如何處理 macOS 的 notarization 和憑證問題。
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: b16ef4074f829246df0aedebf7ffe4df75faed51
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78165362"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a><span data-ttu-id="73727-103">macOS Catalina Notarization 和對 .NET Core 下載和專案的影響</span><span class="sxs-lookup"><span data-stu-id="73727-103">macOS Catalina Notarization and the impact on .NET Core downloads and projects</span></span>

<span data-ttu-id="73727-104">從 macOS Catalina （版本10.15）開始，在2019年6月1日之後建立的所有軟體，以及以開發人員識別碼發佈之後，都必須是公證。</span><span class="sxs-lookup"><span data-stu-id="73727-104">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019, and distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="73727-105">這項需求適用于 .NET core 執行時間、.NET Core SDK 和使用 .NET Core 所建立的軟體。</span><span class="sxs-lookup"><span data-stu-id="73727-105">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span> <span data-ttu-id="73727-106">本文說明您在 .NET Core 和 macOS notarization 中可能會面臨的常見案例。</span><span class="sxs-lookup"><span data-stu-id="73727-106">This article describes the common scenarios you may face with .NET Core and macOS notarization.</span></span>

## <a name="installing-net-core"></a><span data-ttu-id="73727-107">安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="73727-107">Installing .NET Core</span></span>

<span data-ttu-id="73727-108">從2020年2月18日起，已公證 .NET Core （執行時間和 SDK）版本3.1、3.0 和2.1 的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="73727-108">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="73727-109">先前發行的版本不會公證。</span><span class="sxs-lookup"><span data-stu-id="73727-109">Prior released versions aren't notarized.</span></span> <span data-ttu-id="73727-110">您可以手動安裝非公證版本的 .NET Core，方法是先下載安裝程式，然後使用 `sudo installer` 命令。</span><span class="sxs-lookup"><span data-stu-id="73727-110">You can manually install a non-notarized version of .NET Core by first downloading the installer, and then using the `sudo installer` command.</span></span> <span data-ttu-id="73727-111">如需詳細資訊，請參閱[下載並手動安裝 macOS](sdk.md?pivots=os-macos#download-and-manually-install)。</span><span class="sxs-lookup"><span data-stu-id="73727-111">For more information, see [Download and manually install for macOS](sdk.md?pivots=os-macos#download-and-manually-install).</span></span>

<span data-ttu-id="73727-112">從下列版本開始，會公證 .NET Core 安裝程式：</span><span class="sxs-lookup"><span data-stu-id="73727-112">Beginning with the following versions, the .NET Core installers are notarized:</span></span>

- <span data-ttu-id="73727-113">.NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="73727-113">.NET Core Runtime</span></span>
  - <span data-ttu-id="73727-114">2.1.16</span><span class="sxs-lookup"><span data-stu-id="73727-114">2.1.16</span></span>
  - <span data-ttu-id="73727-115">3.0.3</span><span class="sxs-lookup"><span data-stu-id="73727-115">3.0.3</span></span>
  - <span data-ttu-id="73727-116">3.1.2</span><span class="sxs-lookup"><span data-stu-id="73727-116">3.1.2</span></span>

- <span data-ttu-id="73727-117">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="73727-117">.NET Core SDK</span></span>
  - <span data-ttu-id="73727-118">2.1.512</span><span class="sxs-lookup"><span data-stu-id="73727-118">2.1.512</span></span>
  - <span data-ttu-id="73727-119">3.0.103</span><span class="sxs-lookup"><span data-stu-id="73727-119">3.0.103</span></span>
  - <span data-ttu-id="73727-120">3.1.102</span><span class="sxs-lookup"><span data-stu-id="73727-120">3.1.102</span></span>

## <a name="apphost-is-disabled-by-default"></a><span data-ttu-id="73727-121">appHost 預設為停用</span><span class="sxs-lookup"><span data-stu-id="73727-121">appHost is disabled by default</span></span>

<span data-ttu-id="73727-122">根據預設，當您的專案編譯、發行或執行時，不公證的 .NET Core SDK 3.0 和更新版本會產生原生符合-O 可執行檔（稱為**appHost**）。</span><span class="sxs-lookup"><span data-stu-id="73727-122">By default, non-notarized versions of the .NET Core SDK 3.0 and above produce a native Mach-O executable (known as the **appHost**) when your project compiles, publishes, or is run.</span></span> <span data-ttu-id="73727-123">這個可執行檔是執行應用程式的便利方式。</span><span class="sxs-lookup"><span data-stu-id="73727-123">This executable is a convenient way to run your app.</span></span> <span data-ttu-id="73727-124">否則，您必須藉由執行 `dotnet <filename.dll>`來啟動您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="73727-124">Otherwise, your app must be started by running `dotnet <filename.dll>`.</span></span> <span data-ttu-id="73727-125">當 appHost 啟用時，會在 appHost 的內容中叫用 `dotnet run` 命令。</span><span class="sxs-lookup"><span data-stu-id="73727-125">When the appHost is enabled, the `dotnet run` command is invoked in the context of the appHost.</span></span> <span data-ttu-id="73727-126">如需詳細資訊，請參閱[appHost 的內容](#context-of-the-apphost)。</span><span class="sxs-lookup"><span data-stu-id="73727-126">For more information, see [Context of the appHost](#context-of-the-apphost).</span></span>

<span data-ttu-id="73727-127">從 .NET Core SDK 3.0 和更新版本的公證版開始，appHost 可執行檔預設不會產生。</span><span class="sxs-lookup"><span data-stu-id="73727-127">Starting with the notarized versions of the .NET Core SDK 3.0 and above, the appHost executable isn't generated by default.</span></span> <span data-ttu-id="73727-128">您可以使用專案檔中的[`UseAppHost`](../project-sdk/msbuild-props.md#useapphost)布林值設定來開啟 appHost 產生。</span><span class="sxs-lookup"><span data-stu-id="73727-128">You can turn on appHost generation with the [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) boolean setting in the project file.</span></span> <span data-ttu-id="73727-129">您也可以在命令列上，使用 `-p:UseAppHost` 參數，針對您執行的特定 `dotnet` 命令切換 appHost：</span><span class="sxs-lookup"><span data-stu-id="73727-129">You can also toggle the appHost with the `-p:UseAppHost` parameter on the command line for the specific `dotnet` command you run:</span></span>

- <span data-ttu-id="73727-130">專案檔</span><span class="sxs-lookup"><span data-stu-id="73727-130">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="73727-131">命令列參數</span><span class="sxs-lookup"><span data-stu-id="73727-131">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="73727-132">當您發佈[獨立](../deploying/index.md#publish-self-contained)應用程式時，一律會建立 appHost。</span><span class="sxs-lookup"><span data-stu-id="73727-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="73727-133">如需 `UseAppHost` 設定的詳細資訊，請參閱[適用于 MICROSOFT .net 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。</span><span class="sxs-lookup"><span data-stu-id="73727-133">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="context-of-the-apphost"></a><span data-ttu-id="73727-134">AppHost 的內容</span><span class="sxs-lookup"><span data-stu-id="73727-134">Context of the appHost</span></span>

<span data-ttu-id="73727-135">當您的專案中已啟用 appHost，而且您使用 `dotnet run` 命令來執行應用程式時，會在 appHost 的內容中叫用應用程式，而不是在預設主機上叫用（預設主機是 `dotnet` 命令）。</span><span class="sxs-lookup"><span data-stu-id="73727-135">When the appHost is enabled in your project, and you use the `dotnet run` command to run your app, the app is invoked in the context of the appHost and not the default host (the default host is the `dotnet` command).</span></span> <span data-ttu-id="73727-136">如果您的專案中已停用 appHost，`dotnet run` 命令會在預設主機的內容中執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="73727-136">If the appHost is disabled in your project, the `dotnet run` command runs your app in the context of the default host.</span></span> <span data-ttu-id="73727-137">即使已停用 appHost，以獨立式形式發佈應用程式也會產生 appHost 可執行檔，而使用者會使用該可執行檔來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="73727-137">Even if the appHost is disabled, publishing your app as self-contained generates an appHost executable, and users use that executable to run your app.</span></span> <span data-ttu-id="73727-138">使用 `dotnet <filename.dll>` 執行您的應用程式時，會使用預設主機（共用執行時間）叫用應用程式。</span><span class="sxs-lookup"><span data-stu-id="73727-138">Running your app with `dotnet <filename.dll>` invokes the app with the default host, the shared runtime.</span></span>

<span data-ttu-id="73727-139">叫用使用 appHost 的應用程式時，應用程式所存取的憑證分割區與公證預設主機不同。</span><span class="sxs-lookup"><span data-stu-id="73727-139">When an app using the appHost is invoked, the certificate partition accessed by the app is different from the notarized default host.</span></span> <span data-ttu-id="73727-140">如果您的應用程式必須存取透過預設主機安裝的憑證，請使用 `dotnet run` 命令從其專案檔執行您的應用程式，或使用 `dotnet <filename.dll>` 命令直接啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="73727-140">If your app must access the certificates installed through the default host, use the `dotnet run` command to run your app from its project file, or use the `dotnet <filename.dll>` command to start the app directly.</span></span>

<span data-ttu-id="73727-141">如需此案例的詳細資訊，請[ASP.NET Core 和 macOS 和憑證](#aspnet-core-and-macos-and-certificates)一節中提供。</span><span class="sxs-lookup"><span data-stu-id="73727-141">More information about this scenario is provided in the [ASP.NET Core and macOS and certificates](#aspnet-core-and-macos-and-certificates) section.</span></span>

## <a name="aspnet-core-and-macos-and-certificates"></a><span data-ttu-id="73727-142">ASP.NET Core 和 macOS 和憑證</span><span class="sxs-lookup"><span data-stu-id="73727-142">ASP.NET Core and macOS and certificates</span></span>

<span data-ttu-id="73727-143">.NET Core 提供使用 <xref:System.Security.Cryptography.X509Certificates> 類別來管理 macOS Keychain 中憑證的功能。</span><span class="sxs-lookup"><span data-stu-id="73727-143">.NET Core provides the ability to manage certificates in the macOS Keychain with the <xref:System.Security.Cryptography.X509Certificates> class.</span></span> <span data-ttu-id="73727-144">在決定要考慮哪一個分割區時，存取 macOS Keychain 會使用應用程式身分識別做為主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="73727-144">Access to the macOS Keychain uses the applications identity as the primary key when deciding which partition to consider.</span></span> <span data-ttu-id="73727-145">例如，未簽署的應用程式會在不帶正負號的磁碟分割中儲存秘密，但已簽署的應用程式只會將其秘密儲存在資料分割</span><span class="sxs-lookup"><span data-stu-id="73727-145">For example, unsigned applications store secrets in the unsigned partition, but signed applications store their secrets in partitions only they can access.</span></span> <span data-ttu-id="73727-146">叫用您的應用程式的執行來源會決定要使用的資料分割。</span><span class="sxs-lookup"><span data-stu-id="73727-146">The source of execution that invokes your app decides which partition to use.</span></span>

<span data-ttu-id="73727-147">.NET Core 提供三個執行來源： [appHost](#apphost-is-disabled-by-default)、預設主機（`dotnet` 命令）和自訂主機。</span><span class="sxs-lookup"><span data-stu-id="73727-147">.NET Core provides three sources of execution: [appHost](#apphost-is-disabled-by-default), default host (the `dotnet` command), and a custom host.</span></span> <span data-ttu-id="73727-148">每個執行模型可能會有不同的身分識別（帶正負號或不帶正負號），並可存取 Keychain 內的不同分割區。</span><span class="sxs-lookup"><span data-stu-id="73727-148">Each execution model may have different identities, either signed or unsigned, and has access to different partitions within the Keychain.</span></span> <span data-ttu-id="73727-149">一種模式匯入的憑證可能無法從另一種方式存取。</span><span class="sxs-lookup"><span data-stu-id="73727-149">Certificates imported by one mode may not be accessible from another.</span></span> <span data-ttu-id="73727-150">例如，公證版本的 .NET Core 具有已簽署的預設主控制項。</span><span class="sxs-lookup"><span data-stu-id="73727-150">For example, the notarized versions of .NET Core have a default host that is signed.</span></span> <span data-ttu-id="73727-151">憑證會根據其身分識別匯入到安全的磁碟分割中。</span><span class="sxs-lookup"><span data-stu-id="73727-151">Certificates are imported into a secure partition based on its identity.</span></span> <span data-ttu-id="73727-152">因為 appHost 不帶正負號，所以無法從產生的 appHost 存取這些憑證。</span><span class="sxs-lookup"><span data-stu-id="73727-152">These certificates aren't accessible from a generated appHost, as the appHost is unsigned.</span></span>

<span data-ttu-id="73727-153">另一個範例是，ASP.NET Core 預設會透過預設主機匯入預設的 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="73727-153">Another example, by default, ASP.NET Core imports a default SSL certificate through the default host.</span></span> <span data-ttu-id="73727-154">ASP.NET Core 使用 appHost 的應用程式不會有此憑證的存取權，而且當 .NET Core 偵測到無法存取憑證時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="73727-154">ASP.NET Core applications that use an appHost won't have access to this certificate and will receive an error when .NET Core detects the certificate isn't accessible.</span></span> <span data-ttu-id="73727-155">錯誤訊息提供如何修正此問題的指示。</span><span class="sxs-lookup"><span data-stu-id="73727-155">The error message provides instructions on how to fix this problem.</span></span>

<span data-ttu-id="73727-156">如果需要共用憑證，macOS 會提供 `security` 公用程式的設定選項。</span><span class="sxs-lookup"><span data-stu-id="73727-156">If certificate sharing is required, macOS provides configuration options with the `security` utility.</span></span>

<span data-ttu-id="73727-157">如需有關如何針對 ASP.NET Core 憑證問題進行疑難排解的詳細資訊，請參閱[在 ASP.NET Core 中強制執行 HTTPS](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems)。</span><span class="sxs-lookup"><span data-stu-id="73727-157">For more information on how to troubleshoot ASP.NET Core certificate issues, see [Enforce HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).</span></span>

## <a name="default-entitlements"></a><span data-ttu-id="73727-158">預設權利</span><span class="sxs-lookup"><span data-stu-id="73727-158">Default entitlements</span></span>

<span data-ttu-id="73727-159">.NET Core 的預設主機（`dotnet` 命令）具有一組預設權利。</span><span class="sxs-lookup"><span data-stu-id="73727-159">.NET Core’s default host (the `dotnet` command) has a set of default entitlements.</span></span> <span data-ttu-id="73727-160">需要這些權利，才能正常運作 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="73727-160">These entitlements are required for proper operation of .NET Core.</span></span> <span data-ttu-id="73727-161">您的應用程式可能需要額外的權利，在此情況下，您必須產生並使用[appHost](#apphost-is-disabled-by-default) ，然後在本機新增必要的權利。</span><span class="sxs-lookup"><span data-stu-id="73727-161">It's possible that your application may need additional entitlements, in which case you'll need to generate and use an [appHost](#apphost-is-disabled-by-default) and then add the necessary entitlements locally.</span></span>
 
<span data-ttu-id="73727-162">.NET Core 的預設權利集：</span><span class="sxs-lookup"><span data-stu-id="73727-162">Default set of entitlements for .NET Core:</span></span>

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a><span data-ttu-id="73727-163">Notarize .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="73727-163">Notarize a .NET Core app</span></span>

<span data-ttu-id="73727-164">如果您想要讓應用程式在 macOS Catalina （10.15 版）或更新版本上執行，您會想要 notarize 您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="73727-164">If you want your application to run on macOS Catalina (version 10.15) or higher, you'll want to notarize your app.</span></span> <span data-ttu-id="73727-165">您使用應用程式進行 notarization 所提交的 appHost，應至少與 .NET Core 的相同[預設權利](#default-entitlements)搭配使用。</span><span class="sxs-lookup"><span data-stu-id="73727-165">The appHost you submit with your application for notarization should be used with at least the same [default entitlements](#default-entitlements) for .NET Core.</span></span>

## <a name="next-steps"></a><span data-ttu-id="73727-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="73727-166">Next steps</span></span>

- <span data-ttu-id="73727-167">[.Net Core 相依性和需求](dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="73727-167">[.NET Core dependencies and requirements](dependencies.md).</span></span>
- <span data-ttu-id="73727-168">[安裝 .NET Core SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="73727-168">[Install the .NET Core SDK](sdk.md).</span></span>
- [<span data-ttu-id="73727-169">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="73727-169">Install the .NET Core Runtime</span></span>](runtime.md)
