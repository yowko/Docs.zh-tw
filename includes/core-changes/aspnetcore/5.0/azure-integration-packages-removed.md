---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291657"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="fadc3-101">Azure：已刪除 Microsoft 預固定的 Azure 集成包</span><span class="sxs-lookup"><span data-stu-id="fadc3-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="fadc3-102">提供ASP.NET`Microsoft.*`核心和 Azure SDK 之間集成的以下包不包括在 ASP.NET 酷 5.0 中：</span><span class="sxs-lookup"><span data-stu-id="fadc3-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="fadc3-103">[微軟.擴展.配置.AzureKeyVault，](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/)它集成了[Azure 金鑰保存庫](/azure/key-vault/)到[配置系統](/aspnet/core/fundamentals/configuration/)。</span><span class="sxs-lookup"><span data-stu-id="fadc3-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="fadc3-104">[微軟.AspNetCore.Data保護.AzureKeyVault，](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/)將Azure金鑰保存庫集成到[ASP.NET核心資料保護系統中](/aspnet/core/security/data-protection/introduction)。</span><span class="sxs-lookup"><span data-stu-id="fadc3-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="fadc3-105">[微軟.AspNetCore.Data保護.Azure存儲](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)，將Azure [Blob存儲](/azure/storage/blobs/)集成到ASP.NET核心資料保護系統中。</span><span class="sxs-lookup"><span data-stu-id="fadc3-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="fadc3-106">有關此問題的討論，請參閱[dotnet/aspnetcore_19570](https://github.com/dotnet/aspnetcore/issues/19570)。</span><span class="sxs-lookup"><span data-stu-id="fadc3-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fadc3-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="fadc3-107">Version introduced</span></span>

<span data-ttu-id="fadc3-108">5.0 預覽 1</span><span class="sxs-lookup"><span data-stu-id="fadc3-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fadc3-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="fadc3-109">Old behavior</span></span>

<span data-ttu-id="fadc3-110">這些`Microsoft.*`包將 Azure 服務與配置和資料保護 API 集成在一起。</span><span class="sxs-lookup"><span data-stu-id="fadc3-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fadc3-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="fadc3-111">New behavior</span></span>

<span data-ttu-id="fadc3-112">新`Azure.*`包將 Azure 服務與配置和資料保護 API 集成。</span><span class="sxs-lookup"><span data-stu-id="fadc3-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fadc3-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="fadc3-113">Reason for change</span></span>

<span data-ttu-id="fadc3-114">進行更改是因為`Microsoft.*`包是：</span><span class="sxs-lookup"><span data-stu-id="fadc3-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="fadc3-115">使用過時的 Azure SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="fadc3-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="fadc3-116">無法進行簡單的更新，因為 Azure SDK 的新版本包含重大更改。</span><span class="sxs-lookup"><span data-stu-id="fadc3-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="fadc3-117">綁定到 .NET 核心發佈計畫。</span><span class="sxs-lookup"><span data-stu-id="fadc3-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="fadc3-118">將包的擁有權轉移到 Azure SDK 團隊可在 Azure SDK 更新時進行包更新。</span><span class="sxs-lookup"><span data-stu-id="fadc3-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fadc3-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="fadc3-119">Recommended action</span></span>

<span data-ttu-id="fadc3-120">在ASP.NET Core 2.1 或更高版本的專案中`Microsoft.*`，用新`Azure.*`包替換舊包。</span><span class="sxs-lookup"><span data-stu-id="fadc3-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="fadc3-121">老</span><span class="sxs-lookup"><span data-stu-id="fadc3-121">Old</span></span> | <span data-ttu-id="fadc3-122">新增</span><span class="sxs-lookup"><span data-stu-id="fadc3-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="fadc3-123">Azure.AspNetCore.資料保護.金鑰</span><span class="sxs-lookup"><span data-stu-id="fadc3-123">Azure.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="fadc3-124">Azure.AspNetCore.資料保護.Blob</span><span class="sxs-lookup"><span data-stu-id="fadc3-124">Azure.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="fadc3-125">Azure.擴展.配置.機密</span><span class="sxs-lookup"><span data-stu-id="fadc3-125">Azure.Extensions.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

<span data-ttu-id="fadc3-126">新包使用 Azure SDK 的新版本，其中包括重大更改。</span><span class="sxs-lookup"><span data-stu-id="fadc3-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="fadc3-127">一般使用模式保持不變。</span><span class="sxs-lookup"><span data-stu-id="fadc3-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="fadc3-128">某些重載和選項可能不同，以適應基礎 Azure SDK API 中的更改。</span><span class="sxs-lookup"><span data-stu-id="fadc3-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="fadc3-129">舊包將：</span><span class="sxs-lookup"><span data-stu-id="fadc3-129">The old packages will:</span></span>

* <span data-ttu-id="fadc3-130">在 .NET Core 2.1 和 3.1 的存留期內，由 ASP.NET 核心團隊提供支援。</span><span class="sxs-lookup"><span data-stu-id="fadc3-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="fadc3-131">不包括在 .NET 5 中。</span><span class="sxs-lookup"><span data-stu-id="fadc3-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="fadc3-132">將專案升級到 .NET 5 時，請`Azure.*`過渡到包以維護支援。</span><span class="sxs-lookup"><span data-stu-id="fadc3-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="fadc3-133">類別</span><span class="sxs-lookup"><span data-stu-id="fadc3-133">Category</span></span>

<span data-ttu-id="fadc3-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fadc3-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fadc3-135">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fadc3-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
