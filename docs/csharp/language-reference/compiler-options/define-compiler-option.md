---
title: "-define (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 273437a4250a393274fa20ad4c02b61dce35ed34
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-define-c-compiler-options"></a>-define (C# 編譯器選項)
**-define** 選項會將 `name` 定義為程式中所有原始程式碼檔的符號。  
  
## <a name="syntax"></a>語法  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>引數  
 `name`, `name2`  
 您要定義的一或多個符號之名稱。  
  
## <a name="remarks"></a>備註  
 **-define** 選項的作用與使用 [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 前置處理器指示詞相同，不同之處在於編譯器選項對專案中的所有檔案都有效。 直到原始程式檔中的 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 指示詞移除符號的定義之前，符號在原始程式檔中都會維持已定義狀態。 使用 -define 選項時，某個檔案中的 `#undef` 指示詞不會對專案中的其他原始程式碼檔造成影響。  
  
 您可以使用此選項建立的符號，搭配 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)、[#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 和 [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)，有條件地編譯原始程式檔。  
  
 **-d** 是 **-define** 的簡短形式。  
  
 您可以使用分號或逗號分隔符號名稱，以 **-define** 定義多個符號。 例如:   
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 C# 編譯器本身不會定義任何您可以在原始程式碼中使用的符號或巨集；所有符號定義都必須是使用者定義。  
  
> [!NOTE]
>  C# `#define` 不允許指定數值給符號，這點和 C++ 語言相同。 例如，`#define` 不能用來建立巨集或定義常數。 如果您需要定義常數，請使用 `enum` 變數。 如果您想要建立 C++ 樣式巨集，請考慮替代項目，例如泛型。 由於巨集非常可能發生錯誤，因此 C# 不允許使用巨集，而是提供較為安全的替代項目。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  在 [建置] 索引標籤的 [條件式編譯的符號] 方塊中，輸入要定義的符號。 例如，如果您想要使用下列程式碼範例，只要在文字方塊中鍵入 `xx` 即可。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>。  
  
## <a name="example"></a>範例  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
