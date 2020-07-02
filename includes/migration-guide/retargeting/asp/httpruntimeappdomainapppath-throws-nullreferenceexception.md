---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617523"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="8d99d-101">HttpRuntime.AppDomainAppPath 擲回 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="8d99d-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="8d99d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8d99d-102">Details</span></span>

<span data-ttu-id="8d99d-103">在 .NET Framework 4.6.2 中，執行階段在擷取包含 null 字元的 `P:System.Web.HttpRuntime.AppDomainAppPath` 值時，會擲回 `T:System.NullReferenceException`。在 .NET Framework 4.6.1 和更早版本中，執行階段會擲回 `T:System.ArgumentNullException`。</span><span class="sxs-lookup"><span data-stu-id="8d99d-103">In the .NET Framework 4.6.2, the runtime throws a `T:System.NullReferenceException` when retrieving a `P:System.Web.HttpRuntime.AppDomainAppPath` value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an `T:System.ArgumentNullException`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8d99d-104">建議</span><span class="sxs-lookup"><span data-stu-id="8d99d-104">Suggestion</span></span>

<span data-ttu-id="8d99d-105">您可以執行下列其中一個動作以回應這項變更︰</span><span class="sxs-lookup"><span data-stu-id="8d99d-105">You can do either of the follow to respond to this change:</span></span>

- <span data-ttu-id="8d99d-106">如果您的應用程式是在 .NET Framework 4.6.2 上執行，請處理 `T:System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="8d99d-106">Handle the `T:System.NullReferenceException` if you application is running on the .NET Framework 4.6.2.</span></span>
- <span data-ttu-id="8d99d-107">升級至 .NET Framework 4.7，這可以還原舊版行為並擲回 `T:System.ArgumentNullException`。</span><span class="sxs-lookup"><span data-stu-id="8d99d-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an `T:System.ArgumentNullException`.</span></span>

| <span data-ttu-id="8d99d-108">名稱</span><span class="sxs-lookup"><span data-stu-id="8d99d-108">Name</span></span>    | <span data-ttu-id="8d99d-109">值</span><span class="sxs-lookup"><span data-stu-id="8d99d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8d99d-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8d99d-110">Scope</span></span>   | <span data-ttu-id="8d99d-111">Edge</span><span class="sxs-lookup"><span data-stu-id="8d99d-111">Edge</span></span>        |
| <span data-ttu-id="8d99d-112">版本</span><span class="sxs-lookup"><span data-stu-id="8d99d-112">Version</span></span> | <span data-ttu-id="8d99d-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8d99d-113">4.6.2</span></span>       |
| <span data-ttu-id="8d99d-114">類型</span><span class="sxs-lookup"><span data-stu-id="8d99d-114">Type</span></span>    | <span data-ttu-id="8d99d-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8d99d-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8d99d-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8d99d-116">Affected APIs</span></span>

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
