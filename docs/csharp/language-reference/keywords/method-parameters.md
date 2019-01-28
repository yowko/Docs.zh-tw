---
title: 方法參數 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 72917d356ed0fce96502faeef68494c7fdcb214f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564756"
---
# <a name="method-parameters-c-reference"></a>方法參數 (C# 參考)

為沒有 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 的方法宣告之參數，會以值的方式傳遞到呼叫的方法。 該值可以在方法中進行變更，但控制權傳回給呼叫程序時，不會保留已變更值。 使用方法參數關鍵字，即可變更此行為。  
  
 本節描述在您宣告方法參數時可以使用的關鍵字：  
  
-   [params](../../../csharp/language-reference/keywords/params.md) 指定這個參數可以接受可變數目的引數。
  
-   [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) 指定這個參數是傳址方式傳遞，但只會由所呼叫的方法讀取。
  
-   [ref](../../../csharp/language-reference/keywords/ref.md) 指定這個參數是傳址方式傳遞，且可以由所呼叫的方法讀取或寫入。
  
-   [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 指定這個參數是傳址方式傳遞，且由所呼叫的方法寫入。
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)
