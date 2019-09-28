---
title: XML 註解例外狀況必須有 'cref' 屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592032"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML 註解例外狀況必須有 'cref' 屬性
@No__t 0exception > 標記會提供一種方式，記載方法所擲回的例外狀況。 必要的 `cref` 屬性會指定檔產生器所檢查的成員名稱。 如果成員存在，則會轉譯為檔檔中的標準專案名稱。  
  
 **錯誤識別碼：** BC42319  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將 `cref` 屬性新增至例外狀況，如下所示：  
  
    Xml  
    ' ' '<exception cref="member">描述</exception>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
