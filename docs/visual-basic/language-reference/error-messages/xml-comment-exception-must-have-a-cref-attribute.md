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
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="6c7aa-102">BC42319： XML 批註例外狀況必須有 ' cref ' 屬性</span><span class="sxs-lookup"><span data-stu-id="6c7aa-102">BC42319: XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="6c7aa-103">\<exception>標記提供一種方法來記錄方法可能擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6c7aa-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="6c7aa-104">必要的 `cref` 屬性會指定檔產生器所檢查之成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c7aa-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="6c7aa-105">如果成員存在，則會轉譯為檔檔中的標準專案名稱。</span><span class="sxs-lookup"><span data-stu-id="6c7aa-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="6c7aa-106">**錯誤識別碼：** BC42319</span><span class="sxs-lookup"><span data-stu-id="6c7aa-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6c7aa-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6c7aa-107">To correct this error</span></span>

<span data-ttu-id="6c7aa-108">將屬性新增至例外狀況，如下所示 `cref` ：</span><span class="sxs-lookup"><span data-stu-id="6c7aa-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="6c7aa-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c7aa-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="6c7aa-110">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="6c7aa-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="6c7aa-111">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="6c7aa-111">XML Comment Tags</span></span>](../xmldoc/index.md)
