---
title: '#endif - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712542"
---
# <a name="endif-c-reference"></a>#endif (C# 參考)
`#endif` 指定條件指示詞的結尾，而其開始於 [#if](./preprocessor-if.md) 指示詞。 例如，  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>備註  
 以 `#if` 指示詞開頭的條件指示詞必須明確地以 `#endif` 指示詞終止。 如需如何使用 `#endif` 的範例，請參閱 [#if](./preprocessor-if.md)。  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 預處理器指令](./index.md)
