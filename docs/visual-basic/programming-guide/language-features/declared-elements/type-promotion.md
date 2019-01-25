---
title: 類型提升 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: 4761a3ebc3e1271846c2415d8f629500a515ed2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721925"
---
# <a name="type-promotion-visual-basic"></a>類型提升 (Visual Basic)
當您宣告的模組中的程式設計項目時，Visual Basic 升級其範圍包含模組的命名空間。 這就所謂*類型提升*。  
  
 下列範例會顯示模組的基本架構定義，該模組的兩個成員。  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 內`projModule`程式設計，在模組層級宣告的項目會提升至`projNamespace`。 在上述範例中，`basicEnum`並`innerClass`會升級，但`numberSub`不是，因為它未宣告為在模組層級。  
  
## <a name="effect-of-type-promotion"></a>類型提升的效果  
 類型提升的效果是限定性條件字串不需要包含模組名稱。 下列範例會使在上述範例中的程序的兩個呼叫。  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 在上述範例中，第一次呼叫會使用完整限定性條件字串。 不過，這是不需要因為型別提升。 第二個呼叫也存取模組的成員不含`projModule`限定性條件字串中。  
  
## <a name="defeat-of-type-promotion"></a>型別提升失敗  
 如果命名空間已經有具有相同名稱做為模組成員的成員，型別提升是讓該模組成員。 下列範例顯示基本架構定義的列舉型別與相同的命名空間內的模組。  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 在上述範例中，Visual Basic 無法將類別升階`abc`至`thisNameSpace`因為已有同名的命名空間層級的列舉。 若要存取`abcSub`，您必須使用完整限定性條件字串`thisNamespace.thisModule.abc.abcSub`。 不過，類別`xyz`仍會升級，而且您可以存取`xyzSub`使用較短的限定性條件字串`thisNamespace.xyz.xyzSub`。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>部分類型的型別提升失敗  
 如果類別或模組內的結構會使用[部分](../../../../visual-basic/language-reference/modifiers/partial.md)關鍵字、 型別提升會自動失效該類別或結構中，命名空間是否具有相同名稱的成員。 在模組中的其他項目是仍可進行型別提升。  
  
 **結果。** 非預期的結果，甚至是編譯器錯誤，可能會造成的部分定義的型別提升失敗。 下列範例示範基本架構的類別，其中之一就是在模組內的部分定義。  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 在上述範例中，開發人員可能會預期要合併兩個部分定義的編譯器`sampleClass`。 不過，編譯器不會考慮的部分定義內的升級`sampleModule`。 如此一來，它會嘗試將編譯兩個個別且不同的類別，名為`sampleClass`但具有不同的限定性條件路徑。  
  
 只有在完整路徑相同時，編譯器才會合併部分定義。  
  
## <a name="recommendations"></a>建議  
 下列建議代表良好的程式設計作法。  
  
-   **唯一的名稱。** 當您擁有完整控制權的程式設計項目命名時，一律是個不錯的主意，到處都使用唯一的名稱。 相同的名稱需要額外的限定性條件，而且可以讓您的程式碼更難讀取。 它們也可能會導致難以察覺的錯誤和非預期的結果。  
  
-   **完整的限定性條件。** 當您使用的模組和相同的命名空間中的其他項目時，最安全的方法就是一律使用完整限定性條件，針對所有的程式設計項目。 如果型別提升將無效的模組成員，而且您未完整限定該成員，您可能不小心存取不同的程式設計項目。  
  
## <a name="see-also"></a>另請參閱
- [Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Namespace 陳述式](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [如何：控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
