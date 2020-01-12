---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901889"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="eae41-101">身分識別：使用的函式接受新的參數</span><span class="sxs-lookup"><span data-stu-id="eae41-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="eae41-102">從 ASP.NET Core 3.0 開始，新的 `IUserConfirmation<TUser>` 參數已加入至 `SignInManager` 的函式。</span><span class="sxs-lookup"><span data-stu-id="eae41-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="eae41-103">如需詳細資訊，請參閱[dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356)。</span><span class="sxs-lookup"><span data-stu-id="eae41-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eae41-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="eae41-104">Version introduced</span></span>

<span data-ttu-id="eae41-105">3.0</span><span class="sxs-lookup"><span data-stu-id="eae41-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="eae41-106">變更的原因</span><span class="sxs-lookup"><span data-stu-id="eae41-106">Reason for change</span></span>

<span data-ttu-id="eae41-107">這項變更的動機是在身分識別中新增新電子郵件/確認流程的支援。</span><span class="sxs-lookup"><span data-stu-id="eae41-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eae41-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="eae41-108">Recommended action</span></span>

<span data-ttu-id="eae41-109">如果手動建立 `SignInManager`，請提供 `IUserConfirmation` 的執行，或從要提供的相依性插入抓取一個。</span><span class="sxs-lookup"><span data-stu-id="eae41-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="eae41-110">分類</span><span class="sxs-lookup"><span data-stu-id="eae41-110">Category</span></span>

<span data-ttu-id="eae41-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eae41-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eae41-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="eae41-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
