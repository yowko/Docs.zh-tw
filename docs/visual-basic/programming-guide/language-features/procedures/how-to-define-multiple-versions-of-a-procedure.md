---
title: "How to: Define Multiple Versions of a Procedure (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedures, overloading"
  - "procedures, multiple versions"
  - "procedure overloading, multiple versions"
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Define Multiple Versions of a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以利用「*多載化*」\(Overloading\) 來定義多種版本的程序，在每個版本中使用相同的名稱但不同的參數清單。  多載化的目的是定義數個密切相關的程序版本，而不需以名稱區隔它們。  
  
 如需詳細資訊，請參閱[Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
### 若要定義多個程序版本  
  
1.  對於您想定義的每個程序版本，撰寫 `Sub` 或 `Function` 宣告陳述式。  在每個宣告中都使用相同的程序名稱。  
  
2.  在每個宣告的 `Sub` 或 `Function` 關鍵字前面加上 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) 關鍵字。  可在宣告中選擇性省略 `Overloads`，但如果您將它納入任一宣告中，就必須將它納入每個宣告中。  
  
3.  在每個宣告陳述式後面，撰寫程序程式碼以處理特定情況，在該情況中呼叫程式碼會提供與該版本之參數清單相符的引數。  您不必測試呼叫程式碼所提供的參數。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會將控制權傳遞給符合的程序版本。  
  
4.  視情況使用 `End Sub` 或 `End Function` 陳述式來結束每個程序版本。  
  
## 範例  
 下列範例會定義 `Sub` 程序，以針對客戶平衡來張貼交易。  它會使用 `Overloads` 關鍵字來定義兩個版本的程序：一個是依名稱接受客戶，而另一個是依帳號接受客戶。  
  
 [!CODE [VbVbcnProcedures#72](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#72)]  
  
 呼叫程式碼可以 `String` 或 `Integer` 取得客戶識別，然後將相同的呼叫陳述式用於任一情況下。  
  
 如需如何呼叫這些 `post` 程序版本的詳細資訊，請參閱 [How to: Call an Overloaded Procedure](../Topic/How%20to:%20Call%20an%20Overloaded%20Procedure%20\(Visual%20Basic\).md)。  
  
## 編譯程式碼  
 確定每個多載版本的程序名稱都相同，但參數清單不同。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)