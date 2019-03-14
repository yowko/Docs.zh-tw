---
title: .NET Core 2.2 的新功能
description: 了解 .NET Core 2.2 所提供的新功能。
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 12/04/2018
ms.openlocfilehash: 49a65dd44159e9800f7cf50a1edaa3d9e9b82e47
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677262"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="77cd9-103">.NET Core 2.2 的新功能</span><span class="sxs-lookup"><span data-stu-id="77cd9-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="77cd9-104">.NET Core 2.2 包括應用程式部署、執行階段服務的事件處理、對 Azure SQL 資料庫的驗證、JIT 編譯器效能及執行 `Main` 方法前的程式碼插入等方面的增強功能。</span><span class="sxs-lookup"><span data-stu-id="77cd9-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="77cd9-105">新的部署模式</span><span class="sxs-lookup"><span data-stu-id="77cd9-105">New deployment mode</span></span>

<span data-ttu-id="77cd9-106">從 .NET Core 2.2 開始，您可以部署[架構相依可執行檔](../deploying/index.md#framework-dependent-executables-fde)，也就是 **.exe** 檔案，而不是 **.dll** 檔案。</span><span class="sxs-lookup"><span data-stu-id="77cd9-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="77cd9-107">架構相依可執行檔 (FDE) 在功能上與架構相依部署類似，仍然必須要有共用的全系統 .NET Core 版本才能執行。</span><span class="sxs-lookup"><span data-stu-id="77cd9-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="77cd9-108">您的應用程式只包含您的程式碼及任何協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="77cd9-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="77cd9-109">與架構相依部署不同，FDE 是平台特定的。</span><span class="sxs-lookup"><span data-stu-id="77cd9-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="77cd9-110">這個新部署模式的獨特優點是會建置可執行檔而非程式庫，這意謂著您可以直接執行您的應用程式，而無須先叫用 `dotnet`。</span><span class="sxs-lookup"><span data-stu-id="77cd9-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="77cd9-111">核心</span><span class="sxs-lookup"><span data-stu-id="77cd9-111">Core</span></span>

<span data-ttu-id="77cd9-112">**處理執行階段服務中的事件**</span><span class="sxs-lookup"><span data-stu-id="77cd9-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="77cd9-113">您可能常常會想要監視應用程式的執行階段服務使用情況 (例如 GC、JIT 及 ThreadPool)，以了解這些服務對您應用程式的影響。</span><span class="sxs-lookup"><span data-stu-id="77cd9-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="77cd9-114"> 在 Windows 系統上，通常是藉由監視目前程序的 ETW 事件來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="77cd9-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="77cd9-115"> 雖然此方法持續行得通，但如果您是在低權限環境或是在 Linux 或 macOS 中執行，則未必總是能夠使用 ETW。</span><span class="sxs-lookup"><span data-stu-id="77cd9-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span> 

<span data-ttu-id="77cd9-116">從 .NET Core 2.2 開始，現在已可使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> 類別來取用 CoreCLR 事件。</span><span class="sxs-lookup"><span data-stu-id="77cd9-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="77cd9-117">這些事件將這類執行階段服務的行為描述為 GC、JIT、ThreadPool 及 Interop。</span><span class="sxs-lookup"><span data-stu-id="77cd9-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="77cd9-118">這些是作為 CoreCLR ETW 提供者之一部分公開的相同事件。</span><span class="sxs-lookup"><span data-stu-id="77cd9-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="77cd9-119">  這可讓應用程式取用這些事件，或使用傳輸機制將事件傳送給遙測彙總服務。</span><span class="sxs-lookup"><span data-stu-id="77cd9-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="77cd9-120">您可以從下列程式碼範例了解如何訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="77cd9-120">You can see how to subscribe to events in the following code sample:</span></span>

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

<span data-ttu-id="77cd9-121">此外，.NET Core 2.2 還將下列兩個屬性新增至 <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> 類別，以提供有關 ETW 事件的額外資訊：</span><span class="sxs-lookup"><span data-stu-id="77cd9-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="77cd9-122">資料</span><span class="sxs-lookup"><span data-stu-id="77cd9-122">Data</span></span>

<span data-ttu-id="77cd9-123">**使用 SqlConnection.AccessToken 屬性向 Azure SQL 資料庫進行 AAD 驗證**</span><span class="sxs-lookup"><span data-stu-id="77cd9-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="77cd9-124">從 .NET Core 2.2 開始，Azure Active Directory 簽發的存取權杖可用來向 Azure SQL 資料庫進行驗證。</span><span class="sxs-lookup"><span data-stu-id="77cd9-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="77cd9-125">為了支援存取權杖，已將 <xref:System.Data.SqlClient.SqlConnection.AccessToken> 屬性新增至 <xref:System.Data.SqlClient.SqlConnection> 類別。</span><span class="sxs-lookup"><span data-stu-id="77cd9-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="77cd9-126">若要利用 AAD 驗證，請下載 4.6 版 System.Data.SqlClient NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="77cd9-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="77cd9-127">為了使用此功能，您可以使用 [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet 套件中所含的[適用於 .NET 的 Active Directory 驗證程式庫](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)來取得存取權杖值。</span><span class="sxs-lookup"><span data-stu-id="77cd9-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="77cd9-128">JIT 編譯器的改進項目</span><span class="sxs-lookup"><span data-stu-id="77cd9-128">JIT compiler improvements</span></span>

<span data-ttu-id="77cd9-129">**階層式編譯仍然是可選擇加入的功能**</span><span class="sxs-lookup"><span data-stu-id="77cd9-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="77cd9-130">在 .NET Core 2.1 中，JIT 編譯器已實作「階層式編譯」這個新編譯器技術作為可選擇加入的功能。</span><span class="sxs-lookup"><span data-stu-id="77cd9-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="77cd9-131">階層式編譯的目標是要提升效能。</span><span class="sxs-lookup"><span data-stu-id="77cd9-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="77cd9-132">由 JIT 編譯器所執行的其中一個重要工作，是將程式碼的執行最佳化。</span><span class="sxs-lookup"><span data-stu-id="77cd9-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="77cd9-133">不過，針對很少使用的程式碼路徑，編譯器將程式碼最佳化的時間，可能會比執行階段執行未最佳化程式碼的時間還要久。</span><span class="sxs-lookup"><span data-stu-id="77cd9-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="77cd9-134">階層式編譯會在 JIT 編譯中引入兩個階段：</span><span class="sxs-lookup"><span data-stu-id="77cd9-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="77cd9-135">**第一層**：盡快產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="77cd9-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="77cd9-136">**第二層**：針對那些經常執行的方法產生最佳化的程式碼。</span><span class="sxs-lookup"><span data-stu-id="77cd9-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="77cd9-137">編譯的第二層會以平行方式執行以增強效能。</span><span class="sxs-lookup"><span data-stu-id="77cd9-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="77cd9-138">如需了解階層式編譯所能產生的效能改進，請參閱[宣布推出 .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="77cd9-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="77cd9-139">在 .NET Core 2.2 Preview 2 中，階層式編譯是預設啟用的功能。</span><span class="sxs-lookup"><span data-stu-id="77cd9-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="77cd9-140">不過，我們已判定我們尚未做好預設啟用階層式編譯的準備。</span><span class="sxs-lookup"><span data-stu-id="77cd9-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="77cd9-141">因此，在 .NET Core 2.2 中，階層式編譯仍繼續維持為可選擇加入的功能。</span><span class="sxs-lookup"><span data-stu-id="77cd9-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="77cd9-142">如需有關如何選擇加入階層式編譯的資訊，請參閱 [.NET Core 2.1 的新功能](dotnet-core-2-1.md)中的 [Jit 編譯器的改進項目](dotnet-core-2-1.md#jit-compiler-improvements)。</span><span class="sxs-lookup"><span data-stu-id="77cd9-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="77cd9-143">執行階段</span><span class="sxs-lookup"><span data-stu-id="77cd9-143">Runtime</span></span>

<span data-ttu-id="77cd9-144">**在執行 Main 方法前插入程式碼**</span><span class="sxs-lookup"><span data-stu-id="77cd9-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="77cd9-145">從 .NET Core 2.2 開始，您可以使用啟動勾點，在執行應用程式的 Main 方法前插入程式碼。</span><span class="sxs-lookup"><span data-stu-id="77cd9-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="77cd9-146">啟動勾點可讓主機在部署應用程式之後，自訂應用程式的行為，而無須重新編譯或變更應用程式。</span><span class="sxs-lookup"><span data-stu-id="77cd9-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="77cd9-147">我們預期主機服務提供者會定義自訂設定和原則，包括可能影響主要進入點載入行為的設定，例如 <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> 行為。</span><span class="sxs-lookup"><span data-stu-id="77cd9-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="77cd9-148">勾點可用來設定追蹤功能或遙測的插入、設定用於處理的回呼，或定義其他環境相依行為。</span><span class="sxs-lookup"><span data-stu-id="77cd9-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="77cd9-149">勾點與進入點是分開的，因此無須修改使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="77cd9-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="77cd9-150">如需詳細資訊，請參閱[主機啟動勾點](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="77cd9-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="77cd9-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77cd9-151">See also</span></span>

- [<span data-ttu-id="77cd9-152">.NET Core 的新功能</span><span class="sxs-lookup"><span data-stu-id="77cd9-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="77cd9-153">ASP.NET Core 2.2 的新功能</span><span class="sxs-lookup"><span data-stu-id="77cd9-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="77cd9-154">EF Core 2.2 中的新功能</span><span class="sxs-lookup"><span data-stu-id="77cd9-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
