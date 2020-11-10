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
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a>NETSDK1071：明確建立版本的 PackageReference 至將包含在架構中的中繼套件。

本文 **適用于：** ✔️ .NET 5.0.100 SDK 和更新版本

當 .NET SDK 發出警告 NETSDK1071 時，它會建議在 PackageReference 中指定的中繼套件版本與該中繼套件的版本之間可能發生版本衝突，以透過 TargetFramework 屬性隱含參考：

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

因為 TargetFramework 會自動帶入中繼套件的版本，所以這些版本會因為它們的差異而發生衝突。

若要解決這個問題：

1. 以 .NET Core 或 .NET Standard 為目標時，請考慮在您的專案檔中明確參考 `Microsoft.NETCore.App` 或 `NETStandard.Library` 。
2. 如果您在以 .NET Core 為目標時需要特定版本的執行時間，請使用 `<RuntimeFrameworkVersion>` 屬性，而不是直接參考中繼套件。 舉例來說，如果您使用 [獨立的部署](../../deploying/index.md#publish-self-contained) ，並需要 1.0.0 LTS 執行時間的特定修補程式，則可能會發生這種情況。
3. 如果您在以 .NET Standard 為目標時需要特定版本 `NetStandard.Library` ，您可以使用 `<NetStandardImplicitPackageVersion>` 屬性，並將它設定為所需的版本。
4. 請勿 eplicitly 新增或更新 `Microsoft.NETCore.App` `NETSTandard.Library` .NET Framework 專案中或的參考。 `NETStandard.Library`當您使用以 .NET Standard 為基礎的 nuget 套件時，NuGet 會自動安裝您需要的任何版本。
5. `Microsoft.AspNetCore.App` `Microsoft.AspNetCore.All` 使用 .net Core 2.1 + 時，請勿指定或的版本，因為 .NET Core SDK 會自動選取適當的版本。  (附注：如果專案也使用，則這只適用于以 .NET Core 2.1 為目標時 `Microsoft.NET.Sdk.Web` 。 此問題已在 .NET Core 2.2 SDK 中解決。 ) 
6. 如果您想要讓警告消失，您也可以停用它：

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
