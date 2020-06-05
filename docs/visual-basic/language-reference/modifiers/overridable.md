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
ms.openlocfilehash: dcbabde8464dd8a0ce5fad24d7d72b1e780270d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392115"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
指定屬性或程式可由衍生類別中名稱相同的屬性或程式覆寫。  
  
## <a name="remarks"></a>備註  
 `Overridable`修飾詞允許在衍生類別中覆寫類別中的屬性或方法。 [NotOverridable](notoverridable.md)修飾詞可防止在衍生類別中覆寫屬性或方法。  如需詳細資訊，請參閱[繼承的基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果 `Overridable` `NotOverridable` 未指定或修飾詞，預設值會取決於屬性或方法是否會覆寫基類屬性或方法。 如果屬性或方法會覆寫基類屬性或方法，則預設設定為， `Overridable` 否則為 `NotOverridable` 。  
  
 您可以遮蔽或覆寫以重新定義繼承的元素，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的陰影](../../programming-guide/language-features/declared-elements/shadowing.md)。  
  
 可以覆寫的專案有時稱為*虛擬*元素。 如果可以覆寫它，但不一定要這麼做，有時也稱為*具體*元素。  
  
 您 `Overridable` 只能在屬性或程式宣告語句中使用。  
  
## <a name="combined-modifiers"></a>合併的修飾詞  
 您不能 `Overridable` `NotOverridable` 為方法指定或 `Private` 。  
  
 您不能 `Overridable` `MustOverride` `NotOverridable` 在相同的宣告中，搭配、或來指定 `Shared` 。  
  
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
