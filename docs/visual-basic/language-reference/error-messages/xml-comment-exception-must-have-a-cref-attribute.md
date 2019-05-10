---
title: XML 註解例外狀況必須有 'cref' 屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 91bde92e2184c90b14838a09a89a6d261447f139
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662616"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML 註解例外狀況必須有 'cref' 屬性
\<例外狀況 > 標籤可用來記載方法可能擲回的例外狀況。 必要`cref`屬性可將指定的成員，會檢查文件產生器的名稱。 如果成員存在，則會將它轉譯成在文件檔案中的標準項目名稱。  
  
 **錯誤 ID:** BC42319  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 新增`cref`屬性之例外狀況，如下所示：  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>另請參閱

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
