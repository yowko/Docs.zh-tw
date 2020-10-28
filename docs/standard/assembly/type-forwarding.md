---
title: Common Language Runtime 中的類型轉送
description: 類型轉送可讓您將類型移至另一個 .NET 元件，而不需要重新編譯使用原始元件的應用程式。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: cd166068993fb5d1a5164615de3926a06dda8098
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687662"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Common Language Runtime 中的類型轉送

型別轉送可讓您將型別移至另一個組件，而無須重新編譯使用原始組件的應用程式。  
  
 例如，假設應用程式 `Example` 在名為 *Utility.dll* 的元件中使用類別。 *Utility.dll* 的開發人員可能會決定重構元件，並在程式中將此 `Example` 類別移至另一個元件。 如果舊版的 *Utility.dll* 取代為新版本的 *Utility.dll* 和其附屬元件，則使用類別的應用程式 `Example` 會失敗，因為它 `Example` 在新版本的 *Utility.dll* 中找不到類別。  
  
 *Utility.dll* 的開發人員可以使用屬性轉送類別的要求，來避免這個情況 `Example` <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 。 如果屬性已套用至 *Utility.dll* 的新版本，則會將類別的要求 `Example` 轉送至現在包含類別的元件。 現有的應用程式會繼續正常運作，而不必重新編譯。

## <a name="forward-a-type"></a>轉寄型別

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

4. 重新編譯型別曾經所在的組件，具有現在包含型別之組件的參考。 例如，如果您要從命令列編譯 c # 檔案，請使用 [-reference (c # 編譯器選項) ](../../csharp/language-reference/compiler-options/reference-compiler-option.md) 選項來指定包含型別的元件。 在 C++ 中，在來源檔案中使用 [#using](/cpp/preprocessor/hash-using-directive-cpp) 指示詞以指定包含型別的組件。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [類型轉送 (c + +/CLI) ](/cpp/windows/type-forwarding-cpp-cli)
- [#using 指示詞](/cpp/preprocessor/hash-using-directive-cpp)
