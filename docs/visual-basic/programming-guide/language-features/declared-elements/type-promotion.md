---
title: 類型提升
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
ms.openlocfilehash: 6c28ca22e96616ff09e147400bfdb2adb922ff0e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085798"
---
# <a name="type-promotion-visual-basic"></a>類型提升 (Visual Basic)

當您在模組中宣告程式設計專案時，Visual Basic 會將其範圍升級為包含模組的命名空間。 這就是所謂的 *型別提升*。  
  
 下列範例顯示模組的基本架構定義，以及該模組的兩個成員。  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 在中 `projModule` ，在模組層級宣告的程式設計專案會升級為 `projNamespace` 。 在上述範例中， `basicEnum` 和 `innerClass` 會升級，但不是 `numberSub` ，因為它不是在模組層級宣告。  
  
## <a name="effect-of-type-promotion"></a>型別提升的效果  

 型別提升的影響是，限定性字串不需要包含模組名稱。 下列範例會對上述範例中的程式進行兩次呼叫。  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 在上述範例中，第一個呼叫會使用完整的限定字串。 不過，這並不是必要的，因為升級型別。 第二個呼叫也會存取模組的成員，而不包含 `projModule` 在限定性字串中。  
  
## <a name="defeat-of-type-promotion"></a>型別提升的擊敗  

 如果命名空間已經有與模組成員同名的成員，則該模組成員的型別提升會失效。 下列範例顯示列舉的基本架構定義和相同命名空間中的模組。  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 在上述範例中，Visual Basic 無法將類別升級 `abc` 為， `thisNameSpace` 因為在命名空間層級已經有相同名稱的列舉。 若要存取 `abcSub` ，您必須使用完整的限定性字串 `thisNamespace.thisModule.abc.abcSub` 。 不過，類別 `xyz` 仍會升級，而且您可以 `xyzSub` 使用較短的限定性字串來存取 `thisNamespace.xyz.xyzSub` 。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>部分類型的型別提升的擊敗  

 如果模組內的類別或結構使用 [Partial](../../../language-reference/modifiers/partial.md) 關鍵字，則不論命名空間是否有相同名稱的成員，類別或結構的型別提升都會自動失效。 模組中的其他元素仍然符合類型升級的資格。  
  
 **後果。** 部分定義的型別提升的破壞可能會導致非預期的結果，甚至是編譯器錯誤。 下列範例顯示類別的基本架構部分定義，其中之一是在模組中。  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 在上述範例中，開發人員可能會預期編譯器會合並的兩個部分定義 `sampleClass` 。 不過，編譯器並不會考慮升級內部的部分定義 `sampleModule` 。 如此一來，它會嘗試編譯兩個不同的不同類別，這兩個類別都命名為 `sampleClass` 但使用不同的限定路徑。  
  
 只有在完整路徑相同時，編譯器才會合併部分定義。  
  
## <a name="recommendations"></a>建議  

 下列建議代表良好的程式設計作法。  
  
- **唯一的名稱。** 當您完全掌控程式設計項目的命名時，在任何地方都可以使用唯一的名稱。 相同的名稱需要額外的限定性，而且可能會讓您的程式碼更難閱讀。 它們也可能導致微妙的錯誤和非預期的結果。  
  
- **完整限定。** 當您使用相同命名空間中的模組和其他專案時，最安全的方法是一律針對所有程式設計專案使用完整限定。 如果模組成員的型別提升無法通過，而且您未完全符合該成員，您可能會不慎存取不同的程式設計項目。  
  
## <a name="see-also"></a>另請參閱

- [Module 陳述式](../../../language-reference/statements/module-statement.md)
- [Namespace 陳述式](../../../language-reference/statements/namespace-statement.md)
- [Partial](../../../language-reference/modifiers/partial.md)
- [Visual Basic 中的範圍](scope.md)
- [如何：控制變數的範圍](how-to-control-the-scope-of-a-variable.md)
- [References to Declared Elements](references-to-declared-elements.md)
