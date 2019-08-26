---
title: '#elif - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: b04db4bd23a459043efec59b8ebf9d322defbcf7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608593"
---
# <a name="elif-c-reference"></a>#elif (C# 參考)
`#elif` 可讓您建立複合條件指示詞。 如果前面的 [#if](./preprocessor-if.md) 和任何前面的選擇性 `#elif` 指示詞運算式都不是評估為 `true`，就會評估 `#elif` 運算式。 如果 `#elif` 運算式評估為 `true`，編譯器會評估 `#elif` 與下一個條件指示詞之間的所有程式碼。 例如：  
  
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
  
 使用 `#elif` 更為簡單，因為每個 `#if` 都需要 [#endif](./preprocessor-endif.md)，而 `#elif` 可以在沒有相符 `#endif` 的情況下使用。  
  
 如需如何使用 `#elif` 的範例，請參閱 [#if](./preprocessor-if.md)。  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 前置處理器指示詞](./index.md)
