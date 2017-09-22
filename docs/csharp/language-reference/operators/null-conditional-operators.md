---
title: "Null 條件運算子 (C# 和 Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: 3
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
ms.sourcegitcommit: 6118956a5681ddbeb110f6e01f090b85cdd65089
ms.openlocfilehash: 465a395a33c027132b7890e02d540438096e2073
ms.contentlocale: zh-tw
ms.lasthandoff: 08/23/2017

---
# <a name="null-conditional-operators-c-and-visual-basic"></a>Null 條件運算子 (C# 和 Visual Basic)
在執行成員存取 (`?.`) 或對 (`?[`) 作業編製索引之前，可用來測試是否為 Null。  這些運算子可協助您撰寫較少的程式碼來處理 Null 檢查，特別是遞減至資料結構。  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
  
```  
  
```vb  
Dim length = customers?.Length  ‘’ null if customers is null  
Dim first as Customer = customers?(0);  ‘’ null if customers is null  
Dim count as Integer? = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
  
```  
  
 最後一個範例示範使用最少運算的 Null 條件運算子。  如果條件式成員存取和索引作業鏈結中的一項作業傳回 Null，則鏈結的其餘部分會停止執行。  運算式中優先順序較低的其他作業會繼續進行。  例如，下列程式碼中的 `E` 會在第二行執行，而且 `??` 和 `==` 運算會執行。  在第一行，當左邊評估為非 Null 時，`??` 最少運算和 `E` 不會執行。
  
```vb-c#  
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
  
```  
  
 Null 條件成員存取的另一個用法是，使用更少的程式碼以執行緒安全的方式叫用委派。  舊方法需要如下的程式碼：  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…)  
  
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
  
```  
  
 新方法則更簡單：  
  
```vb-c#  
PropertyChanged?.Invoke(e)  
  
```  
  
 新方法是安全執行緒，因為編譯器會產生程式碼只評估 `PropertyChanged` 一次，並將結果保留在暫存變數中。  
  
 由於沒有 Null 條件式委派引動過程語法 `PropertyChanged?(e)`，因此您必須明確呼叫 `Invoke` 方法。  有太多模稜兩可剖析的情況可能會導致無法呼叫。  
  
## <a name="language-specifications"></a>語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 如需詳細資訊，請參閱 [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)。  
  
## <a name="see-also"></a>另請參閱  
 [?? (Null 聯合運算子)](null-conditional-operator.md)   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)   
 [Visual Basic 程式設計手冊](../../../visual-basic/programming-guide/index.md)
