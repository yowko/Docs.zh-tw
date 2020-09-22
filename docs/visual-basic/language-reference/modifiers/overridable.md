---
title: Overrides
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
ms.openlocfilehash: 8506aba7e64f2dbd975cc275cefb7b5bb1aefda5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875005"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)

指定屬性或程式可由衍生類別中的相同命名屬性或程式覆寫。  
  
## <a name="remarks"></a>備註  

 `Overridable`修飾詞允許在衍生類別中覆寫類別中的屬性或方法。 [NotOverridable](notoverridable.md)修飾詞可防止屬性或方法在衍生類別中遭到覆寫。  如需詳細資訊，請參閱[繼承的基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果 `Overridable` `NotOverridable` 未指定或修飾詞，預設值會取決於屬性或方法是否會覆寫基類屬性或方法。 如果屬性或方法會覆寫基類屬性或方法，則預設設定為， `Overridable` 否則為 `NotOverridable` 。  
  
 您可以使用陰影或覆寫來重新定義繼承的元素，但是這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱 [Visual Basic 中的遮蔽](../../programming-guide/language-features/declared-elements/shadowing.md)。  
  
 可以覆寫的元素有時稱為 *虛擬* 元素。 如果可以覆寫，但不一定要這樣做，有時也稱為 *實體* 元素。  
  
 您 `Overridable` 只能在屬性或程式聲明語句中使用。  
  
## <a name="combined-modifiers"></a>合併的修飾詞  

 您無法 `Overridable` `NotOverridable` 為方法指定或 `Private` 。  
  
 您無法 `Overridable` 在相同的宣告中同時指定和 `MustOverride` 、 `NotOverridable` 或 `Shared` 。  
  
 因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。  
  
## <a name="usage"></a>使用方式  

 `Overridable` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../statements/function-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Sub 陳述式](../statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [修飾詞](index.md)
- [繼承基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [New](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [覆寫](overrides.md)
- [關鍵字](../keywords/index.md)
- [Visual Basic 中的遮蔽功能](../../programming-guide/language-features/declared-elements/shadowing.md)
