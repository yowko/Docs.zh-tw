---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803243"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="0e824-101">Kestrel：預設偵測到執行時間的設定變更</span><span class="sxs-lookup"><span data-stu-id="0e824-101">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="0e824-102">Kestrel 現在會回應 `Kestrel` 在執行時間對專案實例之區段進行的變更 `IConfiguration` （例如， *appsettings.js*）。</span><span class="sxs-lookup"><span data-stu-id="0e824-102">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="0e824-103">若要深入瞭解如何使用*appsettings.js*來設定 Kestrel，請參閱[端點](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration)設定中的*appsettings.js*範例。</span><span class="sxs-lookup"><span data-stu-id="0e824-103">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="0e824-104">Kestrel 會視需要系結、解除系結和重新系結端點，以回應這些設定變更。</span><span class="sxs-lookup"><span data-stu-id="0e824-104">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="0e824-105">如需討論，請參閱 issue [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807)。</span><span class="sxs-lookup"><span data-stu-id="0e824-105">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e824-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0e824-106">Version introduced</span></span>

<span data-ttu-id="0e824-107">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="0e824-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0e824-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="0e824-108">Old behavior</span></span>

<span data-ttu-id="0e824-109">在 ASP.NET Core 5.0 Preview 6 之前，Kestrel 不支援在執行時間變更設定。</span><span class="sxs-lookup"><span data-stu-id="0e824-109">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="0e824-110">在 ASP.NET Core 5.0 Preview 6 中，您可以選擇在執行時間回應設定變更的立即預設行為。</span><span class="sxs-lookup"><span data-stu-id="0e824-110">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="0e824-111">手動選擇 [必要的系結 Kestrel] 設定：</span><span class="sxs-lookup"><span data-stu-id="0e824-111">Opting in required binding Kestrel's configuration manually:</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args) =>
        CreateHostBuilder(args).Build().Run();

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a><span data-ttu-id="0e824-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="0e824-112">New behavior</span></span>

<span data-ttu-id="0e824-113">Kestrel 預設會回應執行時間的設定變更。</span><span class="sxs-lookup"><span data-stu-id="0e824-113">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="0e824-114">為了支援這項變更 <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> ， `KestrelServerOptions.Configure(IConfiguration, bool)` 預設會呼叫 `reloadOnChange: true` 。</span><span class="sxs-lookup"><span data-stu-id="0e824-114">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0e824-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="0e824-115">Reason for change</span></span>

<span data-ttu-id="0e824-116">已進行變更，以支援在執行時間重新設定端點，而不需完全重新開機伺服器。</span><span class="sxs-lookup"><span data-stu-id="0e824-116">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="0e824-117">與完整伺服器重新開機不同的是，未變更的端點也不會暫時解除系結。</span><span class="sxs-lookup"><span data-stu-id="0e824-117">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e824-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0e824-118">Recommended action</span></span>

* <span data-ttu-id="0e824-119">在大多數情況下，Kestrel 的預設設定區段不會在執行時間變更，這項變更不會有任何影響，也不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="0e824-119">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="0e824-120">對於 Kestrel 的預設設定區段在執行時間變更的情況，Kestrel 應該對其做出反應，這現在是預設行為。</span><span class="sxs-lookup"><span data-stu-id="0e824-120">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="0e824-121">對於 Kestrel 的預設設定區段在執行時間變更，而 Kestrel 不應對其做出反應的案例，您可以退出宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0e824-121">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="0e824-122">**注意：**</span><span class="sxs-lookup"><span data-stu-id="0e824-122">**Notes:**</span></span>

<span data-ttu-id="0e824-123">這項變更不會修改多載的行為 `KestrelServerOptions.Configure(IConfiguration)` ，這仍然會預設為 `reloadOnChange: false` 行為。</span><span class="sxs-lookup"><span data-stu-id="0e824-123">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="0e824-124">也請務必確定設定來源支援重載。</span><span class="sxs-lookup"><span data-stu-id="0e824-124">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="0e824-125">針對 JSON 來源，重載是藉由呼叫來設定 `AddJsonFile(path, reloadOnChange: true)` 。</span><span class="sxs-lookup"><span data-stu-id="0e824-125">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="0e824-126">在和 appsettings 上，預設已針對*appsettings.js*設定重載 *。 {環境}. json*。</span><span class="sxs-lookup"><span data-stu-id="0e824-126">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

#### <a name="category"></a><span data-ttu-id="0e824-127">類別</span><span class="sxs-lookup"><span data-stu-id="0e824-127">Category</span></span>

<span data-ttu-id="0e824-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0e824-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e824-129">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0e824-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
