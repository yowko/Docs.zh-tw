---
title: "How to: Overload a Procedure that Takes Optional Parameters (Visual Basic) | Microsoft Docs"
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
  - "procedures, parameters"
  - "procedure overloading, optional parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, overloading"
  - "procedures, multiple versions"
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

如果程序有一或多個 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) 參數，則無法定義符合任一其隱含多載的多載版本。  如需詳細資訊，請參閱[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)中的＜選擇性參數的隱含多載＞一節。  
  
## 一個選擇性參數  
  
#### 若要多載採用一個選擇性參數的程序  
  
1.  撰寫將選擇性參數包含在參數清單中的 `Sub` 或 `Function` 宣告陳述式 \(Declaration Statement\)。  不要在這個多載版本中使用 `Optional` 關鍵字。  
  
2.  在 `Sub` 或 `Function` 關鍵字的前面加上 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) 關鍵字。  
  
3.  撰寫呼叫程式碼在提供選擇性引數時所應執行的程序碼。  
  
4.  請視需要以 `End Sub` 或 `End Function` 陳述式來結束程序。  
  
5.  撰寫與第一個宣告相同的第二個宣告陳述式，但它不會將選擇性參數包含在參數清單中。  
  
6.  撰寫呼叫程式碼未提供選擇性引數時所應執行的程序碼。  請視需要以 `End Sub` 或 `End Function` 陳述式來結束程序。  
  
     下列範例會顯示一個有定義選擇性參數的程序、兩個對等的多載程序，而最後是無效和有效多載版本的範例。  
  
     [!CODE [VbVbcnProcedures#59](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#59)]  
  
     [!CODE [VbVbcnProcedures#60](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#60)]  
  
     [!CODE [VbVbcnProcedures#61](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#61)]  
  
## 多個選擇性參數  
 若是有多個選擇性參數的程序，則一般需要兩個以上的多載版本。  例如，如果有兩個選擇性參數，且呼叫程式碼可單獨提供或略過每個參數，則需要四個多載版本，而所提供引數的每個可能組合都會有一個版本。  
  
 當選擇性參數的數目增加時，多載化 \(Overloading\) 的複雜性也會增加。  除非不接受某些引數的組合，否則 N 選擇性參數需要 2 ^ N 個多載版本。  根據程序本質的不同，您可能會發現定義所有多載版本的額外努力會帶來清楚的邏輯。  
  
#### 若要多載採用一個以上之選擇性參數的程序  
  
1.  確定程序邏輯會接受所提供選擇性引數的哪些組合，  如果選擇性參數與另一個選擇性參數具有相依性關係，則可能會引發無法接受的組合。  例如，如果某個參數會接受 \(Accept\) 配偶的姓名，而另一個參數會接受配偶的年齡，則程序邏輯將無法接受提供了年齡卻略過姓名的引數組合。  
  
2.  針對所提供選擇性引數的每個可接受組合，撰寫 `Sub` 或 `Function` 宣告陳述式，用以定義對應的參數清單。  不要使用 `Optional` 關鍵字。  
  
3.  在每個宣告中，於 `Sub` 或 `Function` 關鍵字的前面加上 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) 關鍵字。  
  
4.  在每個宣告後面，撰寫呼叫程式碼在提供與該宣告之參數清單對應的引數清單時，所應執行的程序碼。  
  
5.  請視需要以 `End Sub` 或 `End Function` 陳述式來結束每個程序。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../Topic/How%20to:%20Call%20an%20Overloaded%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)