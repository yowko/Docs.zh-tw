---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394205"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="d1e8e-101">授權： AddAuthorization 多載已移至不同的元件</span><span class="sxs-lookup"><span data-stu-id="d1e8e-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="d1e8e-102">用來存放在 `Microsoft.AspNetCore.Authorization` 中的核心 `AddAuthorization` 方法已重新命名為 `AddAuthorizationCore`。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="d1e8e-103">舊的 `AddAuthorization` 方法仍然存在，但卻是在 `Microsoft.AspNetCore.Authorization.Policy` 封裝中。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` package instead.</span></span> <span data-ttu-id="d1e8e-104">使用這兩種方法的應用程式應該看不到任何影響。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="d1e8e-105">未使用原則套件的應用程式必須切換為使用 `AddAuthorizationCore`。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-105">Apps that weren't using the policy package must switch to using `AddAuthorizationCore`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d1e8e-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d1e8e-106">Version introduced</span></span>

<span data-ttu-id="d1e8e-107">3.0</span><span class="sxs-lookup"><span data-stu-id="d1e8e-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d1e8e-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d1e8e-108">Old behavior</span></span>

<span data-ttu-id="d1e8e-109">`AddAuthorization` 方法存在於 `Microsoft.AspNetCore.Authorization` 中。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d1e8e-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="d1e8e-110">New behavior</span></span>

<span data-ttu-id="d1e8e-111">`AddAuthorization` 方法存在於 `Microsoft.AspNetCore.Authorization.Policy` 中。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="d1e8e-112">`AddAuthorizationCore` 是舊方法的新名稱。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d1e8e-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d1e8e-113">Reason for change</span></span>

<span data-ttu-id="d1e8e-114">`AddAuthorization` 是新增授權所需之所有泛型服務的較佳方法名稱。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d1e8e-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d1e8e-115">Recommended action</span></span>

<span data-ttu-id="d1e8e-116">請將參考新增至 `Microsoft.AspNetCore.Authorization.Policy`，或改為使用 `AddAuthorizationCore`。</span><span class="sxs-lookup"><span data-stu-id="d1e8e-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="d1e8e-117">分類</span><span class="sxs-lookup"><span data-stu-id="d1e8e-117">Category</span></span>

<span data-ttu-id="d1e8e-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d1e8e-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1e8e-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d1e8e-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
