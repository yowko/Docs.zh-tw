---
title: Common Language Runtime 中的類型轉送
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160361"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Common Language Runtime 中的類型轉送
型別轉送可讓您將型別移至另一個組件，而無須重新編譯使用原始組件的應用程式。  
  
 例如，假設應用程式在名為*Utility*的元件中使用 `Example` 類別。 *Utility*的開發人員可能會決定重構元件，而在進程中，他們可能會將 `Example` 類別移至另一個元件。 如果舊版的*公用程式 .dll 和其*隨附元件取代了舊版本的*utility* ，使用 `Example` 類別的應用程式會失敗，因為它找不到新版*公用程式 .dll*中的 `Example` 類別。  
  
 *Utility*的開發人員可以使用 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 屬性來轉送 `Example` 類別的要求，藉以避免這種情況。 如果屬性已套用至新版本的*Utility*，則會將 `Example` 類別的要求轉送至現在包含類別的元件。 現有的應用程式會繼續正常運作，而不必重新編譯。  
  
> [!NOTE]
> 在 .NET Framework 2.0 版中，您無法從在 Visual Basic 中撰寫的組件轉送型別。 不過，在 Visual Basic 中撰寫的應用程式可以使用轉送型別。 也就是說，如果應用程式使用以 C# 或 C++ 編碼的組件，且來自該組件的型別轉送至另一個組件，則 Visual Basic 應用程式可以使用轉送型別。  
  
## <a name="forward-types"></a>轉送類型  
 轉送型別有四個步驟︰  
  
1. 將型別的原始程式碼從原始組件移至目的地組件。  

2. 在使用所尋找類型的組件中，為移動的類型新增 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>。 下列程式碼示範已移動之名為 `Example` 的型別的屬性。  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. 編譯現在包含型別的組件。  

4. 重新編譯型別曾經所在的組件，具有現在包含型別之組件的參考。 例如，如果您要從命令列C#編譯檔案，請使用[-reference （C#編譯器選項）](../../csharp/language-reference/compiler-options/reference-compiler-option.md)選項來指定包含該類型的元件。 在 C++ 中，在來源檔案中使用 [#using](/cpp/preprocessor/hash-using-directive-cpp) 指示詞以指定包含型別的組件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [類型轉送（C++/cli）](/cpp/windows/type-forwarding-cpp-cli)
- [#using 指示詞](/cpp/preprocessor/hash-using-directive-cpp)
