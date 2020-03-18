---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901705"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="f840d-101">資料保護：資料保護.Azure 存儲使用新的 Azure 存儲 API</span><span class="sxs-lookup"><span data-stu-id="f840d-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="f840d-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>取決於[Azure 存儲庫](https://github.com/Azure/azure-storage-net)。</span><span class="sxs-lookup"><span data-stu-id="f840d-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="f840d-103">這些庫重命名其程式集、包和命名空間。</span><span class="sxs-lookup"><span data-stu-id="f840d-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="f840d-104">從 ASP.NET 酷 3.0`Microsoft.AspNetCore.DataProtection.AzureStorage`開始`Microsoft.Azure.Storage.`，使用新的 -預定 API 和包。</span><span class="sxs-lookup"><span data-stu-id="f840d-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="f840d-105">有關 Azure 存儲 API 的問題，<https://github.com/Azure/azure-storage-net>請使用 。</span><span class="sxs-lookup"><span data-stu-id="f840d-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="f840d-106">有關此問題的討論，請參閱[dotnet/aspnetcore_8472](https://github.com/dotnet/aspnetcore/issues/8472)。</span><span class="sxs-lookup"><span data-stu-id="f840d-106">For discussion on this issue, see [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f840d-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f840d-107">Version introduced</span></span>

<span data-ttu-id="f840d-108">3.0</span><span class="sxs-lookup"><span data-stu-id="f840d-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f840d-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="f840d-109">Old behavior</span></span>

<span data-ttu-id="f840d-110">該包引用了`WindowsAzure.Storage`NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="f840d-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f840d-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="f840d-111">New behavior</span></span>

<span data-ttu-id="f840d-112">該包引用`Microsoft.Azure.Storage.Blob`NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="f840d-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f840d-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="f840d-113">Reason for change</span></span>

<span data-ttu-id="f840d-114">此更改允許`Microsoft.AspNetCore.DataProtection.AzureStorage`遷移到建議的 Azure 存儲包。</span><span class="sxs-lookup"><span data-stu-id="f840d-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f840d-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f840d-115">Recommended action</span></span>

<span data-ttu-id="f840d-116">如果仍需要將較舊的 Azure 存儲 API 與 ASP.NET Core 3.0 一起使用，則向[WindowsAzure.存儲](https://www.nuget.org/packages/WindowsAzure.Storage/)包添加直接依賴項。</span><span class="sxs-lookup"><span data-stu-id="f840d-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="f840d-117">此包可以與新`Microsoft.Azure.Storage`API 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="f840d-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="f840d-118">在許多情況下，升級僅涉及更改`using`語句以使用新的命名空間：</span><span class="sxs-lookup"><span data-stu-id="f840d-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="f840d-119">類別</span><span class="sxs-lookup"><span data-stu-id="f840d-119">Category</span></span>

<span data-ttu-id="f840d-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f840d-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f840d-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f840d-121">Affected APIs</span></span>

<span data-ttu-id="f840d-122">None</span><span class="sxs-lookup"><span data-stu-id="f840d-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
