---
title: "Procedure Overloading (Visual Basic) | Microsoft Docs"
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
  - "signatures"
  - "Overloads keyword"
  - "hiding by signature"
  - "Visual Basic code, procedures"
  - "procedures, signatures for"
  - "procedures, overloading"
  - "procedures, multiple versions"
  - "parameters, lists"
  - "signatures, procedure"
  - "parameter lists"
  - "Visual Basic code, parameter lists"
  - "Shadows keyword"
  - "procedure overloading"
  - "procedures, parameter lists"
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Procedure Overloading (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

將程序「*多載化*」\(Overloading\)，表示使用同一個名稱但不同的參數清單，定義多個版本的程序。  多載化的目的是定義數個密切相關的程序版本，而不需以名稱區隔它們。  您可以修改參數清單以達到這個目的。  
  
## 多載化規則  
 當您多載化一個程序時，可套用下列規則：  
  
-   **相同名稱**：  每一個多載化版本必須使用相同的程序名稱。  
  
-   **不同的簽章**：  每一個多載化版本至少必須在下列其中一方面不同於其他多載化版本：  
  
    -   參數的數目  
  
    -   參數的順序  
  
    -   參數的資料型別  
  
    -   型別參數的數目 \(適用於泛型程序\)  
  
    -   傳回型別 \(僅適用於轉換運算子\)  
  
     當前述項目與程序名稱搭配使用時，總稱為程序的「*簽章*」\(Signature\)。  呼叫多載程序時，編譯器會使用簽章來檢查呼叫是否正確符合定義。  
  
-   **不屬於簽章一部分的項目**：  您無法不改變簽章而多載化一個程序。  尤其無法只改變下列一個或幾個項目以多載化一個程序：  
  
    -   程序修飾詞關鍵字，例如 `Public`、`Shared` 和 `Static`  
  
    -   參數或型別參數名稱  
  
    -   型別參數限制 \(適用於泛型程序\)  
  
    -   參數修飾詞關鍵字，如 `ByRef` 和 `Optional`  
  
    -   是否傳回值  
  
    -   傳回值的資料型別 \(轉換運算子除外\)。  
  
     上一張清單內的項目不是簽章的一部分。  雖然無法用它們來區隔多載版本，不過您可在已按簽章適當區隔的多載版本中，改變這些項目。  
  
-   **晚期繫結引數**：  如果您要將晚期繫結物件變數傳遞到多載版本，必須將適當的參數宣告為 <xref:System.Object>。  
  
## 程序的多個版本  
 假設您根據客戶的收支來撰寫一個 `Sub` 程序以公佈其異動，而且您希望可以用名稱或帳號代表該客戶。  要做到這一點，您可以定義兩個不同的 `Sub` 程序，如下列範例所示：  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### 多載版本  
 另一個替代方式是多載化單一程序名稱。  您可以使用 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) 關鍵字來為每一個參數清單定義該程序的版本，如下所示：  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### 其他多載  
 如果您也想以 `Decimal` 或 `Single` 接受交易數量，可以進一步多載化 `post` 以允許這個變化。  如果您在上一個範例中對每一個多載化這麼做，就會得到四個有相同名稱，但不同簽章的 `Sub` 程序。  
  
## 多載化的優點  
 多載化一個程序的好處在於呼叫的彈性。  若要使用在上一個範例中宣告的 `post` 程序，呼叫程式碼可以用 `String` 或 `Integer` 取得客戶識別資訊，不論哪一種方式您都可以呼叫相同的程序。  下面這個範例可說明這點：  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Visual Basic 中的泛型類型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)