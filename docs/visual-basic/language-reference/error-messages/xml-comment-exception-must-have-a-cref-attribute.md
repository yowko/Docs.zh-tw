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
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="20e5f-102">XML 註解例外狀況必須有 'cref' 屬性</span><span class="sxs-lookup"><span data-stu-id="20e5f-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="20e5f-103">@No__t_0exception > 標記提供一種方式來記載方法可能擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="20e5f-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="20e5f-104">必要的 `cref` 屬性會指定檔產生器所檢查的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="20e5f-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="20e5f-105">如果成員存在，則會轉譯為檔檔中的標準專案名稱。</span><span class="sxs-lookup"><span data-stu-id="20e5f-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="20e5f-106">**錯誤識別碼：** BC42319</span><span class="sxs-lookup"><span data-stu-id="20e5f-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="20e5f-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="20e5f-107">To correct this error</span></span>

<span data-ttu-id="20e5f-108">將 `cref` 屬性新增至例外狀況，如下所示：</span><span class="sxs-lookup"><span data-stu-id="20e5f-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="20e5f-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="20e5f-109">See also</span></span>

- [<span data-ttu-id="20e5f-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="20e5f-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="20e5f-111">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="20e5f-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="20e5f-112">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="20e5f-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
