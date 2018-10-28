---
title: Null 條件運算子 (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: c29362a1e335e18b66821919e266b1ce57774692
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195987"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. 和嗎？（） null 條件運算子 (Visual Basic)

測試的左運算元為 null 的值 (`Nothing`) 之前執行成員存取 (`?.`) 或索引 (`?()`) 作業; 會傳回`Nothing`如果左運算元評估為`Nothing`。 請注意，在通常會傳回實值型別運算式中，null 條件運算子傳回<xref:System.Nullable%601>。

這些運算子可協助您撰寫較少的程式碼來處理 null 檢查，尤其是遞減至資料結構。 例如: 

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

相較之下，這些運算式沒有 null 條件運算子的第一個替代程式碼是：

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Null 條件運算子會執行最少運算。  如果在條件式成員存取和索引作業鏈結中的一項作業會傳回 Nothing，就會停止執行在鏈結的其餘部分。  在下列範例中，c （e） 不會評估如果`A`， `B`，或`C`是否評估為 Nothing。

```vb
A?.B?.C?(E);
```

Null 條件成員存取的另一個用途是要以更少的程式碼以執行緒安全的方式叫用委派。  舊方法需要如下的程式碼：  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

新方法則更簡單：  

```vb
PropertyChanged?.Invoke(…)
```

新的方法可以保障執行緒安全，因為編譯器產生的程式碼只會評估 `PropertyChanged` 一次，並將結果保留在暫存變數中。 由於沒有 Null 條件式委派引動過程語法 `PropertyChanged?(e)`，因此您必須明確呼叫 `Invoke` 方法。  

## <a name="see-also"></a>另請參閱

- [運算子 (Visual Basic)](index.md)
- [Visual Basic 程式設計手冊](../../../visual-basic/programming-guide/index.md)
- [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)  
