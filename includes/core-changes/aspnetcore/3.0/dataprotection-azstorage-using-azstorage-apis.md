---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440417"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a><span data-ttu-id="060d1-101">資料保護： DataProtection 會使用新的 Azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="060d1-101">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>

<span data-ttu-id="060d1-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` 相依于 [Azure 儲存體程式庫](https://github.com/Azure/azure-storage-net)。</span><span class="sxs-lookup"><span data-stu-id="060d1-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="060d1-103">這些程式庫會將其元件、封裝和命名空間重新命名。</span><span class="sxs-lookup"><span data-stu-id="060d1-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="060d1-104">從 ASP.NET Core 3.0 開始，會 `Azure.Extensions.AspNetCore.DataProtection.Blobs` 使用新 `Azure.Storage.` 首碼的 api 和套件。</span><span class="sxs-lookup"><span data-stu-id="060d1-104">Starting in ASP.NET Core 3.0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` uses the new `Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="060d1-105">如有 Azure 儲存體 Api 的相關問題，請使用 <https://github.com/Azure/azure-storage-net> 。</span><span class="sxs-lookup"><span data-stu-id="060d1-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="060d1-106">如需此問題的討論，請參閱 [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570)。</span><span class="sxs-lookup"><span data-stu-id="060d1-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="060d1-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="060d1-107">Version introduced</span></span>

<span data-ttu-id="060d1-108">3.0</span><span class="sxs-lookup"><span data-stu-id="060d1-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="060d1-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="060d1-109">Old behavior</span></span>

<span data-ttu-id="060d1-110">封裝參考 `WindowsAzure.Storage` NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="060d1-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>
<span data-ttu-id="060d1-111">套件會參考 `Microsoft.Azure.Storage.Blob` NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="060d1-111">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="060d1-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="060d1-112">New behavior</span></span>

<span data-ttu-id="060d1-113">套件會參考 `Azure.Storage.Blob` NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="060d1-113">The package references the `Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="060d1-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="060d1-114">Reason for change</span></span>

<span data-ttu-id="060d1-115">這種變更可讓 `Azure.Extensions.AspNetCore.DataProtection.Blobs` 您遷移至建議的 Azure 儲存體套件。</span><span class="sxs-lookup"><span data-stu-id="060d1-115">This change allows `Azure.Extensions.AspNetCore.DataProtection.Blobs` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="060d1-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="060d1-116">Recommended action</span></span>

<span data-ttu-id="060d1-117">如果您仍然需要使用舊版 Azure 儲存體 Api 搭配 ASP.NET Core 3.0，請將直接相依性新增至 [WindowsAzure](https://www.nuget.org/packages/WindowsAzure.Storage/) 套件或 [Microsoft Azure 儲存體](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/)。</span><span class="sxs-lookup"><span data-stu-id="060d1-117">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the package [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) or [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span></span> <span data-ttu-id="060d1-118">這個套件可以隨新的 api 一起安裝 `Azure.Storage` 。</span><span class="sxs-lookup"><span data-stu-id="060d1-118">This package can be installed alongside the new `Azure.Storage` APIs.</span></span>

<span data-ttu-id="060d1-119">在許多情況下，升級只牽涉到將 `using` 語句變更為使用新的命名空間：</span><span class="sxs-lookup"><span data-stu-id="060d1-119">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a><span data-ttu-id="060d1-120">類別</span><span class="sxs-lookup"><span data-stu-id="060d1-120">Category</span></span>

<span data-ttu-id="060d1-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="060d1-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="060d1-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="060d1-122">Affected APIs</span></span>

<span data-ttu-id="060d1-123">無</span><span class="sxs-lookup"><span data-stu-id="060d1-123">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
