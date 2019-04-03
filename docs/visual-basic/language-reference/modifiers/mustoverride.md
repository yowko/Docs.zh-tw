---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822813"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
指定屬性或程序不這個類別中實作，而且必須覆寫衍生類別中才可以使用。  
  
## <a name="remarks"></a>備註  
 您只能在屬性或程序宣告陳述式中使用 `MustOverride`。 屬性或程序，指定`MustOverride`必須是類別的成員，且該類別必須標示[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。  
  
## <a name="rules"></a>規則  
  
-   **不完整的宣告。** 當您指定`MustOverride`，您未提供任何額外的數行程式碼的屬性或程序中，不甚至`End Function`， `End Property`，或`End Sub`陳述式。  
  
-   **結合的修飾詞。** 您無法指定`MustOverride`連同`NotOverridable`， `Overridable`，或`Shared`相同宣告中。  
  
-   **遮蔽和覆寫。** 遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱 < [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
-   **替代的字詞。** 不使用以外，覆寫中的項目有時稱為*純虛擬*項目。  
  
 `MustOverride` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
