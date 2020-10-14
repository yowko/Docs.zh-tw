---
ms.openlocfilehash: 16994e9cd97b31a30c8c5ce49d2042ff79b3f60b
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050508"
---
### <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="59309-101">NegotiateStream 和 SslStream 允許連續的開始作業</span><span class="sxs-lookup"><span data-stu-id="59309-101">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="59309-102">安全性資料流程的錯誤案例會以不同方式處理，而後續對或的呼叫 `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` 可能不會再失敗。</span><span class="sxs-lookup"><span data-stu-id="59309-102">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59309-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="59309-103">Version introduced</span></span>

<span data-ttu-id="59309-104">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="59309-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="59309-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="59309-105">Change description</span></span>

<span data-ttu-id="59309-106">在舊版的 .NET 版本中，呼叫 `BeginAuthenticateAsServer` 或 `BeginAuthenticateAsClient` 連續，但不先呼叫 `EndAuthenticateAsServer` 或會 `EndAuthenticateAsClient` 產生 <xref:System.NotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="59309-106">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="59309-107">從 .NET 5.0 開始，後續的呼叫 `BeginAuthenticateAsServer` 或 `BeginAuthenticateAsClient` 不再產生 <xref:System.NotSupportedException> ，因為這些 api 是由型的執行所支援的 <xref:System.Threading.Tasks.Task> 。</span><span class="sxs-lookup"><span data-stu-id="59309-107">Starting in .NET 5.0, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="59309-108">變更的原因</span><span class="sxs-lookup"><span data-stu-id="59309-108">Reason for change</span></span>

<span data-ttu-id="59309-109">從非同步程式設計模型切換內部實 (APM) 轉換為 <xref:System.Threading.Tasks.Task> 基礎，可改善效能並降低程式碼的複雜度。</span><span class="sxs-lookup"><span data-stu-id="59309-109">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59309-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="59309-110">Recommended action</span></span>

<span data-ttu-id="59309-111">開發人員不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="59309-111">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="59309-112">類別</span><span class="sxs-lookup"><span data-stu-id="59309-112">Category</span></span>

<span data-ttu-id="59309-113">網路</span><span class="sxs-lookup"><span data-stu-id="59309-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59309-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="59309-114">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

-->
