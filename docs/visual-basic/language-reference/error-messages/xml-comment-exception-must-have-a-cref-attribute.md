---
title: XML 註解例外狀況必須有 'cref' 屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406504"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML 註解例外狀況必須有 'cref' 屬性

\<exception>標記提供一種方式來記載方法可能擲回的例外狀況。 Required `cref` 屬性會指定檔產生器所檢查的成員名稱。 如果成員存在，則會轉譯為檔檔中的標準專案名稱。

**錯誤識別碼：** BC42319

## <a name="to-correct-this-error"></a>更正這個錯誤

將 `cref` 屬性新增至例外狀況，如下所示：

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>另請參閱

- [\<exception>](../xmldoc/exception.md)
- [如何：建立 XML 文件](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML 註解標籤](../xmldoc/index.md)
