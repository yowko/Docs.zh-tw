---
title: New
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
ms.openlocfilehash: 1b20108a2d42e82c0af7598fde8d60a08fea28ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396190"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
指定在這個類別中不會實作為屬性或程式，而且必須在衍生類別中加以覆寫，才可以使用它。  
  
## <a name="remarks"></a>備註  
 您 `MustOverride` 只能在屬性或程式宣告語句中使用。 指定的屬性或程式 `MustOverride` 必須是類別的成員，而且類別必須標記為[MustInherit](mustinherit.md)。  
  
## <a name="rules"></a>規則  
  
- **不完整的宣告。** 當您指定時，不會 `MustOverride` 為屬性或程式提供任何額外的程式程式碼，甚至不會提供 `End Function` 、 `End Property` 或 `End Sub` 語句。  
  
- **結合的修飾詞。** 您不能 `MustOverride` `NotOverridable` `Overridable` 在相同的宣告中，搭配、或來指定 `Shared` 。  
  
- **遮蔽和覆寫。** 遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的陰影](../../programming-guide/language-features/declared-elements/shadowing.md)。  
  
- **替代詞彙。** 除非在覆寫中，否則無法使用的元素，有時稱為*純虛擬*元素。  
  
 `MustOverride` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../statements/function-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Sub 陳述式](../statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [NotOverridable](notoverridable.md)
- [Overrides](overridable.md)
- [覆寫](overrides.md)
- [MustInherit](mustinherit.md)
- [關鍵字](../keywords/index.md)
- [Visual Basic 中的遮蔽功能](../../programming-guide/language-features/declared-elements/shadowing.md)
