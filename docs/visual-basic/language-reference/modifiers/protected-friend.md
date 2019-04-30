---
title: 受保護的 Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 331c63dc290d4096e8158f265ee869b47743a273
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053882"
---
# <a name="protected-friend-visual-basic"></a>受保護的 Friend (Visual Basic)

`Protected Friend` 關鍵字組合是成員存取修飾詞。 它會授與這兩[Friend](friend.md)存取並[受保護](protected.md)上宣告的項目，使其可從相同的組件，從他們自己的類別，以及從衍生類別中的任何位置存取的存取。 您可以指定`Protected Friend`只能在類別; 的成員上不能套用`Protected Friend`的結構成員因為結構無法被繼承。

> [!NOTE]
> 在 Visual Studio 中，選取 上的 F1 說明`protected friend`提供的其中一個 說明[保護](protected.md)或是[friend](friend.md)。 IDE 會挑選單一語彙基元，在資料指標，而不是複合字。

## <a name="rules"></a>規則

- **宣告內容。** 您可以使用`Protected Friend`只能在類別層級。 這表示的宣告內容`Protected`項目必須是類別，，而且不能是原始程式檔、 命名空間、 介面、 模組、 結構或程序。 

## <a name="see-also"></a>另請參閱

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
