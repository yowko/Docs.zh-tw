---
title: '#endif - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 13b43919b666dcc8c5adfc3490eaad73960547ae
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243893"
---
# <a name="endif-c-reference"></a>#endif (C# 參考)
`#endif` 指定條件指示詞的結尾，而其開始於 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞。 例如，套用至物件的  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>備註  
 以 `#if` 指示詞開頭的條件指示詞必須明確地以 `#endif` 指示詞終止。 如需如何使用 `#endif` 的範例，請參閱 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)
