---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100760"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="40c4a-101">授權：將授權重載移動到不同的程式集</span><span class="sxs-lookup"><span data-stu-id="40c4a-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="40c4a-102">過去駐`AddAuthorization`留在 中`Microsoft.AspNetCore.Authorization`的核心方法重命名為`AddAuthorizationCore`。</span><span class="sxs-lookup"><span data-stu-id="40c4a-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="40c4a-103">舊`AddAuthorization`方法仍然存在，但位於程式集中`Microsoft.AspNetCore.Authorization.Policy`。</span><span class="sxs-lookup"><span data-stu-id="40c4a-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="40c4a-104">使用這兩種方法的應用不應看到任何影響。</span><span class="sxs-lookup"><span data-stu-id="40c4a-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="40c4a-105">請注意，`Microsoft.AspNetCore.Authorization.Policy`現在在共用框架中發貨，而不是共用框架中討論的獨立包[：從 Microsoft 中刪除的程式集](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)。</span><span class="sxs-lookup"><span data-stu-id="40c4a-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40c4a-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="40c4a-106">Version introduced</span></span>

<span data-ttu-id="40c4a-107">3.0</span><span class="sxs-lookup"><span data-stu-id="40c4a-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="40c4a-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="40c4a-108">Old behavior</span></span>
<span data-ttu-id="40c4a-109">`AddAuthorization`方法存在於`Microsoft.AspNetCore.Authorization`中。</span><span class="sxs-lookup"><span data-stu-id="40c4a-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="40c4a-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="40c4a-110">New behavior</span></span>

<span data-ttu-id="40c4a-111">`AddAuthorization`方法存在於`Microsoft.AspNetCore.Authorization.Policy`中。</span><span class="sxs-lookup"><span data-stu-id="40c4a-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="40c4a-112">`AddAuthorizationCore`是舊方法的新名稱。</span><span class="sxs-lookup"><span data-stu-id="40c4a-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="40c4a-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="40c4a-113">Reason for change</span></span>

<span data-ttu-id="40c4a-114">`AddAuthorization`是添加授權所需的所有公共服務的更好方法名稱。</span><span class="sxs-lookup"><span data-stu-id="40c4a-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40c4a-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="40c4a-115">Recommended action</span></span>

<span data-ttu-id="40c4a-116">增加參考`Microsoft.AspNetCore.Authorization.Policy`或改用引用`AddAuthorizationCore`。</span><span class="sxs-lookup"><span data-stu-id="40c4a-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="40c4a-117">類別</span><span class="sxs-lookup"><span data-stu-id="40c4a-117">Category</span></span>

<span data-ttu-id="40c4a-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40c4a-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40c4a-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="40c4a-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
