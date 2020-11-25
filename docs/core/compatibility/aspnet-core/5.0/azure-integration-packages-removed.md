---
title: 重大變更： Azure：已移除的 Microsoft 首碼 Azure 整合套件
description: 瞭解 ASP.NET Core 5.0 中的重大變更，標題為 Azure：已移除 Microsoft 首碼的 Azure 整合套件
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b9f685b8c9fdcd73044f78840f2732809a0de710
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760774"
---
# <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="783d7-103">Azure：已移除的 Microsoft 首碼 Azure 整合套件</span><span class="sxs-lookup"><span data-stu-id="783d7-103">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="783d7-104">下列 `Microsoft.*` 封裝可提供 ASP.NET Core 和 Azure sdk 之間的整合，但不包含在 ASP.NET Core 5.0 中：</span><span class="sxs-lookup"><span data-stu-id="783d7-104">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="783d7-105">[Microsoft.Extensions.Configuration。AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/)，會將 [Azure Key Vault](/azure/key-vault/) 整合至設定 [系統](/aspnet/core/fundamentals/configuration/)。</span><span class="sxs-lookup"><span data-stu-id="783d7-105">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="783d7-106">[AspNetCore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/)，可將 Azure Key Vault 整合到 [ASP.NET Core 資料保護系統](/aspnet/core/security/data-protection/introduction)中。</span><span class="sxs-lookup"><span data-stu-id="783d7-106">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="783d7-107">[AspNetCore. DataProtection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)，可將 [Azure Blob 儲存體](/azure/storage/blobs/) 整合到 ASP.NET Core 資料保護系統中。</span><span class="sxs-lookup"><span data-stu-id="783d7-107">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="783d7-108">如需此問題的討論，請參閱 [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570)。</span><span class="sxs-lookup"><span data-stu-id="783d7-108">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="783d7-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="783d7-109">Version introduced</span></span>

<span data-ttu-id="783d7-110">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="783d7-110">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="783d7-111">舊的行為</span><span class="sxs-lookup"><span data-stu-id="783d7-111">Old behavior</span></span>

<span data-ttu-id="783d7-112">`Microsoft.*`套件整合了 Azure 服務與設定和資料保護 api。</span><span class="sxs-lookup"><span data-stu-id="783d7-112">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="783d7-113">新的行為</span><span class="sxs-lookup"><span data-stu-id="783d7-113">New behavior</span></span>

<span data-ttu-id="783d7-114">新 `Azure.*` 套件會整合 Azure 服務與設定和資料保護 api。</span><span class="sxs-lookup"><span data-stu-id="783d7-114">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="783d7-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="783d7-115">Reason for change</span></span>

<span data-ttu-id="783d7-116">變更的原因是因為 `Microsoft.*` 封裝：</span><span class="sxs-lookup"><span data-stu-id="783d7-116">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="783d7-117">使用過期版本的 Azure SDK。</span><span class="sxs-lookup"><span data-stu-id="783d7-117">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="783d7-118">因為新版本的 Azure SDK 包含了重大變更，所以不可能進行簡單的更新。</span><span class="sxs-lookup"><span data-stu-id="783d7-118">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="783d7-119">與 .NET Core 發行排程相關聯。</span><span class="sxs-lookup"><span data-stu-id="783d7-119">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="783d7-120">將套件的擁有權轉移給 Azure SDK 小組可在 Azure SDK 更新時啟用套件更新。</span><span class="sxs-lookup"><span data-stu-id="783d7-120">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="783d7-121">建議的動作</span><span class="sxs-lookup"><span data-stu-id="783d7-121">Recommended action</span></span>

<span data-ttu-id="783d7-122">在 ASP.NET Core 2.1 或更新版本的專案中，將舊的取代為 `Microsoft.*` 新的 `Azure.*` 套件。</span><span class="sxs-lookup"><span data-stu-id="783d7-122">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="783d7-123">老</span><span class="sxs-lookup"><span data-stu-id="783d7-123">Old</span></span> | <span data-ttu-id="783d7-124">新增</span><span class="sxs-lookup"><span data-stu-id="783d7-124">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="783d7-125">AspNetCore. DataProtection 金鑰</span><span class="sxs-lookup"><span data-stu-id="783d7-125">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="783d7-126">AspNetCore. DataProtection Blob</span><span class="sxs-lookup"><span data-stu-id="783d7-126">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="783d7-127">Azure.Extensions.AspNetCore.Configuration。秘密</span><span class="sxs-lookup"><span data-stu-id="783d7-127">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="783d7-128">新的套件會使用新版本的 Azure SDK，其中包含重大變更。</span><span class="sxs-lookup"><span data-stu-id="783d7-128">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="783d7-129">一般使用模式不會變更。</span><span class="sxs-lookup"><span data-stu-id="783d7-129">The general usage patterns are unchanged.</span></span> <span data-ttu-id="783d7-130">某些多載和選項可能不同，以適應基礎 Azure SDK Api 中的變更。</span><span class="sxs-lookup"><span data-stu-id="783d7-130">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="783d7-131">舊的封裝將會：</span><span class="sxs-lookup"><span data-stu-id="783d7-131">The old packages will:</span></span>

* <span data-ttu-id="783d7-132">在 .NET Core 2.1 和3.1 的存留期內，ASP.NET Core 團隊支援。</span><span class="sxs-lookup"><span data-stu-id="783d7-132">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="783d7-133">不包含在 .NET 5 中。</span><span class="sxs-lookup"><span data-stu-id="783d7-133">Not be included in .NET 5.</span></span>

<span data-ttu-id="783d7-134">將專案升級至 .NET 5 時，請轉換至 `Azure.*` 封裝以維持支援。</span><span class="sxs-lookup"><span data-stu-id="783d7-134">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="783d7-135">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="783d7-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
