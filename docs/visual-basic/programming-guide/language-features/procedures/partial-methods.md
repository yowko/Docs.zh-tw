---
title: "部分方法 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33e34c63988e74be2c22cb7b1358f5e8b04048c6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="partial-methods-visual-basic"></a>部分方法 (Visual Basic)
部分方法可讓開發人員程式碼中插入自訂邏輯。 通常，程式碼是類別的設計工具產生的一部分。 部分方法中所建立的程式碼產生器中，部分類別定義，它們通常用來提供到的項目已變更的通知。 它們可讓開發人員指定自訂的行為變更的回應。  
  
 程式碼產生器的設計工具定義方法簽章和一或多個方法的呼叫。 如果他們想要自訂產生程式碼的行為，開發人員隨後即可提供方法的實作。 提供沒有實作時，編譯器，導致沒有產生額外效能負荷會移除對方法的呼叫。  
  
## <a name="declaration"></a>宣告  
 產生的程式碼將放入關鍵字標記的部分方法定義`Partial`簽章一行的開頭。  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 定義必須符合下列條件：  
  
-   方法必須為`Sub`，而非`Function`。  
  
-   方法的主體必須是空白。  
  
-   存取修飾詞必須`Private`。  
  
## <a name="implementation"></a>實作  
 實作包含主要填滿的部分方法主體中。 通常是在不同的部分類別定義中，從與想要將產生的程式碼擴充的開發人員撰寫的實作。  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 上述範例重複項目中宣告的簽章，但可能會有變化。 特別是，其他修飾詞可增加，例如`Overloads`或`Overrides`。 只有一個`Overrides`允許修飾詞。 如需有關方法的修飾詞的詳細資訊，請參閱[Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## <a name="use"></a>使用  
 您呼叫的部分方法時，就會呼叫任何其他`Sub`程序。 如果已實作的方法，評估引數，並執行之方法主體。 不過請記住，實作部分方法是選擇性的。 如果未實作方法，它的呼叫沒有任何作用，並不會評估運算式做為引數傳遞給方法。  
  
## <a name="example"></a>範例  
 在檔案中名為 Product.Designer.vb，定義`Product`類別具有`Quantity`屬性。  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 在檔案中名為 Product.vb，提供實作`QuantityChanged`。  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 最後，在專案的 Main 方法中，宣告`Product`執行個體並提供的初始值其`Quantity`屬性。  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 應該會出現訊息方塊會顯示此訊息：  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>請參閱  
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Sub 程序](./sub-procedures.md)  
 [選擇性參數](./optional-parameters.md)  
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [LINQ to SQL 中的程式碼產生](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [使用部分方法新增商務邏輯](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
