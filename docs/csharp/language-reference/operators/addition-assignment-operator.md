---
title: += 運算子 (C# 參考)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192027"
---
# <a name="-operator-c-reference"></a>+= 運算子 (C# 參考)

加法指派運算子。

使用 `+=` 運算子的運算式，例如  

```csharp
x += y
```  

相當於  

```csharp
x = x + y
```  

但只會評估 `x` 一次。
  
針對數值型別，[加法運算子](addition-operator.md) `+` 會計算其運算元的和。 如果其中一或兩個運算元的型別為 [string](../keywords/string.md)，則它會串連其運算元的字串表示。 針對委派型別，`+` 運算子會傳回為其運算元組合的新委派執行個體。

如果使用者定義的型別將[加法運算子](addition-operator.md) `+` [多載](../keywords/operator.md)，則加法指派運算子 `+=` 會隱含地多載。

當您訂閱[事件](../keywords/event.md)時，您也會使用 `+=` 來指定事件處理常式方法。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

下列範例示範 `+=` 運算子的用法：

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [事件](../../programming-guide/events/index.md)
- [委派](../../programming-guide/delegates/index.md)
