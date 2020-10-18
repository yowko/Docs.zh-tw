---
title: "'<typename>' 無法繼承自 <type> '<basetypename>'，因為它會在組件外展開基底 <type> 的存取"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 5c019f9d74b11e48aa05a1480b9449fa28488b43
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161838"
---
# <a name="bc30910-typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>BC30910： ' \<typename> ' 無法繼承自 \<type> ' '， \<basetypename> 因為它會展開元件外部的基底存取 \<type>

類別或介面繼承自基底類別或介面，但存取層級較不嚴格。

 例如， `Public` 介面繼承自 `Friend` 介面，或類別繼承自類別 `Protected` `Private` 。 這會公開基底類別或介面，以存取超出預期的層級。

 **錯誤識別碼：** BC30910

## <a name="to-correct-this-error"></a>更正這個錯誤

- 將衍生類別或介面的存取層級變更為至少與基類或介面的限制相同。

     -或-

- 如果您需要較不嚴格的存取層級，請移除該 `Inherits` 語句。 您無法繼承更受限制的基類或介面。

## <a name="see-also"></a>另請參閱

- [Class 陳述式](../statements/class-statement.md)
- [Interface 陳述式](../statements/interface-statement.md)
- [Inherits Statement](../statements/inherits-statement.md)
- [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)
