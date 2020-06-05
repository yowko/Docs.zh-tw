---
title: "'<membername>' 無法透過 <typename> '<containertype>' 在專案外部公開類型 '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 729a9f385d94412469d318cb804d216827eeb0fd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397281"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<membername>' 無法透過 \<typename> '\<containertype>' 在專案外部公開類型 '\<containertypename>'
變數、程式參數或函式傳回會在其容器外公開，但它會宣告為不能在容器外公開的類型。  
  
 下列基本架構程式碼會顯示產生此錯誤的情況。  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 宣告為、、或的類型， `Protected` `Friend` `Protected Friend` `Private` 目的是要在其宣告內容之外擁有有限的存取權。 以較不受限制的存取來使用它做為變數的資料類型，將會破壞此目的。 在上述的基本架構程式碼中， `exposedVar` 是， `Public` 而且會公開 `privateClass` 給不應存取它的程式碼。  
  
 **錯誤識別碼：** BC30909  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將變數、程式參數或函數傳回的存取層級變更為至少與其資料類型的存取層級相同。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)
