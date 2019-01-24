---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: d2495e9d44a32e080d20deb4232ab27bfbd4051a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595807"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
指定的屬性或程序無法覆寫衍生類別中。  
  
## <a name="remarks"></a>備註  
 `NotOverridable`修飾詞可防止屬性或方法覆寫衍生類別中。  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)修飾詞允許在衍生類別中覆寫類別中的屬性或方法。 如需詳細資訊，請參閱[繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果`Overridable`或`NotOverridable`修飾詞未指定，預設值取決於是否屬性或方法會覆寫基底類別屬性或方法。 如果屬性或方法覆寫基底類別屬性或方法，預設值是`Overridable`; 否則它是`NotOverridable`。  
  
 無法覆寫的項目有時稱為*密封*項目。  
  
 您只能在屬性或程序宣告陳述式中使用 `NotOverridable`。 您可以指定`NotOverridable`只能在屬性或程序會覆寫另一個屬性或程序，也就是只有在搭配`Overrides`。  
  
## <a name="combined-modifiers"></a>結合的修飾詞  
 您無法指定`Overridable`或是`NotOverridable`如`Private`方法。  
  
 您無法指定`NotOverridable`連同`MustOverride`， `Overridable`，或`Shared`相同宣告中。  
  
## <a name="usage"></a>使用量  
 `NotOverridable` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱
- [修飾詞](../../../visual-basic/language-reference/modifiers/index.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
