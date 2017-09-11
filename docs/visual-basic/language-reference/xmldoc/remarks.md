---
title: "&lt;註解&gt;(Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: c1b2c48dc3247935f703ff4107f29829c494a305
ms.contentlocale: zh-tw
ms.lasthandoff: 06/01/2017

---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="dff26-102">&lt;註解&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dff26-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="dff26-103">指定成員的 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="dff26-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff26-104">語法</span><span class="sxs-lookup"><span data-stu-id="dff26-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dff26-105">參數</span><span class="sxs-lookup"><span data-stu-id="dff26-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="dff26-106">成員的說明。</span><span class="sxs-lookup"><span data-stu-id="dff26-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dff26-107">備註</span><span class="sxs-lookup"><span data-stu-id="dff26-107">Remarks</span></span>  
 <span data-ttu-id="dff26-108">使用`<remarks>`標記來加入相關型別，以指定的資訊的補充資訊[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)。</span><span class="sxs-lookup"><span data-stu-id="dff26-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="dff26-109">這項資訊會出現在 物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="dff26-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="dff26-110">物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="dff26-110">For information about the Object Browser, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="dff26-111">使用編譯[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)程序至檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="dff26-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dff26-112">範例</span><span class="sxs-lookup"><span data-stu-id="dff26-112">Example</span></span>  
 <span data-ttu-id="dff26-113">這個範例會使用`<remarks>`標記來解釋什麼`UpdateRecord`方法會執行。</span><span class="sxs-lookup"><span data-stu-id="dff26-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 <span data-ttu-id="dff26-114">[!code-vb[VbVbcnXmlDocComments #&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="dff26-114">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff26-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dff26-115">See Also</span></span>  
 [<span data-ttu-id="dff26-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="dff26-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
