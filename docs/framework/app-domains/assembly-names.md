---
title: 組件名稱
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9e1ba7e92614eab4d94fe953e5a0ae19611604f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927985"
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
  
 構成 .NET Framework 之組件的所有組件參考也必須包含組件的完整名稱。 例如，參考 1.0 版的 System.Data .NET Framework 組件會包括：  
  
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
  
## <a name="naming-application-components"></a>命名應用程式元件  
 判斷組件的身分識別時，執行階段不會考慮檔案名稱。 執行階段必須知道包含組件名稱、版本、文化特性和強式名稱的組件身分識別。  
  
 例如，如果您有稱為 myAssembly.exe 的組件可參考稱為 myAssembly.dll 的組件，則會在執行 myAssembly.exe 時正確地進行繫結。 不過，如果另一個應用程式使用 <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> 方法執行 myAssembly.exe，則執行階段會判斷在 myAssembly.exe 要求繫結至 "myAssembly" 時已經載入 "myAssembly"。 在此情況下，永遠不會載入 myAssembly.dll。 因為 myAssembly.exe 未包含所要求的類型，所以會發生 <xref:System.TypeLoadException>。  
  
 若要避免這個問題，請確定構成應用程式的組件沒有相同的組件名稱，或將同名的組件放在不同的目錄中。  
  
> [!NOTE]
> 如果您將強式名稱組件放入全域組件快取中，組件的檔案名稱必須符合組件名稱 (不包括副檔名，例如 .exe 或 .dll)。 例如，如果組件的檔案名稱是 myAssembly.dll，則組件名稱必須是 myAssembly。 只有在根應用程式目錄中部署的私用組件才能具有與檔案名稱不同的組件名稱。  
  
## <a name="see-also"></a>另請參閱

- [如何：決定組件的完整名稱](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)
- [建立組件](../../../docs/framework/app-domains/create-assemblies.md)
- [強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [全域組件快取](../../../docs/framework/app-domains/gac.md)
- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)
