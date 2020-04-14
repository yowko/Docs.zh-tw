---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275035"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="06e71-101">識別:SignInManager 建構函數接受新參數</span><span class="sxs-lookup"><span data-stu-id="06e71-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="06e71-102">從 ASP.NET Core`IUserConfirmation<TUser>`3.0`SignInManager`開始,向構造函數添加了一個新參數。</span><span class="sxs-lookup"><span data-stu-id="06e71-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="06e71-103">有關詳細資訊,請參閱[點網/阿斯平核心#8356](https://github.com/dotnet/aspnetcore/issues/8356)。</span><span class="sxs-lookup"><span data-stu-id="06e71-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="06e71-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="06e71-104">Version introduced</span></span>

<span data-ttu-id="06e71-105">3.0</span><span class="sxs-lookup"><span data-stu-id="06e71-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="06e71-106">變更原因</span><span class="sxs-lookup"><span data-stu-id="06e71-106">Reason for change</span></span>

<span data-ttu-id="06e71-107">更改的動機是在標識中添加新的電子郵件/確認流。</span><span class="sxs-lookup"><span data-stu-id="06e71-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="06e71-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="06e71-108">Recommended action</span></span>

<span data-ttu-id="06e71-109">如果手動構造`SignInManager`,`IUserConfirmation`提供 或 從依賴項注入中獲取實現或抓取一個來提供。</span><span class="sxs-lookup"><span data-stu-id="06e71-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="06e71-110">類別</span><span class="sxs-lookup"><span data-stu-id="06e71-110">Category</span></span>

<span data-ttu-id="06e71-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="06e71-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="06e71-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="06e71-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
