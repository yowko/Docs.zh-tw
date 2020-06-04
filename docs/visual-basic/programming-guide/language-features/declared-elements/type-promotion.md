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
ms.openlocfilehash: 1e284b99a36cdf0f62aee2c45fd9f3bf544d1d81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410704"
---
# <a name="type-promotion-visual-basic"></a>類型提升 (Visual Basic)
當您在模組中宣告程式設計項目時，Visual Basic 會將其範圍升級為包含模組的命名空間。 這就是所謂的*型別提升*。  
  
 下列範例顯示模組的基本架構定義，以及該模組的兩個成員。  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 在中 `projModule` ，于模組層級宣告的程式設計項目會升級為 `projNamespace` 。 在上述範例中， `basicEnum` 和已 `innerClass` 升級，但不 `numberSub` 是，因為它不是在模組層級宣告。  
  
## <a name="effect-of-type-promotion"></a>型別提升的效果  
 升級類型的效果是限定性字串不需要包含模組名稱。 下列範例會對上述範例中的程式進行兩個呼叫。  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 在上述範例中，第一次呼叫會使用完整的合格字串。 不過，這不是必要的，因為升級類型。 第二個呼叫也會存取模組的成員，而不會 `projModule` 在限定性字串中包含。  
  
## <a name="defeat-of-type-promotion"></a>升級類型的破壞  
 如果命名空間已經具有與模組成員同名的成員，該模組成員的型別提升就會失效。 下列範例顯示在相同命名空間內列舉和模組的基本架構定義。  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 在上述範例中，Visual Basic 無法將類別升級 `abc` 為， `thisNameSpace` 因為命名空間層級已有相同名稱的列舉。 若要存取 `abcSub` ，您必須使用完整限定字串 `thisNamespace.thisModule.abc.abcSub` 。 不過， `xyz` 仍然會升級類別，而且您可以 `xyzSub` 使用較短的限定性字串來存取 `thisNamespace.xyz.xyzSub` 。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>部分類型的升級類型失效  
 如果模組內的類別或結構使用[部分](../../../language-reference/modifiers/partial.md)關鍵字，則該類別或結構的型別提升會自動失效，不論命名空間是否有相同名稱的成員。 模組中的其他元素仍然符合類型升級的資格。  
  
 **後果.** 部分定義升級類型的破壞可能會導致非預期的結果，甚至是編譯器錯誤。 下列範例顯示類別的基本架構部分定義，其中一個是在模組內。  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 在上述範例中，開發人員可能會預期編譯器合併的兩個部分定義 `sampleClass` 。 不過，編譯器不會考慮在內進行部分定義的升級 `sampleModule` 。 因此，它會嘗試編譯兩個不同且不同的類別，兩者都命名為， `sampleClass` 但具有不同的限定路徑。  
  
 只有在完整路徑相同時，編譯器才會合併部分定義。  
  
## <a name="recommendations"></a>建議  
 下列建議代表良好的程式設計作法。  
  
- **唯一名稱。** 當您對程式設計項目的命名有完整的控制權時，最好是在任何地方使用唯一的名稱。 相同名稱需要額外的限定，而且可能會讓您的程式碼更難閱讀。 它們也可能會導致微妙的錯誤和非預期的結果。  
  
- **完整限定。** 當您使用相同命名空間中的模組和其他元素時，最安全的方法是一律針對所有程式設計項目使用完整限定。 如果模組成員的型別提升已失效，而且您沒有完整限定該成員，您可能會不小心存取不同的程式設計專案。  
  
## <a name="see-also"></a>另請參閱

- [Module 陳述式](../../../language-reference/statements/module-statement.md)
- [Namespace 陳述式](../../../language-reference/statements/namespace-statement.md)
- [Partial](../../../language-reference/modifiers/partial.md)
- [Visual Basic 中的範圍](scope.md)
- [如何：控制變數的範圍](how-to-control-the-scope-of-a-variable.md)
- [References to Declared Elements](references-to-declared-elements.md)
