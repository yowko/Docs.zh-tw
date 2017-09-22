---
title: "Common Language Runtime 中的類型轉送"
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
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 113ff6decccc190c6638fa04745af425c55c6c0b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# Common Language Runtime 中的類型轉送
型別轉送可讓您將某種型別移到其他組件，而不需重新編譯使用原始組件的應用程式。  
  
 例如，假設某應用程式在名為 `Utility.dll` 的組件內使用了 `Example` 類別。  `Utility.dll` 的開發人員可能決定要重構該組件，而在過程中可能會將 `Example` 類別移到另一個組件。  如果以新版的 `Utility.dll` 和其附屬的組件取代了舊版的 `Utility.dll`，則使用 `Example` 類別的應用程式將無法執行，因為該應用程式無法在新版的 `Utility.dll` 內找到 `Example` 類別。  
  
 `Utility.dll` 的開發人員可以使用 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 屬性 \(Attribute\) 來轉送 `Example` 類別的要求，以避免這種情形發生。  如果已將此屬性套用到新版的 `Utility.dll`，則 `Example` 類別的要求會轉送到目前包含該類別的組件。  現有的應用程式可繼續正常運作，而不需要重新編譯。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，您無法轉送以 Visual Basic 撰寫之組件的型別，  不過，以 Visual Basic 撰寫的應用程式可以使用轉送的型別。  也就是說，如果應用程式使用了以 C\# 或 C\+\+ 撰寫的組件，並且將該組件中的型別轉送到另一個組件，則 Visual Basic 應用程式便可以使用該轉送的型別。  
  
## 轉送型別  
 轉送型別需要進行四個步驟：  
  
1.  將型別的原始程式碼從原始組件移到目的組件。  
  
2.  在用於找出型別的組件中，為移動的型別加入 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>。  下列程式碼會示範已移動之 `Example` 型別的屬性 \(Attribute\)。  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  編譯目前包含此型別的組件。  
  
4.  重新編譯用於找出此型別的組件，其中包含目前包含此型別之組件的參考。  例如，如果您正從命令列編譯 C\# 檔案，請使用 [\/reference \(Import Metadata\)](../Topic/-reference%20\(C%23%20Compiler%20Options\).md) 選項來指定包含此型別的組件。  在 C\+\+ 中，於原始程式檔 \(Source File\) 內使用 [\#using](../Topic/%23using%20Directive%20\(C++\).md) 指示詞可指定包含此型別的組件。  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [型別轉送 (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)   
 [#using 指示詞](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)

