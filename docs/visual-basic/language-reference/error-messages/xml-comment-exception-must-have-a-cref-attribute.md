---
title: XML 註解例外狀況必須有&#39;cref&#39;屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: ee91513ef94e2abbe01d3ac09796b7fdf8e129ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>XML 註解例外狀況必須有&#39;cref&#39;屬性
\<例外狀況 > 標籤提供文件的方法可能會擲回的例外狀況的方法。 所需`cref`屬性可將指定的成員，會檢查文件產生器的名稱。 如果成員存在，則會將它轉譯成正式的項目名稱中的文件檔。  
  
 **錯誤 ID:** BC42319  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   新增`cref`屬性的例外狀況，如下所示：  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
