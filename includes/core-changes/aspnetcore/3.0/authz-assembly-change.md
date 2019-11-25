---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74100760"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="bbee1-101">授權： AddAuthorization 多載已移至不同的元件</span><span class="sxs-lookup"><span data-stu-id="bbee1-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="bbee1-102">用來存放在 `Microsoft.AspNetCore.Authorization` 中的核心 `AddAuthorization` 方法已重新命名為 `AddAuthorizationCore`。</span><span class="sxs-lookup"><span data-stu-id="bbee1-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="bbee1-103">舊的 `AddAuthorization` 方法仍然存在，但卻是在 `Microsoft.AspNetCore.Authorization.Policy` 元件中。</span><span class="sxs-lookup"><span data-stu-id="bbee1-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="bbee1-104">使用這兩種方法的應用程式應該看不到任何影響。</span><span class="sxs-lookup"><span data-stu-id="bbee1-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="bbee1-105">請注意，`Microsoft.AspNetCore.Authorization.Policy` 現在隨附于共用架構中，而不是獨立套件，如[共用架構：從 AspNetCore 移除的元件](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)中所述。</span><span class="sxs-lookup"><span data-stu-id="bbee1-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bbee1-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bbee1-106">Version introduced</span></span>

<span data-ttu-id="bbee1-107">3.0</span><span class="sxs-lookup"><span data-stu-id="bbee1-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bbee1-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="bbee1-108">Old behavior</span></span>
<span data-ttu-id="bbee1-109">`AddAuthorization` 方法存在於 `Microsoft.AspNetCore.Authorization` 中。</span><span class="sxs-lookup"><span data-stu-id="bbee1-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bbee1-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="bbee1-110">New behavior</span></span>

<span data-ttu-id="bbee1-111">`AddAuthorization` 方法存在於 `Microsoft.AspNetCore.Authorization.Policy` 中。</span><span class="sxs-lookup"><span data-stu-id="bbee1-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="bbee1-112">`AddAuthorizationCore` 是舊方法的新名稱。</span><span class="sxs-lookup"><span data-stu-id="bbee1-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bbee1-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="bbee1-113">Reason for change</span></span>

<span data-ttu-id="bbee1-114">`AddAuthorization` 是新增授權所需之所有泛型服務的較佳方法名稱。</span><span class="sxs-lookup"><span data-stu-id="bbee1-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bbee1-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bbee1-115">Recommended action</span></span>

<span data-ttu-id="bbee1-116">請將參考新增至 `Microsoft.AspNetCore.Authorization.Policy`，或改為使用 `AddAuthorizationCore`。</span><span class="sxs-lookup"><span data-stu-id="bbee1-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="bbee1-117">Category</span><span class="sxs-lookup"><span data-stu-id="bbee1-117">Category</span></span>

<span data-ttu-id="bbee1-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bbee1-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bbee1-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bbee1-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
