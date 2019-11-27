---
title: NotOverridable
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
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351450"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
指定無法在衍生類別中覆寫屬性或程式。  
  
## <a name="remarks"></a>備註  
 `NotOverridable` 修飾詞可防止在衍生類別中覆寫屬性或方法。  可覆[寫](../../../visual-basic/language-reference/modifiers/overridable.md)的修飾詞允許在衍生類別中覆寫類別中的屬性或方法。 如需詳細資訊，請參閱[繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果未指定 `Overridable` 或 `NotOverridable` 修飾詞，則預設值取決於屬性或方法是否會覆寫基類屬性或方法。 如果屬性或方法會覆寫基類屬性或方法，則預設設定為 `Overridable`。否則，它會 `NotOverridable`。  
  
 無法覆寫的專案有時稱為*密封*元素。  
  
 您只能在屬性或程式宣告語句中使用 `NotOverridable`。 您只能在覆寫另一個屬性或程式的屬性或程式上指定 `NotOverridable`，也就是只與 `Overrides`組合。  
  
## <a name="combined-modifiers"></a>合併的修飾詞  
 您不能為 `Private` 方法指定 `Overridable` 或 `NotOverridable`。  
  
 您不能在相同的宣告中同時指定 `NotOverridable` 與 `MustOverride`、`Overridable`或 `Shared`。  
  
## <a name="usage"></a>使用方式  
 `NotOverridable` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>請參閱

- [修飾詞](../../../visual-basic/language-reference/modifiers/index.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
