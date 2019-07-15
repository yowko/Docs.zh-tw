---
ms.openlocfilehash: d6c658f306dd4792e3cb5dbdc9471043ca95a071
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859089"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="3f39f-101">HttpRuntime.AppDomainAppPath 擲回 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="3f39f-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3f39f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3f39f-102">Details</span></span>|<span data-ttu-id="3f39f-103">在 .NET Framework 4.6.2 中，執行階段在擷取包含 null 字元的 <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> 值時，會擲回 <code>T:System.NullReferenceException</code>。在 .NET Framework 4.6.1 和更早版本中，執行階段會擲回 <code>T:System.ArgumentNullException</code>。</span><span class="sxs-lookup"><span data-stu-id="3f39f-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="3f39f-104">建議</span><span class="sxs-lookup"><span data-stu-id="3f39f-104">Suggestion</span></span>|<span data-ttu-id="3f39f-105">您可以執行下列其中一個動作以回應這項變更︰</span><span class="sxs-lookup"><span data-stu-id="3f39f-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="3f39f-106">如果您的應用程式是在 .NET Framework 4.6.2 上執行，請處理 <code>T:System.NullReferenceException</code>。</span><span class="sxs-lookup"><span data-stu-id="3f39f-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="3f39f-107">升級至 .NET Framework 4.7，這可以還原舊版行為並擲回 <code>T:System.ArgumentNullException</code>。</span><span class="sxs-lookup"><span data-stu-id="3f39f-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="3f39f-108">範圍</span><span class="sxs-lookup"><span data-stu-id="3f39f-108">Scope</span></span>|<span data-ttu-id="3f39f-109">Edge</span><span class="sxs-lookup"><span data-stu-id="3f39f-109">Edge</span></span>|
|<span data-ttu-id="3f39f-110">版本</span><span class="sxs-lookup"><span data-stu-id="3f39f-110">Version</span></span>|<span data-ttu-id="3f39f-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="3f39f-111">4.6.2</span></span>|
|<span data-ttu-id="3f39f-112">類型</span><span class="sxs-lookup"><span data-stu-id="3f39f-112">Type</span></span>|<span data-ttu-id="3f39f-113">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="3f39f-113">Retargeting</span></span>|
|<span data-ttu-id="3f39f-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3f39f-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

