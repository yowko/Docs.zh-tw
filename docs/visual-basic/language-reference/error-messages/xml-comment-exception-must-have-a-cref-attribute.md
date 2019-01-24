---
title: XML 註解例外狀況必須有&#39;cref&#39;屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 0f276781165e80b2d869da2518dbe34b33085d5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649943"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="522cf-102">XML 註解例外狀況必須有&#39;cref&#39;屬性</span><span class="sxs-lookup"><span data-stu-id="522cf-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="522cf-103">\<例外狀況 > 標籤可用來記載方法可能擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="522cf-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="522cf-104">必要`cref`屬性可將指定的成員，會檢查文件產生器的名稱。</span><span class="sxs-lookup"><span data-stu-id="522cf-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="522cf-105">如果成員存在，則會將它轉譯成在文件檔案中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="522cf-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="522cf-106">**錯誤 ID:** BC42319</span><span class="sxs-lookup"><span data-stu-id="522cf-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="522cf-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="522cf-107">To correct this error</span></span>  
  
-   <span data-ttu-id="522cf-108">新增`cref`屬性之例外狀況，如下所示：</span><span class="sxs-lookup"><span data-stu-id="522cf-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="522cf-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="522cf-109">See also</span></span>
- [<span data-ttu-id="522cf-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="522cf-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="522cf-111">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="522cf-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="522cf-112">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="522cf-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
