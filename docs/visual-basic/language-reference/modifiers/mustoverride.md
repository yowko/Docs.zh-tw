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
ms.openlocfilehash: cf73f07b6e13d524281129e3c5d8dceceb90764c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867939"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)

指定屬性或程式不會在此類別中執行，而且必須在衍生類別中覆寫，才能加以使用。  
  
## <a name="remarks"></a>備註  

 您 `MustOverride` 只能在屬性或程式聲明語句中使用。 指定的屬性或程式 `MustOverride` 必須是類別的成員，而且類別必須標記為 [MustInherit](mustinherit.md)。  
  
## <a name="rules"></a>規則  
  
- **不完整的宣告。** 當您指定時，不會 `MustOverride` 為屬性或程式提供任何額外的程式程式碼，甚至是 `End Function` 、 `End Property` 或 `End Sub` 語句。  
  
- **結合的修飾詞。** 您無法 `MustOverride` 在相同的宣告中同時指定和 `NotOverridable` 、 `Overridable` 或 `Shared` 。  
  
- **遮蔽和覆寫。** 遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱 [Visual Basic 中的遮蔽](../../programming-guide/language-features/declared-elements/shadowing.md)。  
  
- **替代條款。** 除了在覆寫之外，無法使用的元素有時也稱為 *純虛擬* 元素。  
  
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
