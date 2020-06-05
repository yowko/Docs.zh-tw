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
ms.openlocfilehash: 463dd2454aafebf11554fb7bacdb73724c3130d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392154"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
指定無法在衍生類別中覆寫屬性或程式。  
  
## <a name="remarks"></a>備註  
 `NotOverridable`修飾詞可防止在衍生類別中覆寫屬性或方法。  可覆[寫](overridable.md)的修飾詞允許在衍生類別中覆寫類別中的屬性或方法。 如需詳細資訊，請參閱[繼承的基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果 `Overridable` `NotOverridable` 未指定或修飾詞，預設值會取決於屬性或方法是否會覆寫基類屬性或方法。 如果屬性或方法會覆寫基類屬性或方法，則預設設定為， `Overridable` 否則為 `NotOverridable` 。  
  
 無法覆寫的專案有時稱為*密封*元素。  
  
 您 `NotOverridable` 只能在屬性或程式宣告語句中使用。 您只能在 `NotOverridable` 覆寫另一個屬性或程式的屬性或程式上指定，也就是只搭配使用 `Overrides` 。  
  
## <a name="combined-modifiers"></a>合併的修飾詞  
 您不能 `Overridable` `NotOverridable` 為方法指定或 `Private` 。  
  
 您不能 `NotOverridable` `MustOverride` `Overridable` 在相同的宣告中，搭配、或來指定 `Shared` 。  
  
## <a name="usage"></a>使用方式  
 `NotOverridable` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../statements/function-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Sub 陳述式](../statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [修飾詞](index.md)
- [繼承基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [New](mustoverride.md)
- [Overrides](overridable.md)
- [覆寫](overrides.md)
- [關鍵字](../keywords/index.md)
- [Visual Basic 中的遮蔽功能](../../programming-guide/language-features/declared-elements/shadowing.md)
