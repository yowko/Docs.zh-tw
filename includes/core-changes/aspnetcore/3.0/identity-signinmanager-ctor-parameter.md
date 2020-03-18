---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901889"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="7c2d9-101">標識：SignInManager 建構函式接受新參數</span><span class="sxs-lookup"><span data-stu-id="7c2d9-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="7c2d9-102">從 ASP.NET Core 3.0`IUserConfirmation<TUser>`開始，向`SignInManager`建構函式添加了一個新參數。</span><span class="sxs-lookup"><span data-stu-id="7c2d9-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="7c2d9-103">有關詳細資訊，請參閱[點網/阿斯平核心#8356](https://github.com/dotnet/aspnetcore/issues/8356)。</span><span class="sxs-lookup"><span data-stu-id="7c2d9-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7c2d9-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="7c2d9-104">Version introduced</span></span>

<span data-ttu-id="7c2d9-105">3.0</span><span class="sxs-lookup"><span data-stu-id="7c2d9-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7c2d9-106">更改原因</span><span class="sxs-lookup"><span data-stu-id="7c2d9-106">Reason for change</span></span>

<span data-ttu-id="7c2d9-107">更改的動機是在標識中添加新的電子郵件/確認流。</span><span class="sxs-lookup"><span data-stu-id="7c2d9-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7c2d9-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7c2d9-108">Recommended action</span></span>

<span data-ttu-id="7c2d9-109">如果手動構造 ，`SignInManager`提供`IUserConfirmation`或 從依賴項注入中獲取實現或抓取一個來提供。</span><span class="sxs-lookup"><span data-stu-id="7c2d9-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="7c2d9-110">類別</span><span class="sxs-lookup"><span data-stu-id="7c2d9-110">Category</span></span>

<span data-ttu-id="7c2d9-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7c2d9-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7c2d9-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7c2d9-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
