---
title: XML 註解例外狀況必須有 'cref' 屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 18e7aa5f6905eaa9c509aa21fe6f5bfcd54d46f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163294"
---
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a>BC42319： XML 批註例外狀況必須有 ' cref ' 屬性

\<exception>標記提供一種方法來記錄方法可能擲回的例外狀況。 必要的 `cref` 屬性會指定檔產生器所檢查之成員的名稱。 如果成員存在，則會轉譯為檔檔中的標準專案名稱。

**錯誤識別碼：** BC42319

## <a name="to-correct-this-error"></a>更正這個錯誤

將屬性新增至例外狀況，如下所示 `cref` ：

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>另請參閱

- [\<exception>](../xmldoc/exception.md)
- [如何：建立 XML 文件](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML 註解標籤](../xmldoc/index.md)
