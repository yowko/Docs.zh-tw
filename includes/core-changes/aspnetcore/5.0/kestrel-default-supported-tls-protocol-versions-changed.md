---
ms.openlocfilehash: 3244a36808fb687663241e704d08775ea5c96720
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803263"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="48d44-101">Kestrel：預設支援的 TLS 通訊協定版本已變更</span><span class="sxs-lookup"><span data-stu-id="48d44-101">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="48d44-102">Kestrel 現在會使用系統預設的 TLS 通訊協定版本，而不是限制與 TLS 1.1 和 TLS 1.2 通訊協定的連線，就像之前一樣。</span><span class="sxs-lookup"><span data-stu-id="48d44-102">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="48d44-103">這種變更允許：</span><span class="sxs-lookup"><span data-stu-id="48d44-103">This change allows:</span></span>

* <span data-ttu-id="48d44-104">在支援的環境中，預設會使用 TLS 1.3。</span><span class="sxs-lookup"><span data-stu-id="48d44-104">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="48d44-105">在某些環境中使用的 TLS 1.0 （預設為 Windows Server 2016），這通常[不是理想的做法](/security/engineering/solving-tls1-problem)。</span><span class="sxs-lookup"><span data-stu-id="48d44-105">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="48d44-106">如需討論，請參閱 issue [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563)。</span><span class="sxs-lookup"><span data-stu-id="48d44-106">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="48d44-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="48d44-107">Version introduced</span></span>

<span data-ttu-id="48d44-108">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="48d44-108">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="48d44-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="48d44-109">Old behavior</span></span>

<span data-ttu-id="48d44-110">Kestrel 需要連線預設使用 TLS 1.1 或 TLS 1.2。</span><span class="sxs-lookup"><span data-stu-id="48d44-110">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="48d44-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="48d44-111">New behavior</span></span>

<span data-ttu-id="48d44-112">Kestrel 可讓作業系統選擇使用的最佳通訊協定，並封鎖不安全的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="48d44-112">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="48d44-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>現在預設為， `SslProtocols.None` 而不是 `SslProtocols.Tls12 | SslProtocols.Tls11` 。</span><span class="sxs-lookup"><span data-stu-id="48d44-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="48d44-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="48d44-114">Reason for change</span></span>

<span data-ttu-id="48d44-115">根據預設，當 TLS 1.3 和未來的 TLS 版本可供使用時，就會進行變更。</span><span class="sxs-lookup"><span data-stu-id="48d44-115">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="48d44-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="48d44-116">Recommended action</span></span>

<span data-ttu-id="48d44-117">除非您的應用程式具有不適用的特定原因，否則您應該使用新的預設值。</span><span class="sxs-lookup"><span data-stu-id="48d44-117">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="48d44-118">確認您的系統已設定為只允許安全的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="48d44-118">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="48d44-119">若要停用較舊的通訊協定，請採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="48d44-119">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="48d44-120">使用[Windows 指示](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry)停用舊版的通訊協定，例如 TLS 1.0。</span><span class="sxs-lookup"><span data-stu-id="48d44-120">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="48d44-121">它目前在所有 Windows 版本上都是預設為啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="48d44-121">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="48d44-122">手動選取您要在程式碼中支援的通訊協定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="48d44-122">Manually select which protocols you want to support in code as follows:</span></span>

    ```csharp
    using System.Security.Authentication;
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
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="48d44-123">可惜的是，沒有任何 API 可以排除特定的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="48d44-123">Unfortunately, there's no API to exclude specific protocols.</span></span>

#### <a name="category"></a><span data-ttu-id="48d44-124">類別</span><span class="sxs-lookup"><span data-stu-id="48d44-124">Category</span></span>

<span data-ttu-id="48d44-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="48d44-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="48d44-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="48d44-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
