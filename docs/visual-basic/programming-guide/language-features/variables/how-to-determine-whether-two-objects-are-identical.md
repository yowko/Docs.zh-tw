---
title: HOW TO：判斷兩個物件是否相同 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: aae053ae0473ed6ced0f28da3d5e5afc0be629df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769079"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>HOW TO：判斷兩個物件是否相同 (Visual Basic)
在 Visual Basic 中，兩個變數的參考會視為相同其指標都相同，也就是說，如果兩個變數都指向相同的類別執行個體，在記憶體中。 比方說，在 Windows Forms 應用程式中，您可能想要進行比較來決定是否目前的執行個體 (`Me`) 等同於特定的執行個體，例如`Form2`。  
  
 Visual Basic 提供兩個運算子比較指標。 [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)會傳回`True`如果物件相同，而[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)傳回`True`如果它們不是。  
  
## <a name="determining-if-two-objects-are-identical"></a>判斷兩個物件是否相同  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>若要判斷兩個物件是否相同  
  
1. 設定`Boolean`來測試兩個物件的運算式。  
  
2. 在您測試的運算式中，使用`Is`運算子與運算元為兩個物件。  
  
     `Is` 傳回`True`如果物件指向相同的類別執行個體。  
  
## <a name="determining-if-two-objects-are-not-identical"></a>判斷兩個物件是否不相同  
 您想要執行的動作，如果兩個物件並不相同，而且很難結合的有時`Not`並`Is`，例如`If Not obj1 Is obj2`。 在此情況下您可以使用`IsNot`運算子。  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>若要判斷兩個物件是否不相同  
  
1. 設定`Boolean`來測試兩個物件的運算式。  
  
2. 在您測試的運算式中，使用`IsNot`運算子與運算元為兩個物件。  
  
     `IsNot` 傳回`True`如果物件不會指向相同的類別執行個體。  
  
## <a name="example"></a>範例  
 下列範例會測試組`Object`變數上以查看是否它們指向相同的類別執行個體。  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 上述範例中會顯示下列輸出。  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>另請參閱

- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [如何：判斷兩個物件是否關聯](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
