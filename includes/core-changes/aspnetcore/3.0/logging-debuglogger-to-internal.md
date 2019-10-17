---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394395"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="b1cfe-101">記錄： DebugLogger 類別已設為內部</span><span class="sxs-lookup"><span data-stu-id="b1cfe-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="b1cfe-102">在 ASP.NET Core 3.0 之前，`DebugLogger` 的存取修飾詞已 `public`。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="b1cfe-103">在 ASP.NET Core 3.0 中，存取修飾詞已變更為 `internal`。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b1cfe-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b1cfe-104">Version introduced</span></span>

<span data-ttu-id="b1cfe-105">3.0</span><span class="sxs-lookup"><span data-stu-id="b1cfe-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b1cfe-106">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b1cfe-106">Reason for change</span></span>

<span data-ttu-id="b1cfe-107">即將進行變更：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-107">The change is being made to:</span></span>

* <span data-ttu-id="b1cfe-108">強制執行與其他記錄器的一致性，例如 `ConsoleLogger`。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="b1cfe-109">減少 API 介面。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b1cfe-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b1cfe-110">Recommended action</span></span>

<span data-ttu-id="b1cfe-111">使用 <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` 擴充方法來啟用 debug 記錄。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="b1cfe-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> 也仍然 `public` 在事件中，服務必須以手動方式註冊。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="b1cfe-113">分類</span><span class="sxs-lookup"><span data-stu-id="b1cfe-113">Category</span></span>

<span data-ttu-id="b1cfe-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1cfe-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b1cfe-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b1cfe-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
