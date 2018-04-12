---
title: '&#39;&lt;membername&gt;&#39; 無法公開類型 &#39;&lt;typename&gt;&#39; 透過在專案外&lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;&lt;membername&gt;&#39; 無法公開類型 &#39;&lt;typename&gt;&#39; 透過在專案外&lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;
變數、 程序參數或函式傳回其容器，外部公開，但它卻宣告為不會公開容器外的型別。  
  
 下列的基本架構程式碼將示範會產生此錯誤的情況。  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 宣告的型別`Protected`， `Friend`， `Protected Friend`，或`Private`要擁有受限存取其宣告的內容之外。 使用的資料類型的限制較少存取的變數會破壞此用途。 在上述的基本架構程式碼，`exposedVar`是`Public`和會公開`privateClass`不應該有其存取權的程式碼。  
  
 **錯誤 ID:** BC30909  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   變更變數、 程序參數或函式的存取層級會傳回至少嚴格愈好其資料類型的存取層級。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
