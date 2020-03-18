---
title: 強式命名與 .NET 程式庫
description: .NET 程式庫強式命名的最佳做法建議。
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744530"
---
# <a name="strong-naming"></a>強式命名

強式命名是指使用金鑰對組件進行簽名，進而產生[強式名稱組件](../assembly/strong-named.md)。 當組件具有強式名稱時，它會根據名稱與組件版本號碼建立唯一身分識別，而且它可以協助防止組件衝突。

強式命名的缺點是，一旦組件具有強式名稱，Windows 上的 .NET Framework 就會啟用嚴格的組件載入。 強式名稱組件參考必須與組件參考的版本完全符合，以強制開發人員在使用組件時[設定繫結重新導向](../../framework/configure-apps/redirect-assembly-versions.md)：

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

當 .NET 開發人員抱怨強式命名時，他們通常抱怨的是嚴格的組件載入。 幸運的是，只有 .NET Framework 會有此問題。 .NET core、Xamarin、UWP 與其他大部分的 .NET 實作沒有嚴格的組件載入，且移除了強式命名的主要缺點。

強式命名的一個重要層面是它是病毒式：強式命名組件只能參考其他強式名稱組件。 如果您的程式庫不是強式命名，那麼您已經排除了正在建置需要進行強式命名之應用程式或程式庫的開發人員，使其無法使用它。

強式命名的優點為：

1. 組件可以被其他強式名稱組件參考及使用。
2. 組件可以儲存於全域組件快取 (GAC)。
3. 組件可以組件的其他版本並存載入。 具有外掛程式架構的應用程式通常需要並存組件載入。

## <a name="create-strong-named-net-libraries"></a>建立強式命名的 .NET 程式庫

您應該為您的開放原始碼 .NET 程式庫進行強式命名。 強式命名組件可確保大部分的人可以使用它，而嚴格的組件載入只會影響 .NET Framework。

> [!NOTE]
> 本指南特定于公開分發的 .NET 庫，例如NuGet.org上發佈的 .NET 庫。大多數 .NET 應用程式不需要強命名，預設情況下不應進行強命名。

✔️ 考慮為您的程式庫組件進行強式命名。

✔️ 考慮將強式命名金鑰新增至您的原始檔控制系統。

> 公開可用的金鑰可讓開發人員使用相同的金鑰修改及編譯您的程式庫原始程式碼。
>
> 如果過去曾使用強式命名金鑰在[部分信任案例](../../framework/misc/using-libraries-from-partially-trusted-code.md)中授與特殊權限，則不應將它公開。 否則，您可能會危及現有的環境。

> [!IMPORTANT]
> 當需要程式碼發行者的身分識別時，建議使用 [Authenticode](/windows-hardware/drivers/install/authenticode) 與 [NuGet 套件簽署](/nuget/create-packages/sign-a-package)。 程式碼存取安全性 (CAS) 不應作為安全性風險降低機制使用。

✔️ 考慮僅在主要版本變更時遞增組件版本，以協助使用者減少繫結重新導向，以及更新它們的頻率。

> 深入了解[版本控制與組件版本](./versioning.md#assembly-version)。

❌請勿新增、移除或變更強式命名金鑰。

> 修改組件的強式命名金鑰會變更組件的身分識別，並且中斷使用它的編譯程式碼。 如需詳細資訊，請參閱[二進位中斷性變更](./breaking-changes.md#binary-breaking-change)。

❌不要發佈庫的強命名和非強命名版本。 例如 `Contoso.Api` 和 `Contoso.Api.StrongNamed`。

> 發佈兩個套件會派生您的開發人員生態系統。 此外，如果應用程式最後根據這兩個套件，開發人員可能會遇到類型名稱衝突。 就 .NET 而言，它們在不同的組件中是不同的類型。

>[!div class="step-by-step"]
>[上一個](cross-platform-targeting.md)
>[下一個](nuget.md)
