---
title: "Recursive Procedures (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "procedures, that call themselves"
  - "procedures, recursive"
  - "procedures, calling"
  - "recursive procedures"
  - "functions [Visual Basic], calling recursively"
  - "recursion"
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Recursive Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*遞迴*」\(Recursive\) 程序會呼叫自己的程序。  一般而言，這不是撰寫 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式碼最有效的方式。  
  
 下列程序使用遞迴來計算原始引數的階乘：  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## 遞迴程序的考量  
 **限制條件**：  您必須設計遞迴程序，測試至少有一個條件能終止遞迴，也必須能在合理的遞迴呼叫數目內都無法滿足此類條件時進行處理。  除非至少符合一個條件且不會發生失敗，否則程序就可能陷入無限迴圈的高風險。  
  
 **記憶體使用方式**：  應用程式所具備適用於區域變數的空間有限。  每當程序呼叫其本身時，它會使用該空間以外的空間，處理其區域變數的其他複本。  如果這個程序無限地繼續執行，最後會引起 <xref:System.StackOverflowException> 錯誤。  
  
 **效率**：  您幾乎都能取代遞迴迴圈。  迴圈不會有傳遞引數、初始化其他儲存區和傳回值的負荷。  沒有遞迴呼叫，效能可能大幅提升。  
  
 **相互遞迴**：  您或許會觀察到，當兩個程序彼此呼叫時，效能可能很差，甚至造成無限迴圈。  此類設計會與單一遞迴程序呈現相同的問題，但可能更難偵測和偵錯。  
  
 **以括號呼叫**：  當 `Function` 程序遞迴地呼叫其本身時，您必須在程序名稱之後接著括號，即使沒有引數清單也一樣。  否則，函式名稱會被視為代表該函式的傳回值。  
  
 **測試**：  如果您撰寫遞迴程序，則應很謹慎地加以測試，確定它永遠符合部分的限制條件。  您也應該確定不會因過多的遞迴呼叫而將記憶體用完。  
  
## 請參閱  
 <xref:System.StackOverflowException>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [疑難排解例外狀況：System.StackOverflowException](../Topic/Troubleshooting%20Exceptions:%20System.StackOverflowException.md)