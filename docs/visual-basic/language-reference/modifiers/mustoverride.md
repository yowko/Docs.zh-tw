---
title: MustOverride
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
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351487"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
指定在這個類別中不會實作為屬性或程式，而且必須在衍生類別中加以覆寫，才可以使用它。  
  
## <a name="remarks"></a>備註  
 您只能在屬性或程式宣告語句中使用 `MustOverride`。 指定 `MustOverride` 的屬性或程式必須是類別的成員，且類別必須標記為 [ [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)]。  
  
## <a name="rules"></a>規則  
  
- **不完整的宣告。** 當您指定 `MustOverride`時，不會為屬性或程式提供任何額外的程式程式碼，甚至是 `End Function`、`End Property`或 `End Sub` 語句。  
  
- **合併的修飾詞。** 您不能在相同的宣告中同時指定 `MustOverride` 與 `NotOverridable`、`Overridable`或 `Shared`。  
  
- **遮蔽和覆寫。** 遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
- **替代詞彙。** 除非在覆寫中，否則無法使用的元素，有時稱為*純虛擬*元素。  
  
 `MustOverride` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
