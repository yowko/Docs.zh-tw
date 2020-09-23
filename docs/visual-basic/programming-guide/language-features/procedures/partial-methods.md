---
title: 部分方法
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
ms.openlocfilehash: 0e7c1315df50e83c919270f76405e80862bdd03b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071257"
---
# <a name="partial-methods-visual-basic"></a>部分方法 (Visual Basic)

部分方法可讓開發人員在程式碼中插入自訂邏輯。 一般來說，程式碼是設計工具產生之類別的一部分。 部分方法會在程式碼產生器所建立的部分類別中定義，而且通常會用來提供已變更某個內容的通知。 它們可讓開發人員指定自訂行為以回應變更。  
  
 程式碼產生器的設計工具只會定義方法簽章，以及一或多個對方法的呼叫。 如果開發人員想要自訂所產生程式碼的行為，則可以提供方法的執行。 如果未提供任何執行，則編譯器會移除方法的呼叫，而不會產生額外的效能額外負荷。  
  
## <a name="declaration"></a>宣告  

 產生的程式碼會將關鍵字放在簽章行的開頭，藉以標記部分方法的定義 `Partial` 。  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 定義必須符合下列條件：  
  
- 方法必須是 `Sub` ，而不是 `Function` 。  
  
- 方法的主體必須保留空白。  
  
- 存取修飾詞必須是 `Private` 。  
  
## <a name="implementation"></a>實作  

 此實作為主要包含在部分方法的主體中。 其實作通常是在定義的個別部分類別中，而且是由想要擴充產生之程式碼的開發人員所撰寫。  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 先前的範例會完全複製宣告中的簽章，但可能會有變化。 尤其是可以加入其他修飾詞，例如 `Overloads` 或 `Overrides` 。 只 `Overrides` 允許一個修飾詞。 如需方法修飾詞的詳細資訊，請參閱 [Sub 語句](../../../language-reference/statements/sub-statement.md)。  
  
## <a name="use"></a>使用  

 您可以呼叫部分方法，就像呼叫任何其他程式一樣 `Sub` 。 如果已執行方法，則會評估引數，並執行方法的主體。 不過，請記住，執行部分方法是選擇性的。 如果未執行此方法，則對其進行的呼叫不會有任何作用，且不會評估做為引數傳遞至方法的運算式。  
  
## <a name="example"></a>範例  

 在名為 Product. .vb 的檔案中，定義 `Product` 具有屬性的類別 `Quantity` 。  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 在名為 Product 的檔案中，提供的實作為 `QuantityChanged` 。  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 最後，在專案的 Main 方法中，宣告實例， `Product` 並提供其屬性的初始值 `Quantity` 。  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 此時應該會出現訊息方塊，顯示此訊息：  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>另請參閱

- [Sub 陳述式](../../../language-reference/statements/sub-statement.md)
- [Sub 程序](./sub-procedures.md)
- [選擇性參數](./optional-parameters.md)
- [Partial](../../../language-reference/modifiers/partial.md)
- [LINQ to SQL 中的程式碼產生](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [使用部分方法加入商務邏輯](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
