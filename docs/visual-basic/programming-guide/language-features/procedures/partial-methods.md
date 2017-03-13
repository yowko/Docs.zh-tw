---
title: "Partial Methods (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.PartialMethod"
  - "PartialMethod"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "custom logic into code [Visual Basic]"
  - "partial methods [Visual Basic]"
  - "partial, methods [Visual Basic]"
  - "methods [Visual Basic], partial methods"
  - "inserting custom logic into code"
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Partial Methods (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

開發人員可以利用部分方法在程式碼中插入自訂邏輯。  通常，這個程式碼是在設計工具所產生的類別 \(Class\) 中。  部分方法定義於程式碼產生器所建立的部分類別中，通常用來提供變更通知。  部分方法讓開發人員得以自訂當變更發生時的回應行為。  
  
 程式碼產生器的設計工具只會定義方法簽章以及對方法的一個或多個呼叫。  然後，如果開發人員想要自訂所產生程式碼的行為，便可以提供該方法的實作 \(Implementation\)。  不提供實作時，編譯器 \(Compiler\) 會移除對方法的呼叫，而不會對效能造成額外的負荷。  
  
## 宣告  
 產生的程式碼會藉由在簽章行開頭加上 `Partial` 關鍵字，標記部分方法的定義。  
  
```vb#  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 定義必須符合下列條件：  
  
-   方法必須是 `Sub`，而不是 `Function`。  
  
-   方法的主體必須保持為空白。  
  
-   存取修飾詞必須是 `Private`。  
  
## 實作  
 實作工作主要是填入部分方法的主體。  這項實作通常是在定義之外的另一個部分類別中進行，並且是由想要擴充所產生程式碼的開發人員撰寫。  
  
```vb#  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 上述範例完整複製了宣告中的簽章，但還可以做許多變化。  具體而言，可以加入 `Overloads` 或 `Overrides` 等其他修飾詞 \(Modifier\)。  只允許有一個 `Overrides` 修飾詞。  如需方法修飾詞的詳細資訊，請參閱 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## 使用  
 呼叫部分方法時，就像是呼叫任何其他 `Sub` 程序一樣。  如果方法已實作，便會評估引數並且執行方法主體。  不過，請記住，實作部分方法的舉動是選擇性的。  如果方法沒有實作，則對該方法的呼叫會無效，而做為引數傳遞給方法的運算式也不會受到評估。  
  
## 範例  
 在名為 Product.Designer.vb 的檔案中，定義具有 `Quantity` 屬性 \(Property\) 的 `Product` 類別。  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 在名為 Product.vb 的檔案中，提供 `QuantityChanged` 的實作。  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 最後在專案的 Main 方法中，宣告 `Product` 執行個體 \(Instance\) 並指定其 `Quantity` 屬性的初始值。  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 此時應該會出現訊息方塊，並顯示下列訊息：  
  
 `Quantity was changed to 100`  
  
## 請參閱  
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [LINQ to SQL 的程式碼產生](../Topic/Code%20Generation%20in%20LINQ%20to%20SQL.md)   
 [使用部分方法加入商務邏輯](../Topic/Adding%20Business%20Logic%20By%20Using%20Partial%20Methods.md)