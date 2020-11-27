---
ms.openlocfilehash: 2819fb3857fa6d40a2b2e42eeaec2d9c6e50eef0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96299349"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="01ae3-101">授權： AddAuthorization 多載移至不同的元件</span><span class="sxs-lookup"><span data-stu-id="01ae3-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="01ae3-102">`AddAuthorization`用來存放的核心方法已重新 `Microsoft.AspNetCore.Authorization` 命名為 `AddAuthorizationCore` 。</span><span class="sxs-lookup"><span data-stu-id="01ae3-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="01ae3-103">舊 `AddAuthorization` 方法仍存在，但仍在元件中 `Microsoft.AspNetCore.Authorization.Policy` 。</span><span class="sxs-lookup"><span data-stu-id="01ae3-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="01ae3-104">使用這兩種方法的應用程式應該看不到任何影響。</span><span class="sxs-lookup"><span data-stu-id="01ae3-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="01ae3-105">請注意， `Microsoft.AspNetCore.Authorization.Policy` 現在會隨附于共用架構，而不是獨立套件，如共用架構中所討論 [：從 AspNetCore 移除的元件](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)。</span><span class="sxs-lookup"><span data-stu-id="01ae3-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01ae3-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="01ae3-106">Version introduced</span></span>

<span data-ttu-id="01ae3-107">3.0</span><span class="sxs-lookup"><span data-stu-id="01ae3-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="01ae3-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="01ae3-108">Old behavior</span></span>

<span data-ttu-id="01ae3-109">`AddAuthorization` 方法存在於中 `Microsoft.AspNetCore.Authorization` 。</span><span class="sxs-lookup"><span data-stu-id="01ae3-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="01ae3-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="01ae3-110">New behavior</span></span>

<span data-ttu-id="01ae3-111">`AddAuthorization` 方法存在於中 `Microsoft.AspNetCore.Authorization.Policy` 。</span><span class="sxs-lookup"><span data-stu-id="01ae3-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="01ae3-112">`AddAuthorizationCore` 這是舊方法的新名稱。</span><span class="sxs-lookup"><span data-stu-id="01ae3-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="01ae3-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="01ae3-113">Reason for change</span></span>

<span data-ttu-id="01ae3-114">`AddAuthorization` 是更好的方法名稱，可新增授權所需的所有一般服務。</span><span class="sxs-lookup"><span data-stu-id="01ae3-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01ae3-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="01ae3-115">Recommended action</span></span>

<span data-ttu-id="01ae3-116">請改為加入 `Microsoft.AspNetCore.Authorization.Policy` 或使用的參考 `AddAuthorizationCore` 。</span><span class="sxs-lookup"><span data-stu-id="01ae3-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="01ae3-117">類別</span><span class="sxs-lookup"><span data-stu-id="01ae3-117">Category</span></span>

<span data-ttu-id="01ae3-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="01ae3-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01ae3-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="01ae3-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
