---
title: XML 註解例外狀況必須有 'cref' 屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321166"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML 註解例外狀況必須有 'cref' 屬性

@No__t_0exception > 標記提供一種方式來記載方法可能擲回的例外狀況。 必要的 `cref` 屬性會指定檔產生器所檢查的成員名稱。 如果成員存在，則會轉譯為檔檔中的標準專案名稱。

**錯誤識別碼：** BC42319

## <a name="to-correct-this-error"></a>更正這個錯誤

將 `cref` 屬性新增至例外狀況，如下所示：

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>請參閱

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
