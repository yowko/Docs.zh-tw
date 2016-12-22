---
title: "Passing Arguments by Value and by Reference (Visual Basic) | Microsoft Docs"
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
  - "ByRef keyword, passing arguments by reference"
  - "Visual Basic code, procedures"
  - "passing arguments, by value or by reference"
  - "ByVal keyword, passing arguments by value"
  - "arguments [Visual Basic], passing by value or by reference"
  - "argument passing, by value or by reference"
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Passing Arguments by Value and by Reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中，您可利用「*傳值*」\(By Value\) 或「*傳址*」\(By Reference\) 方式，將引數傳遞至程序。  這個動作稱為「*傳遞機制*」\(Passing Mechanism\)，它能判斷程序是否能修改在呼叫程式碼中當做引數基礎的程式設計項目。  程序宣告可藉由指定 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 或 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 關鍵字，決定每一個參數的傳遞機制。  
  
## 不同處  
 將引數傳遞到程序時，請注意幾個會相互影響的不同處：  
  
-   基礎程式設計項目是否為可修改。  
  
-   引數本身是否為可修改。  
  
-   引數是否會以傳值或傳址方式傳遞。  
  
-   引數資料型別是實值型別 \(Value Type\) 還是參考型別 \(Reference Type\)。  
  
 如需詳細資訊，請參閱[Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)與[Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## 選擇傳遞機制  
 您應該小心選擇每一個引數的傳遞機制。  
  
-   **保護**：  在兩種傳遞機制之間作選擇時，最重要的標準就是要變更的呼叫變數之公開方式。  傳遞 `ByRef` 引數的好處是程序可以透過該引數將值傳回給呼叫程式碼。  傳遞 `ByVal` 引數的好處是它可以避免變數被程序更改。  
  
-   **效能**：  雖然傳遞機制會影響程式碼的效能，但它的差別通常並不顯著。  其中的一個例外是以 `ByVal` 傳遞的實值型別。  在這種情況下，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會複製引數的整個資料內容。  因此，對於像結構這樣的大型實值型別，以 `ByRef` 方式傳遞比較有效率。  
  
     若為參考型別，則只會複製資料的指標 \(32 位元平台上為四個位元組，64 位元平台上則為八個位元組\)。  因此，您可以在不損害效能的情況下，以傳值方式傳遞 `String` 或 `Object` 型別的引數。  
  
## 決定傳遞機制  
 程序宣告可指定每一個參數的傳遞機制。  呼叫程式碼無法覆寫 `ByVal` 機制。  
  
 如果參數宣告 `ByRef`，呼叫的程式碼可能會強制機制到 `ByVal` 將引數名稱的括號中對的呼叫。  如需詳細資訊，請參閱[How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中的預設值是以值來傳遞引數。  
  
## 以傳值方式傳遞引數的時機  
  
-   如果呼叫程式碼中做為引數基礎的項目是不能修改的項目，請宣告對應參數 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。  沒有程式碼能變更不可修改項目的值。  
  
-   如果基礎項目是可修改的，但您不要程序變更其值，請宣告參數 `ByVal`。  唯有呼叫程式碼可變更以傳值方式傳遞的可修改項目值。  
  
## 以傳址方式傳遞引數的時機  
  
-   如果程序確實需要變更呼叫程式碼中的基礎項目，請宣告對應參數 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。  
  
-   如果須靠程序來變更呼叫程式碼中的基礎項目，才能正確執行程式碼，請宣告參數 `ByRef`。  如果依傳值方式傳遞，或呼叫程式碼用引號括住引數的方式來覆寫 `ByRef` 傳遞機制，則程序呼叫可能會產生未預期的結果。  
  
## 範例  
  
### 描述  
 下列範例說明何時以傳值方式傳遞引數，何時以傳址方式傳遞引數。  程序 `Calculate` 同時擁有 `ByVal` 和 `ByRef`。  假設給予利率 `rate` 與金額 `debt`，程序的任務是要計算套用利率至原始 `debt` 後所產生的 `debt` 新值。  因為 `debt` 是 `ByRef` 參數，所以新的總數會反映在對應到 `debt` 之呼叫程式碼的引數值內。  至於參數 `rate` 則是 `ByVal` 參數，因為 `Calculate` 不應變更其值。  
  
### 程式碼  
 [!CODE [VbVbcnProcedures#74](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#74)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../Topic/How%20to:%20Pass%20Arguments%20to%20a%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)