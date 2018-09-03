---
title: Null 條件運算子 (C# 和 Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: f00d5e489931d9c1172a21ee5f0d3e3d0a6f4a4e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408994"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. and ?[] Null 條件運算子 (C# 和 Visual Basic)
在執行成員存取 (`?.`) 或索引 (`?[]`) 運算之前，測試左運算元的值是否為 null；如果左運算元評估為 `null`，則傳回 `null`。 

這些運算子可協助您撰寫較少的程式碼來處理 Null 檢查，特別是遞減至資料結構。  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 Null 條件運算子會執行最少運算。  如果條件式成員存取和索引作業鏈結中的一項作業傳回 Null，則鏈結的其餘部分會停止執行。  在下列範例中，如果 `A`、`B` 或 `C` 的計算結果為 Null，則不會執行 `E`。
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Null 條件成員存取的另一個用法是，使用更少的程式碼以執行緒安全的方式叫用委派。  舊方法需要如下的程式碼：  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 新方法則更簡單：  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 新的方法可以保障執行緒安全，因為編譯器產生的程式碼只會評估 `PropertyChanged` 一次，並將結果保留在暫存變數中。 由於沒有 Null 條件式委派引動過程語法 `PropertyChanged?(e)`，因此您必須明確呼叫 `Invoke` 方法。  
  
## <a name="language-specifications"></a>語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 如需詳細資訊，請參閱 [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)。  
  
## <a name="see-also"></a>請參閱

- [?? (Null 聯合運算子)](null-coalescing-operator.md)  
- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [Visual Basic 程式設計手冊](../../../visual-basic/programming-guide/index.md)
