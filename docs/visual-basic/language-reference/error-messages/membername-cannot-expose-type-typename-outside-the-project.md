---
title: "'<membername>' 無法透過 <typename> '<containertype>' 在專案外部公開類型 '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 03767501488a395073f925e27adea439751c0de6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265060"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<成員名稱 >' 無法公開類型'\<類型名稱 >' 透過在專案外\<containertype > '\<containertypename >'
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
