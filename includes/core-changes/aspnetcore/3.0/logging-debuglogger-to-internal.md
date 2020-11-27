---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032388"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="b5d09-101">記錄： DebugLogger 類別設為內部</span><span class="sxs-lookup"><span data-stu-id="b5d09-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="b5d09-102">在 ASP.NET Core 3.0 之前， `DebugLogger` 的存取修飾詞是 `public` 。</span><span class="sxs-lookup"><span data-stu-id="b5d09-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="b5d09-103">在 ASP.NET Core 3.0 中，存取修飾詞變更為 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="b5d09-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b5d09-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b5d09-104">Version introduced</span></span>

<span data-ttu-id="b5d09-105">3.0</span><span class="sxs-lookup"><span data-stu-id="b5d09-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b5d09-106">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b5d09-106">Reason for change</span></span>

<span data-ttu-id="b5d09-107">正在進行變更：</span><span class="sxs-lookup"><span data-stu-id="b5d09-107">The change is being made to:</span></span>

* <span data-ttu-id="b5d09-108">強制執行與其他記錄器執行的一致性，例如 `ConsoleLogger` 。</span><span class="sxs-lookup"><span data-stu-id="b5d09-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="b5d09-109">減少 API 介面。</span><span class="sxs-lookup"><span data-stu-id="b5d09-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b5d09-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b5d09-110">Recommended action</span></span>

<span data-ttu-id="b5d09-111">使用 <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` 擴充方法來啟用 debug 記錄。</span><span class="sxs-lookup"><span data-stu-id="b5d09-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="b5d09-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> 也仍然 `public` 在事件中，必須以手動方式註冊服務。</span><span class="sxs-lookup"><span data-stu-id="b5d09-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="b5d09-113">類別</span><span class="sxs-lookup"><span data-stu-id="b5d09-113">Category</span></span>

<span data-ttu-id="b5d09-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b5d09-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5d09-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b5d09-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
