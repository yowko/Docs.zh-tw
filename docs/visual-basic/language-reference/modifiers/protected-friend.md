---
title: Protected 的 Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306537"
---
# <a name="protected-friend-visual-basic"></a>Protected 的 Friend (Visual Basic)

`Protected Friend`關鍵字的組合都是成員的存取修飾詞。 它會同時授與[Friend](friend.md)存取和[保護](protected.md)上宣告的項目，這樣就可從相同組件，從其自己的類別和衍生類別中的任何位置存取的存取。 您可以指定`Protected Friend`只成員上的類別; 無法套用`Protected Friend`結構的成員因為結構無法被繼承。

> [!NOTE]
> 在 Visual Studio 中，選取 F1 說明上`protected friend`提供任何說明[保護](protected.md)或[friend](friend.md)。 IDE 會挑選單一語彙基元，在資料指標，而不是複合字。

## <a name="rules"></a>規則

- **宣告內容。** 您可以使用`Protected Friend`只能在類別層級。 這表示宣告內容`Protected`項目必須是類別，且不能原始程式檔、 命名空間、 介面、 模組、 結構或程序。 


## <a name="see-also"></a>另請參閱

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[受保護的私用](./private-protected.md)   
[在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
