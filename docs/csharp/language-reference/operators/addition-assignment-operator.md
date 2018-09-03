---
title: += 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bd0997ec5b7d79a41e01f9c2b17533293e412c1e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468405"
---
# <a name="-operator-c-reference"></a>+= 運算子 (C# 參考)
加法指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `+=` 指派運算子的運算式，例如  
  
```csharp  
x += y  
```  
  
 相當於  
  
```csharp  
x = x + y  
```  
  
 但只會評估 `x` 一次。 [+ 運算子](../../../csharp/language-reference/operators/addition-operator.md)的意義隨 `x` 和 `y` 的類型而定 (加上數值運算元、字串運算元串連等等)。  
  
 無法直接多載 `+=` 運算子，但使用者定義型別可以多載 [+ 運算子](../../../csharp/language-reference/operators/addition-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
 `+=` 運算子也可以用來指定回應事件所呼叫的方法，這類方法稱之為事件處理常式。 在此內容中使用 `+=` 運算子，稱之為「訂閱事件」。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)和[委派](../../../csharp/programming-guide/delegates/index.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
