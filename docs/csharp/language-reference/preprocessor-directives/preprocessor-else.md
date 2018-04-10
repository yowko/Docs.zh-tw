---
title: '#else (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c3468d35a6e45c06f46fe8671708ce01a3cc7b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="else-c-reference"></a>#else (C# 參考)
`#else` 可讓您建立複合條件指示詞，如此，如果前面的 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 或 (選擇性) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 指示詞中沒有運算式為 `true`，則編譯器會評估 `#else` 與後續 `#endif` 之間的所有程式碼。  
  
## <a name="remarks"></a>備註  
 [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) 必須是 `#else` 後面的下一個前置處理器指示詞。 如需如何使用 `#else` 的範例，請參閱 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)
