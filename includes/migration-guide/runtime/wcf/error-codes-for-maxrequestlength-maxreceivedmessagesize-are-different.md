---
ms.openlocfilehash: c9d6111edcfeec6852f23cc0768833de32e61022
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235154"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="a276b-101">maxRequestLength 或 maxReceivedMessageSize 的錯誤碼不同</span><span class="sxs-lookup"><span data-stu-id="a276b-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a276b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a276b-102">Details</span></span>|<span data-ttu-id="a276b-103">Internet Information Services (IIS) 或 ASP.NET 程式開發伺服器裝載的 WCF Web 服務中，超過 maxRequestLength (在 ASP.NET 中) 或 maxReceivedMessageSize (在 WCF 中) 的訊息具有不同的錯誤碼。HTTP 狀態碼已從 400 (錯誤的要求) 變更為 413 (要求的實體太大)，而且超過 maxRequestLength 或 maxReceivedMessageSize 設定的訊息會擲回 <xref:System.ServiceModel.ProtocolException?displayProperty=name> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a276b-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=name> exception.</span></span> <span data-ttu-id="a276b-104">傳輸模式為 Streamed 的案例也包括在內。</span><span class="sxs-lookup"><span data-stu-id="a276b-104">This includes cases in which the transfer mode is Streamed.</span></span>|
|<span data-ttu-id="a276b-105">建議</span><span class="sxs-lookup"><span data-stu-id="a276b-105">Suggestion</span></span>|<span data-ttu-id="a276b-106">這項變更有助於在訊息長度超過 ASP.NET 或 WCF 所允許之限制的情況下進行偵錯。您必須修改任何依據 HTTP 400 狀態碼執行處理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a276b-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>|
|<span data-ttu-id="a276b-107">範圍</span><span class="sxs-lookup"><span data-stu-id="a276b-107">Scope</span></span>|<span data-ttu-id="a276b-108">Edge</span><span class="sxs-lookup"><span data-stu-id="a276b-108">Edge</span></span>|
|<span data-ttu-id="a276b-109">版本</span><span class="sxs-lookup"><span data-stu-id="a276b-109">Version</span></span>|<span data-ttu-id="a276b-110">4.5</span><span class="sxs-lookup"><span data-stu-id="a276b-110">4.5</span></span>|
|<span data-ttu-id="a276b-111">類型</span><span class="sxs-lookup"><span data-stu-id="a276b-111">Type</span></span>|<span data-ttu-id="a276b-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="a276b-112">Runtime</span></span>|
