---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615627"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a><span data-ttu-id="48c05-101">使用 Null 引數呼叫 CreateDefaultAuthorizationContext 已變更</span><span class="sxs-lookup"><span data-stu-id="48c05-101">Calling CreateDefaultAuthorizationContext with a null argument has changed</span></span>

#### <a name="details"></a><span data-ttu-id="48c05-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="48c05-102">Details</span></span>

<span data-ttu-id="48c05-103">使用 Null authorizationPolicies 引數呼叫 <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> 所傳回的 <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> 實作，已變更其在 .NET Framework 4.6 中的實作。</span><span class="sxs-lookup"><span data-stu-id="48c05-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> with a null authorizationPolicies argument has changed its implementation in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="48c05-104">建議</span><span class="sxs-lookup"><span data-stu-id="48c05-104">Suggestion</span></span>

<span data-ttu-id="48c05-105">在少數情況下，使用自訂驗證的 WCF 應用程式，在行為上可能會有些許差異。</span><span class="sxs-lookup"><span data-stu-id="48c05-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span> <span data-ttu-id="48c05-106">在此情況下，您可使用下列兩種方式之一還原舊版行為：</span><span class="sxs-lookup"><span data-stu-id="48c05-106">In such cases, the previous behavior can be restored in either of two ways:</span></span>

- <span data-ttu-id="48c05-107">以 .NET Framework 4.6 之前的舊版為目標，重新編譯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="48c05-107">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="48c05-108">對於裝載在 IIS 上的服務，請使用 `<httpRuntime targetFramework="x.x">` 項目，將目標設為舊版 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="48c05-108">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x">` element to target an earlier version of the .NET Framework.</span></span>
- <span data-ttu-id="48c05-109">將下列行加入 app.config 檔案中的 `<appSettings>` 區段：</span><span class="sxs-lookup"><span data-stu-id="48c05-109">Add the following line to the `<appSettings>` section of your app.config file:</span></span>

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| <span data-ttu-id="48c05-110">名稱</span><span class="sxs-lookup"><span data-stu-id="48c05-110">Name</span></span>    | <span data-ttu-id="48c05-111">值</span><span class="sxs-lookup"><span data-stu-id="48c05-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="48c05-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="48c05-112">Scope</span></span>   | <span data-ttu-id="48c05-113">Minor</span><span class="sxs-lookup"><span data-stu-id="48c05-113">Minor</span></span>       |
| <span data-ttu-id="48c05-114">版本</span><span class="sxs-lookup"><span data-stu-id="48c05-114">Version</span></span> | <span data-ttu-id="48c05-115">4.6</span><span class="sxs-lookup"><span data-stu-id="48c05-115">4.6</span></span>         |
| <span data-ttu-id="48c05-116">類型</span><span class="sxs-lookup"><span data-stu-id="48c05-116">Type</span></span>    | <span data-ttu-id="48c05-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="48c05-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="48c05-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="48c05-118">Affected APIs</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
