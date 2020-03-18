---
title: 組件名稱
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 7a1a4d2512ebb002a3153fe2d51f47157136744d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733096"
---
# <a name="assembly-names"></a>組件名稱
組件的名稱儲存在中繼資料內，而且對組件範圍具有重大影響，並供應用程式使用。 強式名稱組件的完整名稱包括組件的名稱、文化特性、公開金鑰和版本號碼。 這通常稱為顯示名稱，以及可以使用 <xref:System.Reflection.Assembly.FullName%2A> 屬性取得載入的組件。

 執行階段會使用這項資訊來尋找組件，並區別它與其他同名的組件。 例如，稱為 `myTypes` 的強式名稱組件的完整名稱可能如下：

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> 處理器架構會新增至 .NET Framework 2.0 版中的組件身分識別，以允許組件的處理器特定版本。 您可以建立組件的版本，其身分識別只有處理器架構不同，例如 32 位元和 64 位元處理器特定版本。 強式名稱不需要處理器架構。 如需詳細資訊，請參閱 <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>。

 在此範例中，完整名稱指出 `myTypes` 組件具有含公開金鑰權杖的強式名稱、具有文化特性值「美式英文」，以及具有版本號碼 1.0.1234.0。 它的處理器架構為 "msil"，表示它將是根據作業系統和處理器編譯成 32 位元程式碼或 64 位元程式碼的 Just-In-Time (JIT)。

 要求組件中類型的程式碼必須使用完整組件名稱。 這稱為完整繫結。 在 .NET Framework 中參考組件時，不允許只指定組件名稱的部分繫結。

 對構成 .NET 框架的程式集的所有程式集引用還必須包含程式集的完全限定名稱。 例如，對 1.0 版 System.Data .NET 框架程式集的引用將包括：

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 請注意，版本會對應到 .NET Framework 1.0 版隨附之所有 .NET Framework 組件的版本號碼。 針對 .NET Framework 組件，文化特性值一律為中性，而且公開金鑰與上述範例所示相同。

 例如，若要在組態檔中新增組件參考來設定追蹤接聽程式，您將包括系統 .NET Framework 組件的完整名稱：

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> 繫結至組件時，執行階段會將組件名稱視為不區分大小寫，但會保留組件名稱中所使用的大小寫。 Windows SDK 中的數個工具會以區分大小寫的方式處理組件名稱。 為了獲得最佳結果，請如同其區分大小寫一樣地管理組件名稱。

## <a name="name-application-components"></a>命名應用程式元件
 判斷組件的身分識別時，執行階段不會考慮檔案名稱。 執行階段必須知道包含組件名稱、版本、文化特性和強式名稱的組件身分識別。

 例如，如果您有一個名為*myAssembly.exe*的程式集引用名為*myAssembly.dll*的程式集，則如果執行*myAssembly.exe，* 則綁定將正確進行。 但是，<xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>如果另一個應用程式使用 方法執行*myAssembly.exe，* 則運行時將`myAssembly`確定在*myAssembly.exe*請求綁定到`myAssembly`時已載入的運行時。 在這種情況下，我的*Assembly.dll*永遠不會載入。 由於*myAssembly.exe*不包含請求的類型，因此發生了<xref:System.TypeLoadException>。

 若要避免這個問題，請確定構成應用程式的組件沒有相同的組件名稱，或將同名的組件放在不同的目錄中。

> [!NOTE]
> 在 .NET 框架中，如果將強式名稱程式集放在全域組件快取中，則程式集的檔案名必須與程式集名稱匹配，不包括檔案名副檔名，如 *.exe*或 *.dll*。 例如，如果程式集的檔案名是*myAssembly.dll，* 則程式集名稱必須為`myAssembly`。 只有在根應用程式目錄中部署的私用組件才能具有與檔案名稱不同的組件名稱。

## <a name="see-also"></a>另請參閱

- [如何：確定程式集的完全限定名稱](find-fully-qualified-name.md)
- [建立組件](create.md)
- [強命名程式集](strong-named.md)
- [全域組件快取](../../framework/app-domains/gac.md)
- [運行時如何定位程式集](../../framework/deployment/how-the-runtime-locates-assemblies.md)
