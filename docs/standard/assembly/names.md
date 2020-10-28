---
title: 組件名稱
description: 瞭解 .NET 元件名稱及其對元件範圍的影響，以及應用程式的使用方式，並瞭解 FullName 屬性。
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET], assemblies
- assemblies [.NET], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 136c3b7a06ce72be02e00bcc4d2354160178468c
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687573"
---
# <a name="assembly-names"></a>組件名稱

組件的名稱儲存在中繼資料內，而且對組件範圍具有重大影響，並供應用程式使用。 強式名稱元件具有完整名稱，其中包含元件的名稱、文化特性、公開金鑰、版本號碼，以及選擇性的處理器架構。 您 <xref:System.Reflection.Assembly.FullName%2A> 可以使用屬性來取得已載入元件的完整名稱，通常稱為顯示名稱。

執行時間會使用名稱資訊來找出元件，並將它與具有相同名稱的其他元件區別。 例如，稱為 `myTypes` 的強式名稱組件的完整名稱可能如下：

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

在此範例中，完整名稱表示 `myTypes` 元件具有具有公開金鑰 token 的強式名稱、具有適用于美國英文的文化特性值，且具有1.0.1234.0 的版本號碼。 它的處理器架構是 `msil` ，這表示它會及時 (JIT) 編譯成32位程式碼或64位程式碼，視作業系統和處理器而定。

> [!TIP]
> 此 `ProcessorArchitecture` 資訊允許處理器特定版本的元件。 您可以建立組件的版本，其身分識別只有處理器架構不同，例如 32 位元和 64 位元處理器特定版本。 強式名稱不需要處理器架構。 如需詳細資訊，請參閱<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>。

 要求組件中類型的程式碼必須使用完整組件名稱。 這稱為完整繫結。 參考 .NET Framework 中的元件時，不允許只指定元件名稱的部分系結。

 組成 .NET Framework 之元件的所有元件參考也必須包含元件的完整名稱。 例如，版本1.0 的資料 .NET Framework 元件的參考包括：

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

版本會對應至 .NET Framework 1.0 版隨附的所有 .NET Framework 元件的版本號碼。 針對 .NET Framework 組件，文化特性值一律為中性，而且公開金鑰與上述範例所示相同。

 例如，若要在組態檔中新增組件參考來設定追蹤接聽程式，您將包括系統 .NET Framework 組件的完整名稱：

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> 繫結至組件時，執行階段會將組件名稱視為不區分大小寫，但會保留組件名稱中所使用的大小寫。 Windows SDK 中的數個工具會以區分大小寫的方式處理組件名稱。 為了獲得最佳結果，請如同其區分大小寫一樣地管理組件名稱。

## <a name="name-application-components"></a>命名應用程式元件
 判斷組件的身分識別時，執行階段不會考慮檔案名稱。 執行階段必須知道包含組件名稱、版本、文化特性和強式名稱的組件身分識別。

 例如，如果您有一個稱為 *myAssembly.exe* 的元件，而該元件參考稱為 *myAssembly.dll* 的元件，則系結會在您執行 *myAssembly.exe* 時正確進行。 但是，如果另一個應用程式使用方法執行 *myAssembly.exe* <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> ，則運行 `myAssembly` 時間會判斷當 *myAssembly.exe* 要求系結至時，已經載入 `myAssembly` 。 在此情況下，絕對不會載入 *myAssembly.dll* 。 因為 *myAssembly.exe* 不包含所要求的型別，所以 <xref:System.TypeLoadException> 會發生。

 若要避免這個問題，請確定構成應用程式的組件沒有相同的組件名稱，或將同名的組件放在不同的目錄中。

> [!NOTE]
> 在 .NET Framework 中，如果您將強式名稱的元件放在全域組件快取中，元件的檔案名必須符合元件名稱，而不包含副檔名，例如 *.exe* 或 *.dll* 。 例如，如果元件的檔案名是 *myAssembly.dll* ，元件名稱必須是 `myAssembly` 。 只有在根應用程式目錄中部署的私用組件才能具有與檔案名稱不同的組件名稱。

## <a name="see-also"></a>請參閱

- [如何：決定元件的完整名稱](find-fully-qualified-name.md)
- [建立組件](create.md)
- [強式名稱組件](strong-named.md)
- [全域組件快取](../../framework/app-domains/gac.md)
- [執行時間如何找出元件](../../framework/deployment/how-the-runtime-locates-assemblies.md)
