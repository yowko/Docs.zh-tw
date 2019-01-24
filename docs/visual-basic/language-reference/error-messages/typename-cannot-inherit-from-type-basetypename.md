---
title: '&#39;&lt;typename&gt; &#39;無法繼承自&lt;型別&gt; &#39;&lt;基&gt;&#39;因為它會展開基底存取&lt;類型&gt;外部組件'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 108025132bdd0fa86df5ed142aaa39c7b7e18062
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556479"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;typename&gt; &#39;無法繼承自&lt;型別&gt; &#39;&lt;基&gt;&#39;因為它會展開基底存取&lt;類型&gt;外部組件
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
