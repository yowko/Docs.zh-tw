---
title: 如何：判斷兩個物件是否相同
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348603"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>如何：判斷兩個物件是否相同 (Visual Basic)
在 Visual Basic 中，如果兩個變數的指標相同，則會將其視為相同，也就是說，如果這兩個變數都指向記憶體中的相同類別實例。 例如，在 Windows Forms 應用程式中，您可能會想要進行比較，以判斷目前的實例（`Me`）是否與特定實例相同，例如 `Form2`。  
  
 Visual Basic 提供兩個運算子來比較指標。 如果物件相同，則[Is 運算子會](../../../../visual-basic/language-reference/operators/is-operator.md)傳回 `True`，而[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)會傳回 `True` （如果不是）。  
  
## <a name="determining-if-two-objects-are-identical"></a>判斷兩個物件是否相同  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>判斷兩個物件是否相同  
  
1. 設定 `Boolean` 運算式來測試兩個物件。  
  
2. 在測試運算式中，使用 `Is` 運算子搭配兩個物件做為運算元。  
  
     如果物件指向相同的類別實例，`Is` 會傳回 `True`。  
  
## <a name="determining-if-two-objects-are-not-identical"></a>判斷兩個物件是否不相同  
 有時候您會想要在兩個物件不相同時執行動作，而且結合 `Not` 和 `Is`（例如 `If Not obj1 Is obj2`）可能會很難。 在這種情況下，您可以使用 `IsNot` 運算子。  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>判斷兩個物件是否不相同  
  
1. 設定 `Boolean` 運算式來測試兩個物件。  
  
2. 在測試運算式中，使用 `IsNot` 運算子搭配兩個物件做為運算元。  
  
     如果物件未指向相同的類別實例，`IsNot` 會傳回 `True`。  
  
## <a name="example"></a>範例  
 下列範例會測試 `Object` 變數的配對，以查看它們是否指向相同的類別實例。  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 上述範例會顯示下列輸出。  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>請參閱

- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [如何：判斷兩個物件是否關聯](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
