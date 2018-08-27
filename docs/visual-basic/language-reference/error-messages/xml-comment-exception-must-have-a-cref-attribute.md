---
title: XML 註解例外狀況必須有&#39;cref&#39;屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: abe9fe0f6216f81fa223fe83a122b580577e1c32
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930024"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="bada0-102">XML 註解例外狀況必須有&#39;cref&#39;屬性</span><span class="sxs-lookup"><span data-stu-id="bada0-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="bada0-103">\<例外狀況 > 標籤可用來記載方法可能擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bada0-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="bada0-104">必要`cref`屬性可將指定的成員，會檢查文件產生器的名稱。</span><span class="sxs-lookup"><span data-stu-id="bada0-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="bada0-105">如果成員存在，則會將它轉譯成在文件檔案中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="bada0-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="bada0-106">**錯誤 ID:** BC42319</span><span class="sxs-lookup"><span data-stu-id="bada0-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bada0-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bada0-107">To correct this error</span></span>  
  
-   <span data-ttu-id="bada0-108">新增`cref`屬性之例外狀況，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bada0-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bada0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bada0-109">See Also</span></span>  
 [<span data-ttu-id="bada0-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="bada0-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="bada0-111">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="bada0-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="bada0-112">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="bada0-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
