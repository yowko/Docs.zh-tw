---
title: "'<typename>' 無法繼承自 <type> '<basetypename>'，因為它會在組件外展開基底 <type> 的存取"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: aa04c558abbcc4259c2821cdcbdc1669b91ffee0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402768"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename>' 無法繼承自 \<type> '\<basetypename>'，因為它會在組件外展開基底 \<type> 的存取
類別或介面繼承自基類或介面，但具有較不嚴格的存取層級。  
  
 例如， `Public` 介面繼承自 `Friend` 介面，或 `Protected` 類別繼承自 `Private` 類別。 這會公開基類或介面，以存取超出預期的層級。  
  
 **錯誤識別碼：** BC30910  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將衍生類別或介面的存取層級變更為至少和基類或介面的限制。  
  
     -或-  
  
- 如果您需要較不嚴格的存取層級，請移除 `Inherits` 語句。 您無法從更受限制的基類或介面繼承。  
  
## <a name="see-also"></a>另請參閱

- [Class 陳述式](../statements/class-statement.md)
- [Interface 陳述式](../statements/interface-statement.md)
- [Inherits Statement](../statements/inherits-statement.md)
- [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)
