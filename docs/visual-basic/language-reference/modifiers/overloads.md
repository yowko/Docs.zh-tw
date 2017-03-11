---
title: "Overloads (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Overloads"
  - "Overloads"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Overloads keyword"
  - "hiding by signature"
  - "Shadows keyword"
  - "signature, hiding by"
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Overloads (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定屬性或程序會重新宣告一或多個同名的現有屬性或程序。  
  
## 備註  
 *多載*是一種作法，可將多個定義提供給相同範圍中指定的屬性或程序名稱。  利用不同的簽章宣告屬性或程序，有時稱為*依簽章隱藏*。  
  
## 規則  
  
-   **宣告內容。** 您只能在屬性或程序宣告陳述式中使用 `Overloads`。  
  
-   **結合的修飾詞。** 您不能在相同的程序宣告中同時指定 `Overloads` 與 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
-   **必要的差異。** 此宣告中的*簽章*必須與其多載的每個屬性或程序之簽章不同。  簽章包含屬性或程序名稱，以及下列項目：  
  
    -   參數的數目  
  
    -   參數的順序  
  
    -   參數的資料類型  
  
    -   類型參數的數目 \(適用於泛型程序\)  
  
    -   傳回類型 \(僅適用於轉換運算子程序\)  
  
     所有多載必須有相同的名稱，但每個多載的名稱在一或多個上述方面中必須和其他多載不同。  這可讓編譯器在程式碼呼叫屬性或程序時可識別要使用的版本。  
  
-   **不允許的差異。** 變更下列一或多個項目，對於多載屬性或程序是無效的，因為它們屬於簽章：  
  
    -   是否傳回值 \(適用於程序\)  
  
    -   傳回值的資料類型 \(除了轉換運算子之外\)  
  
    -   參數或類型參數的名稱  
  
    -   類型參數上的條件約束 \(適用於泛型程序\)  
  
    -   參數修飾詞關鍵字 \(例如 `ByRef` 或 `Optional`\)  
  
    -   屬性或程序修飾詞關鍵字 \(例如 `Public` 或 `Shared`\)  
  
-   **選擇性修飾詞。** 當您在相同類別中定義多個多載的屬性或程序時，您不必使用 `Overloads` 修飾詞。  不過，如果您在其中一個宣告中使用 `Overloads`，您必須在全部的宣告中使用它。  
  
-   **Shadowing 和多載。** `Overloads` 也可用來遮蔭基底類別中的現有成員或多載成員集合。  以此方式使用 `Overloads` 時，即表示您會宣告同名的屬性或方法和相同的參數清單作為基底類別成員，而且您並未提供 `Shadows` 關鍵字。  
  
 如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C\#。  
  
 `Overloads` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)