---
title: "組件名稱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7029fb2b436c9ba49f2dfd3da07c5147222fbeaf
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 組件名稱
組件名稱存放在中繼資料中，對於組件的範圍 \(Scope\) 和應用程式的使用有重大的影響。  強式名稱的組件具有包含組件名稱、文化特性、公開金鑰和版本號碼的完整名稱。  這通常稱為顯示名稱，以及可以使用 <xref:System.Reflection.Assembly.FullName%2A> 屬性取得的載入組件。  
  
 執行階段會使用這項資訊找出組件，並和其他有相同名稱的組件區別。  例如，稱為 `myTypes` 的強式名稱組件可能會有下列完整名稱：  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  處理器架構會加入到 .NET Framework 2.0 版中的組件識別，以允許處理器特定的組件版本。  您可以建立不同組件版本，讓這些版本的識別之間只有處理器架構不同，例如，32 位元和 64 位元的處理器特定版本。  強式名稱不需要處理器架構。  如需詳細資訊，請參閱<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=fullName>。  
  
 在這個範例中，完整名稱表示 `myTypes` 組件的強式名稱有公開金鑰語彙基元、文化特性值為英文 \(美國\)，以及版本號碼為 1.0.1234.0。  它的處理器架構為 "msil"，這表示它會是編譯成 32 位元或 64 位元的 Just\-in\-Time \(JIT\) 程式碼 \(根據作業系統和處理器而定\)。  
  
 在組件中要求型別的程式碼必須使用完整的組件名稱。  這稱為完整繫結。  在 .NET Framework 中參考組件時，則不允許僅指定組件名稱的部分繫結。  
  
 構成 .NET Framework 的組件的所有組件參考必須包含組件的完整名稱。  例如，若要參考版本 1.0 的 System.Data .NET Framework 組件將包括：  
  
```  
  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
  
```  
  
 請注意，版本和隨附於 .NET Framework 版本 1.0 的所有 .NET Framework 組件版本號碼對應。  對於 .NET Framework 組件，文化特性值永遠是中性的，公開金鑰則和上述範例中顯示的相同。  
  
 例如，若要在組態檔中加入組件參考以設定追蹤接聽程式，您會包括系統 .NET Framework 組件的完整名稱：  
  
```  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  執行階段繫結至組件時，不會區分組件名稱的大小寫，但是會保留組件名稱中所使用的大小寫。  [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 中有幾項工具會區分組件名稱的大小寫。  如果要取得最佳效果，請區分組件名稱的大小寫。  
  
## 命名應用程式元件  
 判斷組件識別 \(Identity\) 時，執行階段並不會考慮到檔名。  對執行階段而言，由組件名稱、版本、文化特性和強式名稱所組成的組件識別必須非常清楚。  
  
 例如，如果您有一個名稱為 myAssembly.exe 的組件，且參考一個名稱為 myAssembly.dll 的組件，則如果您執行 myAssembly.exe 就會正確繫結。  但是，如果其他應用程式使用方法 <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=fullName> 執行 myAssembly.exe，則當 myAssembly.exe 要求繫結至 "myAssembly" 時，執行階段會判斷 "myAssembly" 已載入。 在這種情況下，myAssembly.dll 並未載入。  因為 myAssembly.exe 並未包含要求的型別，而且會發生 <xref:System.TypeLoadException>。  
  
 若要避免這個問題，請確認構成應用程式的組件並未使用相同的組件名稱，或是將名稱相同的組件放在不同的目錄中。  
  
> [!NOTE]
>  如果將強式名稱的組件放在全域組件快取中，組件的檔案名稱必須符合組件名稱 \(不包括副檔名，如 .exe 或 .dll\)。  例如，如果組件的檔名為 myAssembly.dll，則組件名稱必須是 myAssembly。  僅部署在根應用程式目錄的私用組件可以擁有檔名以外的組件名稱。  
  
## 請參閱  
 [如何：決定組件的完整名稱](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)   
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)   
 [強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)   
 [全域組件快取](../../../docs/framework/app-domains/gac.md)   
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)