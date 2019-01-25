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
ms.openlocfilehash: b4a9acb5a43898ef616bbc6bb97f2f4f96d206b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496945"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
代表任何資料類型的預設值。 若是參考類型，預設值是`null`參考。 實值型別，預設值取決於實值型別是否可為 null。  
  
> [!NOTE]
>  不可為 null 的實值型別，如`Nothing`在 Visual Basic 中與不同`null`在C#。 在 Visual Basic 中，如果您的變數設定為不可為 null 的實值型別`Nothing`，此變數會設為其宣告類型的預設值。 在C#，如果您指派至不可為 null 的實值型別的變數`null`，就會發生編譯時期錯誤。  
  
## <a name="remarks"></a>備註  
 `Nothing` 表示資料類型的預設值。 預設值取決於變數是否是參考類型或實值類型。  
  
 變數*實值型別*直接包含其值。 實值型別包含的所有數值資料類型， `Boolean`， `Char`， `Date`，所有的結構和所有列舉型別。 變數*參考的型別*在記憶體中儲存物件的執行個體的參考。 參考型別包括類別、 陣列、 委派和字串。 如需詳細資訊，請參閱 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
 如果變數是實值類型，行為`Nothing`取決於是否可為 null 的資料類型的變數。 若要表示可為 null 的實值型別，新增`?`修飾詞加入型別名稱。 指派`Nothing`可為 null 的變數的值設定為`null`。 如需詳細資訊和範例，請參閱 <<c0> [ 可為 Null 的實值型別](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)。  
  
 如果變數屬於實值型別不是可為 null，指派`Nothing`要它將它設定為預設值為其宣告的型別。 如果該類型包含變數的成員，它們會都設為其預設值。 下列範例會說明這點的純量類型。  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 如果變數屬於參考類型，將指派`Nothing`變數將它設定為`null`參考變數的類型。 此變數會設為`null`參考不是任何物件相關聯。 下列範例為其示範。  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 檢查變數是否參照 （或可為 null 的實值類型） 時`null`，請勿使用`= Nothing`或`<> Nothing`。 一律使用`Is Nothing`或`IsNot Nothing`。  
  
 在 Visual Basic 中的字串，則為空字串就等於`Nothing`。 因此，`"" = Nothing`為 true。  
  
 下列範例示範使用的比較`Is`和`IsNot`運算子。  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 如果您宣告變數時不用`As`子句並將它設定為`Nothing`，該變數具有一種`Object`。 這個範例是`Dim something = Nothing`。 在此情況下發生編譯時期錯誤時`Option Strict`位於和`Option Infer`已關閉。  
  
 當您將指派`Nothing`給物件變數，它不再是指任何物件執行個體。 如果之前已將該變數參考執行個體，將它設定為`Nothing`並不會終止執行個體本身。 終止執行個體，並與它相關聯的記憶體和系統資源的發行，記憶體回收行程 (GC) 偵測到沒有剩餘的作用中參考時，才。  
  
 `Nothing` 不同於<xref:System.DBNull>物件，表示未初始化的變數或不存在的資料庫資料行。  
  
## <a name="see-also"></a>另請參閱
- [Dim 陳述式](../../visual-basic/language-reference/statements/dim-statement.md)
- [物件存留期：如何建立和終結物件](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [在 Visual Basic 中的存留期](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is 運算子](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 運算子](../../visual-basic/language-reference/operators/isnot-operator.md)
- [可為 Null 的值類型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
