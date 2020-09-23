---
title: 如何：判斷兩個物件是否相同
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 1bbc8083fcfb6f5ff0f4328c32b83a2e7218ecd6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072271"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>如何：判斷兩個物件是否相同 (Visual Basic)

在 Visual Basic 中，如果兩個變數參考都相同，則會將兩個變數參考視為相同，也就是兩個變數都指向記憶體中的相同類別實例。 例如，在 Windows Forms 應用程式中，您可能會想要進行比較，以判斷目前的實例 (`Me`) 是否與特定的實例相同，例如 `Form2` 。  
  
 Visual Basic 提供兩個運算子來比較指標。 如果物件相同，則 [運算子會](../../../language-reference/operators/is-operator.md) 傳回 `True` ，而且如果不是，則會傳回 [IsNot 運算子](../../../language-reference/operators/isnot-operator.md) `True` 。  
  
## <a name="determining-if-two-objects-are-identical"></a>判斷兩個物件是否相同  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>判斷兩個物件是否相同  
  
1. 設定 `Boolean` 運算式以測試這兩個物件。  
  
2. 在您的測試運算式中，使用 `Is` 具有兩個物件的運算子做為運算元。  
  
     `Is``True`如果物件指向相同的類別實例，則傳回。  
  
## <a name="determining-if-two-objects-are-not-identical"></a>判斷兩個物件是否不相同  

 有時候您會想要在兩個物件不相同的情況下執行動作，而結合和也可能很難 `Not` `Is` `If Not obj1 Is obj2` 。 在這種情況下，您可以使用 `IsNot` 運算子。  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>判斷兩個物件是否相同  
  
1. 設定 `Boolean` 運算式以測試這兩個物件。  
  
2. 在您的測試運算式中，使用 `IsNot` 具有兩個物件的運算子做為運算元。  
  
     `IsNot``True`如果物件沒有指向相同的類別實例，則傳回。  
  
## <a name="example"></a>範例  

 下列範例會測試變數的配對 `Object` ，以查看它們是否指向相同的類別實例。  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 上述範例會顯示下列輸出。  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>另請參閱

- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [物件變數](object-variables.md)
- [物件變數值](object-variable-values.md)
- [Is 運算子](../../../language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../language-reference/operators/isnot-operator.md)
- [如何：判斷兩個物件是否關聯](how-to-determine-whether-two-objects-are-related.md)
- [Me、My、MyBase 及 MyClass](../../program-structure/me-my-mybase-and-myclass.md)
