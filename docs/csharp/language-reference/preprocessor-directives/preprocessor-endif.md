---
title: "#<a name=\"endif-c-reference\"></a>endif (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#endif'
dev_langs:
- CSharp
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e4c37657a1ca81b7e5403e58123cf630a224b8ec
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="endif-c-reference"></a>#endif (C# 參考)
`#endif` 指定條件指示詞的結尾，而其開始於 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞。 例如：  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>備註  
 以 `#if` 指示詞開頭的條件指示詞必須明確地以 `#endif` 指示詞終止。 如需如何使用 `#endif` 的範例，請參閱 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)

