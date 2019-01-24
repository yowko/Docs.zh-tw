---
title: '&#39;&lt;membername&gt; &#39;無法公開 （expose) 的型別&#39; &lt;typename&gt; &#39;透過在專案外&lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 39d316aca5ec306de4b1e43e2eb2d1495f5525d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672340"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;&lt;membername&gt; &#39;無法公開 （expose) 的型別&#39; &lt;typename&gt; &#39;透過在專案外&lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;
變數、 程序參數或函式傳回外部公開其容器，但它卻宣告為不會公開對容器外部的型別。  
  
 下列的基本架構程式碼顯示會產生此錯誤的情況。  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 宣告的型別`Protected`， `Friend`， `Protected Friend`，或`Private`旨在有限存取，其宣告的內容之外。 使用做為資料類型的限制較少存取的變數會破壞此目的。 在上述的基本架構程式碼中，`exposedVar`是`Public`，並會公開`privateClass`不應該存取它的程式碼。  
  
 **錯誤 ID:** BC30909  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   變更存取層級的變數、 程序參數或函式會傳回至少為其資料類型的存取層級限制。  
  
## <a name="see-also"></a>另請參閱
- [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
