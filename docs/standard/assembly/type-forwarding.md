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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160361"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Common Language Runtime 中的類型轉送
型別轉送可讓您將型別移至另一個組件，而無須重新編譯使用原始組件的應用程式。  
  
 例如，假設應用程式在名為`Example`*實用程式.dll*的程式集中使用 類。 *實用程式.dll*的開發人員可能會決定重構程式集，在此過程中，他們可能會將`Example`類移動到另一個程式集。 如果*舊版本的實用程式.dll*替換為新版本的*實用程式.dll*及其配套程式集，則使用`Example`該類的應用程式將失敗，因為它無法在新版本的`Example`*實用程式.dll*中定位類。  
  
 *實用程式.dll*的開發人員可以通過使用 屬性`Example`<xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>轉發類的請求來避免這種情況。 如果該屬性已應用於新版本的*實用程式.dll，* 則`Example`類的請求將轉發到現在包含該類的程式集。 現有的應用程式會繼續正常運作，而不必重新編譯。  
  
> [!NOTE]
> 在 .NET Framework 2.0 版中，您無法從在 Visual Basic 中撰寫的組件轉送型別。 不過，在 Visual Basic 中撰寫的應用程式可以使用轉送型別。 也就是說，如果應用程式使用以 C# 或 C++ 編碼的組件，且來自該組件的型別轉送至另一個組件，則 Visual Basic 應用程式可以使用轉送型別。  
  
## <a name="forward-types"></a>轉發類型  
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

4. 重新編譯型別曾經所在的組件，具有現在包含型別之組件的參考。 例如，如果要從命令列編譯 C# 檔，請使用[-參考 （C# 編譯器選項）選項](../../csharp/language-reference/compiler-options/reference-compiler-option.md)指定包含該類型的程式集。 在 C++ 中，在來源檔案中使用 [#using](/cpp/preprocessor/hash-using-directive-cpp) 指示詞以指定包含型別的組件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [類型轉發（C++/CLI）](/cpp/windows/type-forwarding-cpp-cli)
- [#using指令](/cpp/preprocessor/hash-using-directive-cpp)
