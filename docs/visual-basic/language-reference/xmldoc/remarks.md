---
title: "&lt;註解&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f70c2d7df190d2ff8187882a9176dbe98984296
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="26dc4-102">&lt;註解&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26dc4-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="26dc4-103">指定成員的 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="26dc4-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26dc4-104">語法</span><span class="sxs-lookup"><span data-stu-id="26dc4-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26dc4-105">參數</span><span class="sxs-lookup"><span data-stu-id="26dc4-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="26dc4-106">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="26dc4-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26dc4-107">備註</span><span class="sxs-lookup"><span data-stu-id="26dc4-107">Remarks</span></span>  
 <span data-ttu-id="26dc4-108">使用`<remarks>`加入類型，補充指定的資訊的相關資訊的標記[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)。</span><span class="sxs-lookup"><span data-stu-id="26dc4-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="26dc4-109">這項資訊會出現在 物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="26dc4-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="26dc4-110">物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="26dc4-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="26dc4-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="26dc4-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26dc4-112">範例</span><span class="sxs-lookup"><span data-stu-id="26dc4-112">Example</span></span>  
 <span data-ttu-id="26dc4-113">這個範例會使用`<remarks>`標記加入至說明`UpdateRecord`方法會執行。</span><span class="sxs-lookup"><span data-stu-id="26dc4-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="26dc4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26dc4-114">See Also</span></span>  
 [<span data-ttu-id="26dc4-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="26dc4-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
