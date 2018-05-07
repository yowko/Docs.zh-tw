---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: fb1af7d748faac78b26177af453a0e858f9e97c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
代表任何資料類型的預設值。 預設值是參考類型`null`參考。 對於實值類型的預設值取決於是否可為 null 的實值型別。  
  
> [!NOTE]
>  不可為 null 的實值型別，`Nothing`在 Visual Basic 中不同於`null`C# 中。 在 Visual Basic，如果您設定的非 null 值型別變數`Nothing`，此變數會設為其宣告類型的預設值。 在 C# 中，如果您指派的變數不可為 null 的實值型別`null`，就會發生編譯時期錯誤。  
  
## <a name="remarks"></a>備註  
 `Nothing` 代表資料類型的預設值。 預設值取決於變數是否是實值類型或參考型別。  
  
 變數的*實值型別*直接包含其值。 實值型別包含所有的數值資料類型， `Boolean`， `Char`， `Date`，所有的結構，以及所有列舉型別。 變數的*參考型別*儲存在記憶體中物件的執行個體的參考。 參考類型包括類別、 陣列、 委派和字串。 如需詳細資訊，請參閱 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
 如果變數是實值類型，行為`Nothing`取決於是否可為 null 的資料類型的變數。 若要表示 null 的實值類型，新增`?`修飾詞加入型別名稱。 指派`Nothing`可為 null 的變數的值設定為`null`。 如需詳細資訊和範例，請參閱[可為 Null 的實值型別](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)。  
  
 如果變數屬於實值型別不是可為 null，指派`Nothing`到它將它設定為預設值為其宣告的型別。 如果該類型包含可變成員，它們是全部設定為其預設值。 下列範例將說明這點的純量類型。  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 如果變數屬於參考型別，指派`Nothing`變數將其設為`null`參考變數的類型。 此變數會設為`null`參考不是任何物件相關聯。 下列範例為其示範。  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 當檢查是否參考 （或 null 的實值類型） 變數`null`，請勿使用`= Nothing`或`<> Nothing`。 一律使用`Is Nothing`或`IsNot Nothing`。  
  
 在 Visual Basic 中的字串，則為空字串等於`Nothing`。 因此，`"" = Nothing`為 true。  
  
 下列範例顯示使用的比較`Is`和`IsNot`運算子。  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 如果您宣告變數，而不使用`As`子句並將它設定為`Nothing`，變數會有一種`Object`。 舉例來說，這是`Dim something = Nothing`。 編譯時間錯誤，就會發生這種情況下時`Option Strict`上和`Option Infer`已關閉。  
  
 當您指派`Nothing`物件變數，即不再參考任何物件執行個體。 如果執行個體，之前已參考變數，將它設定為`Nothing`並不會終止執行個體本身。 終止執行個體，並與它相關聯的記憶體和系統資源之後才, 釋放記憶體回收行程 (GC) 偵測到沒有剩餘的作用中參考。  
  
 `Nothing` 不同於<xref:System.DBNull>物件，代表未初始化的變數或不存在的資料庫資料行。  
  
## <a name="see-also"></a>另請參閱  
 [Dim 陳述式](../../visual-basic/language-reference/statements/dim-statement.md)  
 [物件存留期：物件的建立和終結](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [在 Visual Basic 中的存留期](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Is 運算子](../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot 運算子](../../visual-basic/language-reference/operators/isnot-operator.md)  
 [可為 Null 的值類型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
