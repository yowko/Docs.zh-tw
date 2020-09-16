---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275035"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="b768a-101">Identity：使用函式接受新的參數</span><span class="sxs-lookup"><span data-stu-id="b768a-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="b768a-102">從 ASP.NET Core 3.0 開始，已將新 `IUserConfirmation<TUser>` 的參數新增至函式 `SignInManager` 。</span><span class="sxs-lookup"><span data-stu-id="b768a-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="b768a-103">如需詳細資訊，請參閱 [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356)。</span><span class="sxs-lookup"><span data-stu-id="b768a-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b768a-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b768a-104">Version introduced</span></span>

<span data-ttu-id="b768a-105">3.0</span><span class="sxs-lookup"><span data-stu-id="b768a-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b768a-106">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b768a-106">Reason for change</span></span>

<span data-ttu-id="b768a-107">變革的動機是要在身分識別中新增電子郵件/確認流程的支援。</span><span class="sxs-lookup"><span data-stu-id="b768a-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b768a-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b768a-108">Recommended action</span></span>

<span data-ttu-id="b768a-109">如果手動建立 `SignInManager` ，請提供的實作為， `IUserConfirmation` 或從相依性插入中取得一個，以提供。</span><span class="sxs-lookup"><span data-stu-id="b768a-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="b768a-110">類別</span><span class="sxs-lookup"><span data-stu-id="b768a-110">Category</span></span>

<span data-ttu-id="b768a-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b768a-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b768a-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b768a-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
