---
title: "Expression is a value and therefore cannot be the target of an assignment | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30068"
  - "vbc30068"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30068"
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Expression is a value and therefore cannot be the target of an assignment
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

陳述式 \(Statement\) 嘗試指派運算式的值。  在執行階段，您只能指派可寫入變數、屬性，或是陣列元素的值。  下列範例將說明此錯誤如何發生。  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 類似的範例可以套用至屬性和陣列元素。  
  
 **間接存取。** 透過實值型別 \(Value Type\) 的間接存取也會產生此錯誤。  請參考下列程式碼範例，此範例嘗試藉由 <xref:System.Windows.Forms.Control.Location%2A> 間接進行存取並設定 <xref:System.Drawing.Point> 的值。  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 以上範例的最後一行失敗，因為它只針對 <xref:System.Windows.Forms.Control.Location%2A> 屬性傳回的 <xref:System.Drawing.Point> 結構建立臨時配置。  結構是一個實值型別，而暫存結構在陳述式執行後不會保留。  這個問題會藉由宣告及使用 <xref:System.Windows.Forms.Control.Location%2A> 的變數而解決，它為 <xref:System.Drawing.Point> 結構建立更為長久的配置。  下列範例列出的程式碼，可以用來取代前述範例中最後的陳述式。  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **錯誤 ID**：BC30068  
  
### 若要更正這個錯誤  
  
-   如果陳述式指派值給運算式，請以單一的可寫入變數、屬性或陣列元素取代運算式。  
  
-   如果此陳述式間接存取實值型別 \(通常是結構\)，請建立一個變數以保留此實值型別。  
  
-   指派適當的結構 \(或其他實值型別\) 至此變數。  
  
-   使用此變數存取屬性，以指派屬性的值。  
  
## 請參閱  
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)