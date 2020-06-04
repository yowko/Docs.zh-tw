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
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="f8bf8-102">XML 註解例外狀況必須有 'cref' 屬性</span><span class="sxs-lookup"><span data-stu-id="f8bf8-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="f8bf8-103">\<exception>標記提供一種方式來記載方法可能擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f8bf8-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="f8bf8-104">Required `cref` 屬性會指定檔產生器所檢查的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="f8bf8-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="f8bf8-105">如果成員存在，則會轉譯為檔檔中的標準專案名稱。</span><span class="sxs-lookup"><span data-stu-id="f8bf8-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="f8bf8-106">**錯誤識別碼：** BC42319</span><span class="sxs-lookup"><span data-stu-id="f8bf8-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f8bf8-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f8bf8-107">To correct this error</span></span>

<span data-ttu-id="f8bf8-108">將 `cref` 屬性新增至例外狀況，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f8bf8-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="f8bf8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8bf8-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="f8bf8-110">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="f8bf8-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="f8bf8-111">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="f8bf8-111">XML Comment Tags</span></span>](../xmldoc/index.md)
