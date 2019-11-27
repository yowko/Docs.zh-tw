---
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351393"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
指定屬性或程式可由衍生類別中名稱相同的屬性或程式覆寫。  
  
## <a name="remarks"></a>備註  
 `Overridable` 修飾詞允許在衍生類別中覆寫類別中的屬性或方法。 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)修飾詞可防止在衍生類別中覆寫屬性或方法。  如需詳細資訊，請參閱[繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果未指定 `Overridable` 或 `NotOverridable` 修飾詞，則預設值取決於屬性或方法是否會覆寫基類屬性或方法。 如果屬性或方法會覆寫基類屬性或方法，則預設設定為 `Overridable`。否則，它會 `NotOverridable`。  
  
 您可以遮蔽或覆寫以重新定義繼承的元素，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
 可以覆寫的專案有時稱為*虛擬*元素。 如果可以覆寫它，但不一定要這麼做，有時也稱為*具體*元素。  
  
 您只能在屬性或程式宣告語句中使用 `Overridable`。  
  
## <a name="combined-modifiers"></a>合併的修飾詞  
 您不能為 `Private` 方法指定 `Overridable` 或 `NotOverridable`。  
  
 您不能在相同的宣告中同時指定 `Overridable` 與 `MustOverride`、`NotOverridable`或 `Shared`。  
  
 因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。  
  
## <a name="usage"></a>使用方式  
 `Overridable` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [修飾詞](../../../visual-basic/language-reference/modifiers/index.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
