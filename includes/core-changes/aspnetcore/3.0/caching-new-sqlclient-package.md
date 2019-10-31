---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198383"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="6069d-101">快取： SqlClient 使用新的封裝</span><span class="sxs-lookup"><span data-stu-id="6069d-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="6069d-102">`Microsoft.Extensions.Caching.SqlServer` 套件將會使用新的 `Microsoft.Data.SqlClient` 套件，而不是 `System.Data.SqlClient` 套件。</span><span class="sxs-lookup"><span data-stu-id="6069d-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="6069d-103">這種變更可能會造成些許的行為重大變更。</span><span class="sxs-lookup"><span data-stu-id="6069d-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="6069d-104">如需詳細資訊，請參閱[新的 SqlClient 簡介](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)。</span><span class="sxs-lookup"><span data-stu-id="6069d-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6069d-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6069d-105">Version introduced</span></span>

<span data-ttu-id="6069d-106">3.0</span><span class="sxs-lookup"><span data-stu-id="6069d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6069d-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="6069d-107">Old behavior</span></span>

<span data-ttu-id="6069d-108">`Microsoft.Extensions.Caching.SqlServer` 封裝使用了 `System.Data.SqlClient` 套件。</span><span class="sxs-lookup"><span data-stu-id="6069d-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6069d-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="6069d-109">New behavior</span></span>

<span data-ttu-id="6069d-110">`Microsoft.Extensions.Caching.SqlServer` 現在正在使用 `Microsoft.Data.SqlClient` 套件。</span><span class="sxs-lookup"><span data-stu-id="6069d-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6069d-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="6069d-111">Reason for change</span></span>

<span data-ttu-id="6069d-112">`Microsoft.Data.SqlClient` 是建置於 `System.Data.SqlClient` 的新套件。</span><span class="sxs-lookup"><span data-stu-id="6069d-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="6069d-113">從現在開始，所有的新功能工作都將從這裡開始進行。</span><span class="sxs-lookup"><span data-stu-id="6069d-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6069d-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6069d-114">Recommended action</span></span>

<span data-ttu-id="6069d-115">除非客戶使用 `Microsoft.Extensions.Caching.SqlServer` 封裝所傳回的類型，並將它們轉換成 `System.Data.SqlClient` 類型，否則不應擔心這項重大變更。</span><span class="sxs-lookup"><span data-stu-id="6069d-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="6069d-116">例如，如果有人將 `DbConnection` 轉換成[舊的 SqlConnection 型](xref:System.Data.SqlClient.SqlConnection)別，則必須將轉換變更為新的 `Microsoft.Data.SqlClient.SqlConnection` 型別。</span><span class="sxs-lookup"><span data-stu-id="6069d-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="6069d-117">Category</span><span class="sxs-lookup"><span data-stu-id="6069d-117">Category</span></span>

<span data-ttu-id="6069d-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6069d-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6069d-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6069d-119">Affected APIs</span></span>

<span data-ttu-id="6069d-120">None</span><span class="sxs-lookup"><span data-stu-id="6069d-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
