---
ms.openlocfilehash: 19ccdb634d4e53ea66c032502f2adb70423ab121
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416260"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="49fd5-101">Azure：已移除 Microsoft 前面的 Azure 整合套件</span><span class="sxs-lookup"><span data-stu-id="49fd5-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="49fd5-102">`Microsoft.*`ASP.NET Core 5.0 中不包含下列提供 ASP.NET Core 與 Azure sdk 之間整合的套件：</span><span class="sxs-lookup"><span data-stu-id="49fd5-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="49fd5-103">[Microsoft.Extensions.Configuration。AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/)，它會將[Azure Key Vault](/azure/key-vault/)整合至設定[系統](/aspnet/core/fundamentals/configuration/)。</span><span class="sxs-lookup"><span data-stu-id="49fd5-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="49fd5-104">[AspNetCore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/)，可將 Azure Key Vault 整合到 ASP.NET Core 的[資料保護系統](/aspnet/core/security/data-protection/introduction)。</span><span class="sxs-lookup"><span data-stu-id="49fd5-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="49fd5-105">[AspNetCore. DataProtection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)，可將[Azure Blob 儲存體](/azure/storage/blobs/)整合到 ASP.NET Core 的資料保護系統。</span><span class="sxs-lookup"><span data-stu-id="49fd5-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="49fd5-106">如需此問題的討論，請參閱[dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570)。</span><span class="sxs-lookup"><span data-stu-id="49fd5-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="49fd5-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="49fd5-107">Version introduced</span></span>

<span data-ttu-id="49fd5-108">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="49fd5-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="49fd5-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="49fd5-109">Old behavior</span></span>

<span data-ttu-id="49fd5-110">`Microsoft.*`套件整合了 Azure 服務與設定和資料保護 api。</span><span class="sxs-lookup"><span data-stu-id="49fd5-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="49fd5-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="49fd5-111">New behavior</span></span>

<span data-ttu-id="49fd5-112">新 `Azure.*` 的套件會整合 Azure 服務與設定和資料保護 api。</span><span class="sxs-lookup"><span data-stu-id="49fd5-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="49fd5-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="49fd5-113">Reason for change</span></span>

<span data-ttu-id="49fd5-114">已進行變更，因為 `Microsoft.*` 封裝是：</span><span class="sxs-lookup"><span data-stu-id="49fd5-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="49fd5-115">使用過時版本的 Azure SDK。</span><span class="sxs-lookup"><span data-stu-id="49fd5-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="49fd5-116">不可能進行簡單的更新，因為新版本的 Azure SDK 包含重大變更。</span><span class="sxs-lookup"><span data-stu-id="49fd5-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="49fd5-117">系結至 .NET Core 發行排程。</span><span class="sxs-lookup"><span data-stu-id="49fd5-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="49fd5-118">將套件的擁有權轉移給 Azure SDK 小組會在更新 Azure SDK 時啟用套件更新。</span><span class="sxs-lookup"><span data-stu-id="49fd5-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="49fd5-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="49fd5-119">Recommended action</span></span>

<span data-ttu-id="49fd5-120">在 ASP.NET Core 2.1 或更新版本的專案中，以新的套件取代舊的 `Microsoft.*` `Azure.*` 。</span><span class="sxs-lookup"><span data-stu-id="49fd5-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="49fd5-121">多久</span><span class="sxs-lookup"><span data-stu-id="49fd5-121">Old</span></span> | <span data-ttu-id="49fd5-122">新增</span><span class="sxs-lookup"><span data-stu-id="49fd5-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="49fd5-123">AspNetCore. DataProtection. 金鑰</span><span class="sxs-lookup"><span data-stu-id="49fd5-123">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="49fd5-124">AspNetCore. DataProtection Blob</span><span class="sxs-lookup"><span data-stu-id="49fd5-124">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="49fd5-125">Azure.Extensions.AspNetCore.Configuration。越長</span><span class="sxs-lookup"><span data-stu-id="49fd5-125">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="49fd5-126">新的套件會使用新版本的 Azure SDK，其中包含重大變更。</span><span class="sxs-lookup"><span data-stu-id="49fd5-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="49fd5-127">一般使用模式不會變更。</span><span class="sxs-lookup"><span data-stu-id="49fd5-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="49fd5-128">有些多載和選項可能會不同，以適應基礎 Azure SDK Api 中的變更。</span><span class="sxs-lookup"><span data-stu-id="49fd5-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="49fd5-129">舊的套件將會：</span><span class="sxs-lookup"><span data-stu-id="49fd5-129">The old packages will:</span></span>

* <span data-ttu-id="49fd5-130">在 .NET Core 2.1 和3.1 的存留期間，由 ASP.NET Core 小組支援。</span><span class="sxs-lookup"><span data-stu-id="49fd5-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="49fd5-131">不包含在 .NET 5 中。</span><span class="sxs-lookup"><span data-stu-id="49fd5-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="49fd5-132">將您的專案升級至 .NET 5 時，請轉換至 `Azure.*` 套件以維持支援。</span><span class="sxs-lookup"><span data-stu-id="49fd5-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="49fd5-133">類別</span><span class="sxs-lookup"><span data-stu-id="49fd5-133">Category</span></span>

<span data-ttu-id="49fd5-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49fd5-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="49fd5-135">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="49fd5-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
