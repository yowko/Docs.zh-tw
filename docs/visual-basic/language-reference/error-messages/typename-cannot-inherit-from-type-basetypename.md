---
title: '&#39;&lt;typename&gt;&#39; 無法繼承自&lt;類型&gt;&#39;&lt;產生&gt;&#39;，因為它會展開基底存取&lt;類型&gt;外部組件'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d01981d3136968ae2534539b8eccab4c5c535fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;typename&gt;&#39; 無法繼承自&lt;類型&gt;&#39;&lt;產生&gt;&#39;，因為它會展開基底存取&lt;類型&gt;外部組件
類別或介面繼承自基底類別或介面，但具有較不嚴格的存取層級。  
  
 例如，`Public`介面繼承自`Friend`介面，或`Protected`類別繼承自`Private`類別。 這樣會公開基底類別或介面，以存取超過預期的層級。  
  
 **錯誤 ID:** BC30910  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   變更衍生的類別或介面若要在至少相同嚴格度的基底類別或介面的存取層級。  
  
     -或-  
  
-   如果您需要較不嚴格的存取層級，移除`Inherits`陳述式。 您無法繼承自更具限制性的基底類別或介面。  
  
## <a name="see-also"></a>另請參閱  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
