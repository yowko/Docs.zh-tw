---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198383"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="1d4ec-101">緩存：微軟.擴展.緩存.SqlServer 使用新的 SqlClient 包</span><span class="sxs-lookup"><span data-stu-id="1d4ec-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="1d4ec-102">包`Microsoft.Extensions.Caching.SqlServer`將使用新`Microsoft.Data.SqlClient`包而不是`System.Data.SqlClient`包。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="1d4ec-103">此更改可能會導致輕微的行為中斷更改。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="1d4ec-104">有關詳細資訊，請參閱[介紹新的 Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1d4ec-105">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="1d4ec-105">Version introduced</span></span>

<span data-ttu-id="1d4ec-106">3.0</span><span class="sxs-lookup"><span data-stu-id="1d4ec-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1d4ec-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="1d4ec-107">Old behavior</span></span>

<span data-ttu-id="1d4ec-108">包`Microsoft.Extensions.Caching.SqlServer`使用了包`System.Data.SqlClient`。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1d4ec-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="1d4ec-109">New behavior</span></span>

<span data-ttu-id="1d4ec-110">`Microsoft.Extensions.Caching.SqlServer`正在使用包`Microsoft.Data.SqlClient`。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1d4ec-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="1d4ec-111">Reason for change</span></span>

<span data-ttu-id="1d4ec-112">`Microsoft.Data.SqlClient`是 由 構建的新包`System.Data.SqlClient`。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="1d4ec-113">從現在起，所有新功能工作都將在這裡完成。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1d4ec-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1d4ec-114">Recommended action</span></span>

<span data-ttu-id="1d4ec-115">客戶無需擔心這種重大更改，除非他們使用`Microsoft.Extensions.Caching.SqlServer`包返回的類型並將其強制轉換給`System.Data.SqlClient`類型。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="1d4ec-116">例如，如果有人將 強制轉換為`DbConnection`[舊的 SqlConnection 類型](xref:System.Data.SqlClient.SqlConnection)，則需要將強制轉換更改為新`Microsoft.Data.SqlClient.SqlConnection`類型。</span><span class="sxs-lookup"><span data-stu-id="1d4ec-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="1d4ec-117">類別</span><span class="sxs-lookup"><span data-stu-id="1d4ec-117">Category</span></span>

<span data-ttu-id="1d4ec-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d4ec-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1d4ec-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1d4ec-119">Affected APIs</span></span>

<span data-ttu-id="1d4ec-120">None</span><span class="sxs-lookup"><span data-stu-id="1d4ec-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
