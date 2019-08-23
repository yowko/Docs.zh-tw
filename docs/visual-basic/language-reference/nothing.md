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
ms.openlocfilehash: 12c88db49dc7723fc269195e7d174bfa822c64d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963752"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
表示任何資料類型的預設值。 對於參考型別, 預設值為`null`參考。 對於實數值型別, 預設值取決於實數值型別是否可為 null。  
  
> [!NOTE]
> 針對不可為 null 的實值`Nothing`類型, 在中`null` , C#Visual Basic 與中的不同。 在 Visual Basic 中, 如果您將不可為 null 的實數值型別變數設`Nothing`為, 則變數會設定為其宣告類型的預設值。 在C#中, 如果您將不可為 null 的實數值型別的變數`null`指派給, 就會發生編譯時期錯誤。  
  
## <a name="remarks"></a>備註  
 `Nothing`表示資料類型的預設值。 預設值取決於變數是實數值型別或參考型別。  
  
 實*值型*別的變數直接包含它的值。 實數值型別包括所有數值資料類型`Boolean`、 `Char`、 `Date`、、所有結構和所有列舉。 *參考型別*的變數會將物件實例的參考儲存在記憶體中。 參考型別包括類別、陣列、委派和字串。 如需詳細資訊，請參閱 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
 如果變數是實值型別, 則的行為`Nothing`取決於變數是否為可為 null 的資料型別。 若要表示可為 null 的實值`?`型別, 請將修飾詞加入至型別名稱。 指派`Nothing`給可為 null 的變數會將`null`值設定為。 如需詳細資訊和範例, 請參閱[可為 null 的實數值型別](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)。  
  
 如果變數是不可為 null 的實數值型別, 則指派`Nothing`給它會將它設定為其宣告類型的預設值。 如果該類型包含變數成員, 則會將它們全部設定為預設值。 下列範例會針對純量類型說明這種情況。  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 如果變數是參考型別, 則指派`Nothing`給變數會將它設定`null`為變數類型的參考。 設定為`null`參考的變數不會與任何物件相關聯。 下列範例為其示範。  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 檢查參考 (或可為 null 的實數值型別) 變數`null`是否為時, `= Nothing`請`<> Nothing`不要使用或。 請一律`Is Nothing`使用`IsNot Nothing`或。  
  
 對於 Visual Basic 中的字串, 空字串等於`Nothing`。 因此, `"" = Nothing`為 true。  
  
 下列範例顯示使用`Is`和`IsNot`運算子的比較。  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 如果您在不使用`As`子句的情況下宣告變數, 並將它設定為`Nothing`, 則`Object`變數的類型為。 其中一個範例是`Dim something = Nothing`。 當是 on 且為 off 時`Option Strict` , `Option Infer`就會發生編譯時期錯誤。  
  
 當您指派`Nothing`給物件變數時, 它不會再參考任何物件實例。 如果變數先前已參考實例, 將其設定為`Nothing`不會終止實例本身。 實例會終止, 而且只有在垃圾收集行程 (GC) 偵測到沒有任何使用中的參考之後, 才會釋放與它相關聯的記憶體和系統資源。  
  
 `Nothing`不同于<xref:System.DBNull>物件, 代表未初始化的 variant 或不存在的資料庫資料行。  
  
## <a name="see-also"></a>另請參閱

- [Dim 陳述式](../../visual-basic/language-reference/statements/dim-statement.md)
- [物件存留期:物件的建立和終結方式](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic 中的存留期](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is 運算子](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 運算子](../../visual-basic/language-reference/operators/isnot-operator.md)
- [可為 Null 的值類型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
