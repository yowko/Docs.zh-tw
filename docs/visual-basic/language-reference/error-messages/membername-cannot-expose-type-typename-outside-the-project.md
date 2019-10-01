---
title: "'<membername>' 無法透過 <typename> '<containertype>' 在專案外部公開類型 '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: ca67e74d7790352bd1842cb8a59fe1525af6e18c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700893"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>' @no__t 0membername > ' 無法透過 \<containertype > ' \<containertypename > '，在專案外公開類型 ' \<typename > '
變數、程式參數或函式傳回會在其容器外公開，但它會宣告為不能在容器外公開的類型。  
  
 下列基本架構程式碼會顯示產生此錯誤的情況。  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 @No__t-0、`Friend`、`Protected Friend` 或 `Private` 宣告的類型，主要是在其宣告內容外具有有限的存取權。 以較不受限制的存取來使用它做為變數的資料類型，將會破壞此目的。 在上述的基本架構程式碼中，`exposedVar` 會 `Public`，並將 `privateClass` 公開給不應該有存取權的程式碼。  
  
 **錯誤識別碼：** BC30909  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將變數、程式參數或函數傳回的存取層級變更為至少與其資料類型的存取層級相同。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
