---
title: "How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "procedures, parameters"
  - "procedure overloading, indefinite number of parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, overloading"
  - "procedures, multiple versions"
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

如果程序擁有 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 參數，就無法定義採用一維陣列當做參數陣列的多載版本。  如需詳細資訊，請參閱[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)中的＜ParamArray 參數的隱含多載＞一節。  
  
### 若要多載可接受變動數目之參數的程序  
  
1.  確定程序和呼叫程式碼邏輯在多載版本中的好處，會比在 `ParamArray` 參數中的還多。  請參閱[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)中的＜多載和參數陣列＞一節。  
  
2.  決定程序在參數清單的變數部分中，應該接受的提供值數目。  這可能包含沒有值的情況，也可能只有單一的一維陣列。  
  
3.  對於每一個提供值的可接受數目，撰寫 `Sub` 或 `Function` 宣告陳述式來定義對應的參數清單。  不要在這個多載版本中使用 `Optional` 或 `ParamArray` 關鍵字。  
  
4.  在每個宣告中，於 `Sub` 或 `Function` 關鍵字的前面加上 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) 關鍵字。  
  
5.  遵循每一個宣告來撰寫程序程式碼，以便在呼叫程式碼提供與該宣告的參數清單相對應的值時，執行該程式碼。  
  
6.  請視需要以 `End Sub` 或 `End Function` 陳述式來結束每個程序。  
  
## 範例  
 下列範例顯示 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 參數所定義的程序，然後顯示相等的多載程序集。  
  
 [!CODE [VbVbcnProcedures#69](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#69)]  
  
 [!CODE [VbVbcnProcedures#70](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#70)]  
  
 對於這類擁有採用一維陣列當做參數陣列的參數清單之程序，您無法多載。  然而，您可以使用其他隱含多載的簽章。  下面宣告可說明這點。  
  
 [!CODE [VbVbcnProcedures#71](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#71)]  
  
 多載版本的程式碼不必測試呼叫程式碼是否提供一或多個 `ParamArray` 參數值；若提供則顯示數目。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會將控制權傳遞給符合呼叫引數清單的版本。  
  
## 編譯程式碼  
 由於含 `ParamArray` 參數的程序等於一組多載版本，所以只要程序的參數清單與其中任何隱含多載相對應，您就無法多載該程序。  如需詳細資訊，請參閱[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)。  
  
## .NET Framework 安全性  
 只要處理可能是無限大的陣列，就會有導致應用程式內部容量滿溢的風險。  如果接受參數陣列，就應該測試呼叫程式碼傳給它的陣列長度，若長度對應用程式而言太大，請執行適當的步驟。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../Topic/How%20to:%20Call%20an%20Overloaded%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)