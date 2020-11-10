---
title: NETSDK1071： ' ' 的 PackageReference {0} 指定了的版本 `{1}` 。
description: 如何解決 PackageReference 與具有版本之架構所包含之中繼套件的問題。
author: Forgind
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1071
ms.openlocfilehash: 852232cba04bb93a17872280e10848c2896991ae
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445750"
---
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a><span data-ttu-id="15260-103">NETSDK1071：明確建立版本的 PackageReference 至將包含在架構中的中繼套件。</span><span class="sxs-lookup"><span data-stu-id="15260-103">NETSDK1071: Explicitly versioned PackageReference to a metapackage that would be included with the framework.</span></span>

<span data-ttu-id="15260-104">本文 **適用于：** ✔️ .NET 5.0.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="15260-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="15260-105">當 .NET SDK 發出警告 NETSDK1071 時，它會建議在 PackageReference 中指定的中繼套件版本與該中繼套件的版本之間可能發生版本衝突，以透過 TargetFramework 屬性隱含參考：</span><span class="sxs-lookup"><span data-stu-id="15260-105">When the .NET SDK issues warning NETSDK1071, it suggests there may be a version conflict in the future between the version of a metapackage specified in a PackageReference and the version of that metapackage as implicitly referenced via a TargetFramework property:</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="15260-106">因為 TargetFramework 會自動帶入中繼套件的版本，所以這些版本會因為它們的差異而發生衝突。</span><span class="sxs-lookup"><span data-stu-id="15260-106">Since the TargetFramework automatically brings in a version of the metapackage, the versions will conflict should they ever differ.</span></span>

<span data-ttu-id="15260-107">若要解決這個問題：</span><span class="sxs-lookup"><span data-stu-id="15260-107">To resolve this:</span></span>

1. <span data-ttu-id="15260-108">以 .NET Core 或 .NET Standard 為目標時，請考慮在您的專案檔中明確參考 `Microsoft.NETCore.App` 或 `NETStandard.Library` 。</span><span class="sxs-lookup"><span data-stu-id="15260-108">Consider, when targeting .NET Core or .NET Standard, avoiding explicit references to `Microsoft.NETCore.App` or `NETStandard.Library` in your project file.</span></span>
2. <span data-ttu-id="15260-109">如果您在以 .NET Core 為目標時需要特定版本的執行時間，請使用 `<RuntimeFrameworkVersion>` 屬性，而不是直接參考中繼套件。</span><span class="sxs-lookup"><span data-stu-id="15260-109">If you need a specific version of the runtime when targeting .NET Core, use the `<RuntimeFrameworkVersion>`property instead of referencing the metapackage directly.</span></span> <span data-ttu-id="15260-110">舉例來說，如果您使用 [獨立的部署](../../deploying/index.md#publish-self-contained) ，並需要 1.0.0 LTS 執行時間的特定修補程式，則可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="15260-110">As an example, this could happen if you're using [self-contained deployments](../../deploying/index.md#publish-self-contained) and need a specific patch of the 1.0.0 LTS runtime.</span></span>
3. <span data-ttu-id="15260-111">如果您在以 .NET Standard 為目標時需要特定版本 `NetStandard.Library` ，您可以使用 `<NetStandardImplicitPackageVersion>` 屬性，並將它設定為所需的版本。</span><span class="sxs-lookup"><span data-stu-id="15260-111">If you need a specific version of `NetStandard.Library` when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set it to the version you need.</span></span>
4. <span data-ttu-id="15260-112">請勿 eplicitly 新增或更新 `Microsoft.NETCore.App` `NETSTandard.Library` .NET Framework 專案中或的參考。</span><span class="sxs-lookup"><span data-stu-id="15260-112">Don't eplicitly add or update references to either `Microsoft.NETCore.App` or `NETSTandard.Library` in .NET Framework projects.</span></span> <span data-ttu-id="15260-113">`NETStandard.Library`當您使用以 .NET Standard 為基礎的 nuget 套件時，NuGet 會自動安裝您需要的任何版本。</span><span class="sxs-lookup"><span data-stu-id="15260-113">NuGet automatically installs any version of `NETStandard.Library` you need when using a .NET Standard-based NuGet package.</span></span>
5. <span data-ttu-id="15260-114">`Microsoft.AspNetCore.App` `Microsoft.AspNetCore.All` 使用 .net Core 2.1 + 時，請勿指定或的版本，因為 .NET Core SDK 會自動選取適當的版本。</span><span class="sxs-lookup"><span data-stu-id="15260-114">Do not specify a version for `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` when using .NET Core 2.1+, as the .NET Core SDK automatically selects the appropriate version.</span></span> <span data-ttu-id="15260-115"> (附注：如果專案也使用，則這只適用于以 .NET Core 2.1 為目標時 `Microsoft.NET.Sdk.Web` 。</span><span class="sxs-lookup"><span data-stu-id="15260-115">(Note: This only works when targeting .NET Core 2.1 if the project also uses `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="15260-116">此問題已在 .NET Core 2.2 SDK 中解決。 ) </span><span class="sxs-lookup"><span data-stu-id="15260-116">This problem was resolved in the .NET Core 2.2 SDK.)</span></span>
6. <span data-ttu-id="15260-117">如果您想要讓警告消失，您也可以停用它：</span><span class="sxs-lookup"><span data-stu-id="15260-117">If you want the warning to go away, you can also disable it:</span></span>

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
