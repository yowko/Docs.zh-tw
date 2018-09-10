---
title: Common Language Runtime 中的類型轉送
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d25bac953ff68422a1dddc54bdb01b4b4f241cbb
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275713"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Common Language Runtime 中的類型轉送
型別轉送可讓您將型別移至另一個組件，而無須重新編譯使用原始組件的應用程式。  
  
 例如，假設應用程式在名為 `Utility.dll` 的組件中使用 `Example`類別。 `Utility.dll` 的開發人員可能會決定重構組件，在流程中可能會將 `Example` 類別移至另一個組件。 如果舊版的 `Utility.dll` 被新版的 `Utility.dll` 和其隨附組件取代，使用 `Example` 類別的應用程式會失敗，因為它在新版 `Utility.dll` 中找不到 `Example` 類別。  
  
 `Utility.dll` 的開發人員可以使用 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 屬性轉送 `Example` 類別要求，避免這個狀況。 如果屬性已套用至新版的 `Utility.dll`，`Example` 類別的要求會轉送給現在包含類別的組件。 現有的應用程式會繼續正常運作，而不必重新編譯。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，您無法從在 Visual Basic 中撰寫的組件轉送型別。 不過，在 Visual Basic 中撰寫的應用程式可以使用轉送型別。 也就是說，如果應用程式使用以 C# 或 C++ 編碼的組件，且來自該組件的型別轉送至另一個組件，則 Visual Basic 應用程式可以使用轉送型別。  
  
## <a name="forwarding-types"></a>轉送型別  
 轉送型別有四個步驟︰  
  
1.  將型別的原始程式碼從原始組件移至目的地組件。  
  
2.  在使用所尋找類型的組件中，為移動的類型新增 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>。 下列程式碼示範已移動之名為 `Example` 的型別的屬性。  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  編譯現在包含型別的組件。  
  
4.  重新編譯型別曾經所在的組件，具有現在包含型別之組件的參考。 例如，如果您正在從命令列編譯 C# 檔案，請使用 [/reference (C# 編譯器選項) ](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) 選項來指定包含型別的組件。 在 C++ 中，在來源檔案中使用 [#using](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) 指示詞以指定包含型別的組件。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [類型轉送 (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)  
 [#using 指示詞](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
