---
title: 部分方法 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 765a667f18340c53909c3ff1e9fcc5f2ffc0f9bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837464"
---
# <a name="partial-methods-visual-basic"></a>部分方法 (Visual Basic)
部分方法可讓開發人員程式碼中插入自訂邏輯。 一般而言，程式碼會是類別的一部分的設計工具所產生。 部分方法中所建立的程式碼產生器中，部分類別定義，它們通常用來提供的項目已變更的通知。 它們可讓開發人員指定自訂的行為變更的回應。  
  
 程式碼產生器的設計工具定義方法簽章和方法的一個或多個呼叫。 如果他們想要自訂產生的程式碼的行為，開發人員可以接著會提供方法的實作。 提供任何實作時，對方法的呼叫會移除的編譯器，產生任何額外的效能負擔。  
  
## <a name="declaration"></a>宣告  
 產生的程式碼會加上關鍵字標記的部分方法定義`Partial`簽名行開頭。  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 定義必須符合下列條件：  
  
-   這個方法必須是`Sub`，而非`Function`。  
  
-   方法的主體必須是空白。  
  
-   存取修飾詞必須是`Private`。  
  
## <a name="implementation"></a>實作  
 實作主要包含填入部分方法的主體。 實作通常是在不同的部分類別定義，並寫入由開發人員想要擴充產生的程式碼。  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 上述範例重複項目中宣告的簽章，但可能會有變化。 特別是，其他修飾詞，可以加入這類`Overloads`或`Overrides`。 只有一個`Overrides`允許修飾詞。 如需有關方法的修飾詞的詳細資訊，請參閱 < [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## <a name="use"></a>使用  
 您呼叫的部分方法時，就會呼叫任何其他`Sub`程序。 如果方法已實作，會評估引數，並執行方法的主體。 不過請記住，實作部分方法是選擇性的。 如果未實作方法，呼叫它沒有任何作用，並不會評估運算式做為引數傳遞至方法。  
  
## <a name="example"></a>範例  
 在檔案中名為 Product.Designer.vb，定義`Product`類別具有`Quantity`屬性。  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 在檔案中名為 Product.vb，提供實作`QuantityChanged`。  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 最後，在專案的 Main 方法中，宣告`Product`執行個體，並提供初始值其`Quantity`屬性。  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 應該會出現訊息方塊，會顯示下列訊息：  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>另請參閱

- [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Sub 程序](./sub-procedures.md)
- [選擇性參數](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [LINQ to SQL 中的程式碼產生](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [使用部分方法新增商務邏輯](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
