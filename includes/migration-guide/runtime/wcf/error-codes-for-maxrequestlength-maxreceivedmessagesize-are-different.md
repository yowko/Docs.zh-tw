---
ms.openlocfilehash: 26facb645de175d7ef0432394fc2b84f59e8437d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497549"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="b2bc7-101">maxRequestLength 或 maxReceivedMessageSize 的錯誤碼不同</span><span class="sxs-lookup"><span data-stu-id="b2bc7-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

#### <a name="details"></a><span data-ttu-id="b2bc7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b2bc7-102">Details</span></span>

<span data-ttu-id="b2bc7-103">Internet Information Services (IIS) 或 ASP.NET 程式開發伺服器裝載的 WCF Web 服務中，超過 maxRequestLength (在 ASP.NET 中) 或 maxReceivedMessageSize (在 WCF 中) 的訊息具有不同的錯誤碼。HTTP 狀態碼已從 400 (錯誤的要求) 變更為 413 (要求的實體太大)，而且超過 maxRequestLength 或 maxReceivedMessageSize 設定的訊息會擲回 <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b2bc7-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="b2bc7-104">傳輸模式為 Streamed 的案例也包括在內。</span><span class="sxs-lookup"><span data-stu-id="b2bc7-104">This includes cases in which the transfer mode is Streamed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b2bc7-105">建議</span><span class="sxs-lookup"><span data-stu-id="b2bc7-105">Suggestion</span></span>

<span data-ttu-id="b2bc7-106">這項變更有助於在訊息長度超過 ASP.NET 或 WCF 所允許之限制的情況下進行偵錯。您必須修改任何依據 HTTP 400 狀態碼執行處理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2bc7-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>

| <span data-ttu-id="b2bc7-107">名稱</span><span class="sxs-lookup"><span data-stu-id="b2bc7-107">Name</span></span>    | <span data-ttu-id="b2bc7-108">值</span><span class="sxs-lookup"><span data-stu-id="b2bc7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b2bc7-109">範圍</span><span class="sxs-lookup"><span data-stu-id="b2bc7-109">Scope</span></span>   |<span data-ttu-id="b2bc7-110">Edge</span><span class="sxs-lookup"><span data-stu-id="b2bc7-110">Edge</span></span>|
|<span data-ttu-id="b2bc7-111">版本</span><span class="sxs-lookup"><span data-stu-id="b2bc7-111">Version</span></span>|<span data-ttu-id="b2bc7-112">4.5</span><span class="sxs-lookup"><span data-stu-id="b2bc7-112">4.5</span></span>|
|<span data-ttu-id="b2bc7-113">類型</span><span class="sxs-lookup"><span data-stu-id="b2bc7-113">Type</span></span>|<span data-ttu-id="b2bc7-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="b2bc7-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b2bc7-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b2bc7-115">Affected APIs</span></span>

<span data-ttu-id="b2bc7-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="b2bc7-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
