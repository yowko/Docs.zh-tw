---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394395"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="df7bd-101">日誌記錄：調試記錄器類是內部製作的</span><span class="sxs-lookup"><span data-stu-id="df7bd-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="df7bd-102">在 ASP.NET Core 3.0 之前，`DebugLogger`訪問修改`public`器為 。</span><span class="sxs-lookup"><span data-stu-id="df7bd-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="df7bd-103">在 ASP.NET 核心 3.0 中，訪問`internal`修改器更改為 。</span><span class="sxs-lookup"><span data-stu-id="df7bd-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="df7bd-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="df7bd-104">Version introduced</span></span>

<span data-ttu-id="df7bd-105">3.0</span><span class="sxs-lookup"><span data-stu-id="df7bd-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="df7bd-106">更改原因</span><span class="sxs-lookup"><span data-stu-id="df7bd-106">Reason for change</span></span>

<span data-ttu-id="df7bd-107">正在作出以下更改：</span><span class="sxs-lookup"><span data-stu-id="df7bd-107">The change is being made to:</span></span>

* <span data-ttu-id="df7bd-108">強制與其他記錄器實現（如`ConsoleLogger`） 保持一致。</span><span class="sxs-lookup"><span data-stu-id="df7bd-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="df7bd-109">減少 API 表面。</span><span class="sxs-lookup"><span data-stu-id="df7bd-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="df7bd-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="df7bd-110">Recommended action</span></span>

<span data-ttu-id="df7bd-111"><xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder`使用擴充方法啟用調試日誌記錄。</span><span class="sxs-lookup"><span data-stu-id="df7bd-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="df7bd-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>如果服務需要`public`手動註冊，則仍處於此情況。</span><span class="sxs-lookup"><span data-stu-id="df7bd-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="df7bd-113">類別</span><span class="sxs-lookup"><span data-stu-id="df7bd-113">Category</span></span>

<span data-ttu-id="df7bd-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="df7bd-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="df7bd-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="df7bd-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
