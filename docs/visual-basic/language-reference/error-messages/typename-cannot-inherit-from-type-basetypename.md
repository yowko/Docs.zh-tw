---
title: "'<typename>' 無法繼承自 <type> '<basetypename>'，因為它會在組件外展開基底 <type> 的存取"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838946"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<類型名稱 >' 無法繼承自\<類型 >'\<基 >' 因為它會展開基底存取\<類型 > 外部組件
類別或介面繼承自基底類別或介面，但具有較不嚴格的存取層級。  
  
 例如，`Public`介面繼承自`Friend`介面，或有`Protected`類別繼承自`Private`類別。 這會公開基底類別或介面，以存取超過預期的層級。  
  
 **錯誤 ID:** BC30910  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   變更衍生的類別或介面，以最少的基底類別或介面限制的存取層級。  
  
     -或-  
  
-   如果您需要較不嚴格的存取層級時，移除`Inherits`陳述式。 您無法繼承自更具限制性的基底類別或介面。  
  
## <a name="see-also"></a>另請參閱

- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
