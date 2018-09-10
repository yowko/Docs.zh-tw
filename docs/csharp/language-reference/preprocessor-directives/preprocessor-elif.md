---
title: '#elif (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 423cedfb947964172a6e06d54a6dd3c76d91e9f3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864424"
---
# <a name="elif-c-reference"></a>#elif (C# 參考)
`#elif` 可讓您建立複合條件指示詞。 如果前面的 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 和任何前面的選擇性 `#elif` 指示詞運算式都不是評估為 `true`，就會評估 `#elif` 運算式。 如果 `#elif` 運算式評估為 `true`，編譯器會評估 `#elif` 與下一個條件指示詞之間的所有程式碼。 例如:   
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 您可以使用 `==` (相等)、`!=` (不相等)、`&&` (和) 以及 `||` (或) 運算子來評估多個符號。 您也可以使用括弧來將符號和運算子分組。  
  
## <a name="remarks"></a>備註  
 `#elif` 相當於使用：  
  
```csharp
#else  
#if  
```  
  
 使用 `#elif` 更為簡單，因為每個 `#if` 都需要 [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)，而 `#elif` 可以在沒有相符 `#endif` 的情況下使用。  
  
 如需如何使用 `#elif` 的範例，請參閱 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)
