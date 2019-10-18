---
title: 受保護的 Friend （Visual Basic）
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524782"
---
# <a name="protected-friend-visual-basic"></a>受保護的 Friend （Visual Basic）

`Protected Friend` 關鍵字組合是成員存取修飾詞。 它會在宣告的元素上授[Friend](friend.md)存取和[受保護](protected.md)的存取，因此可以從相同元件中的任何位置、從其本身的類別，以及從衍生類別存取。 您只能在類別的成員上指定 `Protected Friend`;您無法將 `Protected Friend` 套用到結構的成員，因為無法繼承結構。

> [!NOTE]
> 在 Visual Studio 中，選取 [F1 說明] [`protected friend`] 可提供[受保護](protected.md)或[friend](friend.md)的協助。 IDE 會挑選游標下的單一 token，而不是複合字組。

## <a name="rules"></a>規則

**宣告內容。** 您只能在類別層級使用 `Protected Friend`。 這表示 `Protected` 元素的宣告內容必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。

## <a name="see-also"></a>請參閱

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
