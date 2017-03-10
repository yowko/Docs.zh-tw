---
title: "Troubleshooting Arrays (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "troubleshooting arrays"
  - "arrays [Visual Basic], initialization errors"
  - "troubleshooting Visual Basic, arrays"
  - "arrays [Visual Basic], compilation errors"
  - "arrays [Visual Basic], declaration errors"
  - "arrays [Visual Basic], troubleshooting"
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Troubleshooting Arrays (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本頁面會列出一些使用陣列時所發生的常見問題。  
  
## 宣告和初始化陣列時發生編譯錯誤  
 編譯錯誤是因為不了解宣告、建立和初始化陣列的規則所引起。  最常見的錯誤原因如下：  
  
-   在陣列變數宣告中指定維度 \(Dimension\) 長度之後，才提供 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) 子句。  下列程式碼行會顯示這種類型的無效宣告。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   對不規則陣列 \(Jagged Array\) 的多個最上層陣列指定維度長度。  下列程式碼行會顯示這種類型的無效宣告。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   指定項目值時省略 `New` 關鍵字。  下列程式碼行會顯示這種類型的無效宣告。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   提供 `New` 子句而未使用大括號 \(`{}`\)。  下列程式碼行會顯示這種類型的無效宣告。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## 存取超出界限的陣列  
 初始化陣列的處理序會指定每個維度的上限 \(Upper Bound\) 和下限。  陣列項目的每個存取權限都必須對每個維度指定有效的索引或註標 \(Subscript\)。  如果索引低於它的下限或高於它的上限，則會產生 <xref:System.IndexOutOfRangeException> 例外狀況。  編譯器 \(Compiler\) 無法偵測到這種錯誤，因此會在執行階段發生錯誤。  
  
### 決定界限  
 例如，如果其他元件將陣列傳遞至程式碼做為程序引數，則您不會知道該陣列的大小或它的維度長度。  在嘗試存取任何項目之前，一定要先判斷每個陣列維度的上限。  如果已使用 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] `New` 子句以外的方法建立陣列，下限可能是 0 以外的值，這也是決定該下限最安全的值。  
  
### 指定維度  
 判斷多維陣列的界限時，請特別注意指定維度的方法。  <xref:System.Array.GetLowerBound%2A> 和 <xref:System.Array.GetUpperBound%2A> 方法的 `dimension` 參數是以零起始，而 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> 和 <xref:Microsoft.VisualBasic.Information.UBound%2A> 函式的 `Rank` 參數則是以 1 起始。  
  
## 請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)