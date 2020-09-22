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
ms.openlocfilehash: 8eec54a12c7fb748df46e8c48a8b07eab983cc72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867861"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)

指定無法在衍生類別中覆寫屬性或程式。  
  
## <a name="remarks"></a>備註  

 `NotOverridable`修飾詞可防止屬性或方法在衍生類別中遭到覆寫。  可 [覆寫的修飾詞](overridable.md) 允許在衍生類別中覆寫類別中的屬性或方法。 如需詳細資訊，請參閱[繼承的基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果 `Overridable` `NotOverridable` 未指定或修飾詞，預設值會取決於屬性或方法是否會覆寫基類屬性或方法。 如果屬性或方法會覆寫基類屬性或方法，則預設設定為， `Overridable` 否則為 `NotOverridable` 。  
  
 無法覆寫的元素有時也稱為 *密封* 元素。  
  
 您 `NotOverridable` 只能在屬性或程式聲明語句中使用。 您只能在 `NotOverridable` 覆寫另一個屬性或程式的屬性或程式上指定，也就是只與一起使用 `Overrides` 。  
  
## <a name="combined-modifiers"></a>合併的修飾詞  

 您無法 `Overridable` `NotOverridable` 為方法指定或 `Private` 。  
  
 您無法 `NotOverridable` 在相同的宣告中同時指定和 `MustOverride` 、 `Overridable` 或 `Shared` 。  
  
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
