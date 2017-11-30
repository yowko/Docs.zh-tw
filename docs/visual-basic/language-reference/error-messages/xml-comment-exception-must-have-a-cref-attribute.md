---
title: "XML 註解例外狀況必須有 &#39; cref &#39;屬性"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords: BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="e45f3-102">XML 註解例外狀況必須有 &#39; cref &#39;屬性</span><span class="sxs-lookup"><span data-stu-id="e45f3-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="e45f3-103">\<例外狀況 > 標籤提供文件的方法可能會擲回的例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="e45f3-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="e45f3-104">所需`cref`屬性可將指定的成員，會檢查文件產生器的名稱。</span><span class="sxs-lookup"><span data-stu-id="e45f3-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="e45f3-105">如果成員存在，則會將它轉譯成正式的項目名稱中的文件檔。</span><span class="sxs-lookup"><span data-stu-id="e45f3-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="e45f3-106">**錯誤 ID:** BC42319</span><span class="sxs-lookup"><span data-stu-id="e45f3-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e45f3-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e45f3-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e45f3-108">新增`cref`屬性的例外狀況，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e45f3-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e45f3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e45f3-109">See Also</span></span>  
 [<span data-ttu-id="e45f3-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="e45f3-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="e45f3-111">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="e45f3-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="e45f3-112">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="e45f3-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
