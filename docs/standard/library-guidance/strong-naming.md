---
title: 強式命名和.NET 程式庫
description: 強式命名的.NET 程式庫的最佳作法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: e3f7d443eb9acc84c800ea2611b803733085391c
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372801"
---
# <a name="strong-naming"></a>強式命名

強式命名簽署金鑰，產生的組件是指[強式名稱組件](../../framework/app-domains/strong-named-assemblies.md)。 當強式名稱組件，它會建立唯一的名稱和組件版本號碼為基礎的身分識別，它可以協助防止組件衝突。

強式命名的缺點是 Windows 上的.NET Framework 可讓組件具有強式名稱之後嚴格方式載入組件。 強式名稱組件的參考必須完全符合的組件中，然後再強制開發人員所參考的版本[設定繫結重新導向](../../framework/configure-apps/redirect-assembly-versions.md)時使用的組件：

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

當強式命名抱怨.NET 開發人員時，什麼它們通常抱怨是嚴格的組件載入。 幸運的是，這是問題隔離至.NET Framework。 .NET core、 Xamarin、 UWP 和其他大部分的.NET 實作不需要嚴格的組件載入，並移除強式命名的主要缺點。

強式命名的一個重要層面是它是病毒式： 強式命名組件可以只參考其他強式名稱組件。 如果您的程式庫不強式命名，您已排除的開發人員所建置的應用程式庫需要使用它的強式命名。

強式命名的優點為：

1. 組件可參考，並由其他強式名稱組件中。
2. 組件可以儲存在全域組件快取 (GAC) 中。
3. 組件可以載入組件的其他版本並存。 使用外掛程式架構的應用程式通常需要並排顯示的組件載入。

## <a name="create-strong-named-net-libraries"></a>建立強式命名的.NET 程式庫

您應該強式命名您的開放原始碼.NET 程式庫。 強式命名組件可確保大部分的人可以使用它，並嚴格的組件載入僅會影響在.NET Framework。

> [!NOTE]
> 本指南旨在公開分散式的.NET 程式庫，例如在 NuGet.org 上發行的.NET 程式庫。大部分的.NET 應用程式不需要強式命名，並不應該根據預設。

**請考慮 ✔️**強式命名您的程式庫組件。

**請考慮 ✔️**簽入到原始檔控制系統使用的強式名稱的金鑰。

> 公開可用的金鑰可讓開發人員修改及編譯您的程式庫程式碼使用相同的金鑰。

> [!IMPORTANT]
> 時需要密碼編譯的身分識別，則[Authenticode](/windows-hardware/drivers/install/authenticode)並[NuGet 套件簽署](/nuget/create-packages/sign-a-package)建議。 強式命名不應該使用的安全性考量。

**請考慮 ✔️**遞增組件版本，只有主要版本變更，以協助使用者減少繫結重新導向，以及要更新的頻率。

> 深入了解[版本控制和組件版本](./versioning.md#assembly-version)。

**不這麼做 ❌**新增、 移除或變更的強式命名的索引鍵。

> 修改組件的強式命名金鑰變更組件的識別，並且中斷編譯的程式碼使用它。 如需詳細資訊，請參閱 <<c0> [ 二進位的重大變更](./breaking-changes.md#binary-breaking-change)。

**不這麼做 ❌**發佈您的媒體櫃的強式名稱，且非強式名稱版本。 例如，`Contoso.Api` 和 `Contoso.Api.StrongNamed`。

> 發佈兩個套件分岔程式開發人員最系統。 此外，如果應用程式最後會根據這兩個封裝開發人員可能會遇到類型名稱衝突。 .NET 是而言它們是不同的組件中的不同類型。

>[!div class="step-by-step"]
[上一頁](./cross-platform-targeting.md)
[下一頁](./nuget.md)
