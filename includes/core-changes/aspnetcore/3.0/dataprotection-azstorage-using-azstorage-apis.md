---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394302"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="efb04-101">資料保護： DataProtection. AzureStorage 使用新的 Azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="efb04-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="efb04-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> 取決於[Azure 儲存體程式庫](https://github.com/Azure/azure-storage-net)。</span><span class="sxs-lookup"><span data-stu-id="efb04-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="efb04-103">這些程式庫會將其元件、封裝和命名空間重新命名。</span><span class="sxs-lookup"><span data-stu-id="efb04-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="efb04-104">從 ASP.NET Core 3.0 開始，`Microsoft.AspNetCore.DataProtection.AzureStorage` 會使用新的 `Microsoft.Azure.Storage.` 首碼的 Api 和套件。</span><span class="sxs-lookup"><span data-stu-id="efb04-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="efb04-105">如有 Azure 儲存體 Api 的相關問題，請使用 <https://github.com/Azure/azure-storage-net>。</span><span class="sxs-lookup"><span data-stu-id="efb04-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="efb04-106">如需此問題的討論，請參閱[aspnet/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472)。</span><span class="sxs-lookup"><span data-stu-id="efb04-106">For discussion on this issue, see [aspnet/AspNetCore#8472](https://github.com/aspnet/AspNetCore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="efb04-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="efb04-107">Version introduced</span></span>

<span data-ttu-id="efb04-108">3.0</span><span class="sxs-lookup"><span data-stu-id="efb04-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="efb04-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="efb04-109">Old behavior</span></span>

<span data-ttu-id="efb04-110">封裝參考了 `WindowsAzure.Storage` NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="efb04-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="efb04-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="efb04-111">New behavior</span></span>

<span data-ttu-id="efb04-112">此套件會參考 `Microsoft.Azure.Storage.Blob` NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="efb04-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="efb04-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="efb04-113">Reason for change</span></span>

<span data-ttu-id="efb04-114">這種變更可讓 `Microsoft.AspNetCore.DataProtection.AzureStorage` 遷移至建議的 Azure 儲存體套件。</span><span class="sxs-lookup"><span data-stu-id="efb04-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="efb04-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="efb04-115">Recommended action</span></span>

<span data-ttu-id="efb04-116">如果您仍然需要使用具有 ASP.NET Core 3.0 的舊版 Azure 儲存體 Api，請新增[windowsazure.storage](https://www.nuget.org/packages/WindowsAzure.Storage/)套件的直接相依性。</span><span class="sxs-lookup"><span data-stu-id="efb04-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="efb04-117">此套件可以與新的 `Microsoft.Azure.Storage` Api 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="efb04-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="efb04-118">在許多情況下，升級只牽涉到將 @no__t 0 的語句變更為使用新的命名空間：</span><span class="sxs-lookup"><span data-stu-id="efb04-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="efb04-119">分類</span><span class="sxs-lookup"><span data-stu-id="efb04-119">Category</span></span>

<span data-ttu-id="efb04-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="efb04-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="efb04-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="efb04-121">Affected APIs</span></span>

<span data-ttu-id="efb04-122">無</span><span class="sxs-lookup"><span data-stu-id="efb04-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
