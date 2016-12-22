---
title: "How to: Assign One Array to Another Array (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "covariance, arrays"
  - "arrays [Visual Basic], assigning"
  - "arrays [Visual Basic], covariance"
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Assign One Array to Another Array (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

由於陣列就是物件，所以陣列可以像其他物件型別一樣在指派陳述式 \(Assignment Statement\) 中使用。  陣列變數會保留構成陣列元素、陣序規範及長度資訊的資料指標，以及僅複製此指標的指派。  
  
### 將陣列指派給另一個陣列  
  
1.  請確定兩個陣列均具有相同的陣序規範 \(維度數目\) 及相容的元素資料型別。  
  
2.  使用標準指派陳述式 \(Assignment Statement\)，將來源陣列指定給目的陣列。  請勿在陣列名稱之後加上括弧。  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 當您將一個陣列指派給另一陣列時，會套用下列規則 \(Rule\)：  
  
-   **相同陣序規範**： 目的陣列的陣序規範 \(維度數目\) 必須與來源陣列相同。  
  
     如果兩個陣列的陣序規範相等的話，維度並不一定會相等。  指定維度中的元素數可能會在指派期間變更。  
  
-   **元素型別**： 兩個陣列都必須具有「*參考型別*」\(Reference Type\) 元素，或是兩個陣列都必須具有「*實值型別*」\(Value Type\) 元素。  如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
    -   如果兩個陣列都具有實值型別元素，則元素資料型別必須完全相同。  唯一的例外狀況 \(Exception\) 是，您可以將 `Enum` 元素的陣列指派給 `Enum` 的基底型別 \(Base Type\) 陣列。  
  
    -   如果兩個陣列都具有參考型別元素，則來源元素型別必須衍生自目的元素型別。  在此情況下，兩個陣列的繼承 \(Inheritance\) 關係與其元素相同。  這稱為「*陣列共異變數*」\(Array Covariance\)。  
  
 如果違反上述規則，例如，資料型別不相容或是陣序規範不相等，編譯器 \(Compiler\) 就會報告錯誤。  您可以將錯誤處理加入您的程式碼，確保陣列在指派前都是相容的。  如果您想避免擲回例外狀況，也可以使用 [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) 關鍵字。  
  
## 請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)