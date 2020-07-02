---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614324"
---
### <a name="calls-to-claimsidentity-constructors"></a><span data-ttu-id="4b063-101">呼叫 ClaimsIdentity 建構函式</span><span class="sxs-lookup"><span data-stu-id="4b063-101">Calls to ClaimsIdentity constructors</span></span>

#### <a name="details"></a><span data-ttu-id="4b063-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4b063-102">Details</span></span>

<span data-ttu-id="4b063-103">從 .NET Framework 4.6.2 開始，具有 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 參數的 <xref:System.Security.Claims.ClaimsIdentity> 建構函式如何設定 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性的方法有變更。</span><span class="sxs-lookup"><span data-stu-id="4b063-103">Starting with the .NET Framework 4.6.2, there is a change in how <xref:System.Security.Claims.ClaimsIdentity> constructors with an <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parameter set the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property.</span></span> <span data-ttu-id="4b063-104">如果 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 引數是 <xref:System.Security.Claims.ClaimsIdentity> 物件，而且該 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性不是 `null`，則會使用 <xref:System.Security.Claims.ClaimsIdentity.Clone> 方法來附加 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4b063-104">If the <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone> method.</span></span> <span data-ttu-id="4b063-105">在 Framework 4.6.1 和更早版本中，<xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性會附加作為現有的參考。由於此項變更，從 .NET Framework 4.6.2 開始，新 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性便不等於建構函式之 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 引數的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4b063-105">In the Framework 4.6.1 and earlier versions, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached as an existing reference.Because of this change, starting with the .NET Framework 4.6.2, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument.</span></span> <span data-ttu-id="4b063-106">在 .NET Framework 4.6.1 和更早版本中，它是相等的。</span><span class="sxs-lookup"><span data-stu-id="4b063-106">In the .NET Framework 4.6.1 and earlier versions, it is equal.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4b063-107">建議</span><span class="sxs-lookup"><span data-stu-id="4b063-107">Suggestion</span></span>

<span data-ttu-id="4b063-108">如果不想要這種行為，您可以將應用程式組態檔中的 `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` 參數設為 `true` 來還原舊版行為。</span><span class="sxs-lookup"><span data-stu-id="4b063-108">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="4b063-109">您會需要將下列內容新增至 web.config 檔案的 `<runtime>` 區段︰</span><span class="sxs-lookup"><span data-stu-id="4b063-109">This requires that you add the following to the `<runtime>` section of your web.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="4b063-110">名稱</span><span class="sxs-lookup"><span data-stu-id="4b063-110">Name</span></span>    | <span data-ttu-id="4b063-111">值</span><span class="sxs-lookup"><span data-stu-id="4b063-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4b063-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="4b063-112">Scope</span></span>   | <span data-ttu-id="4b063-113">Edge</span><span class="sxs-lookup"><span data-stu-id="4b063-113">Edge</span></span>        |
| <span data-ttu-id="4b063-114">版本</span><span class="sxs-lookup"><span data-stu-id="4b063-114">Version</span></span> | <span data-ttu-id="4b063-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="4b063-115">4.6.2</span></span>       |
| <span data-ttu-id="4b063-116">類型</span><span class="sxs-lookup"><span data-stu-id="4b063-116">Type</span></span>    | <span data-ttu-id="4b063-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="4b063-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4b063-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4b063-118">Affected APIs</span></span>

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
