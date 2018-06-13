---
title: '&lt;註解&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 6e4e280760b9238fdc403ac5fe586743334e4c69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598181"
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="95a0a-102">&lt;註解&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95a0a-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="95a0a-103">指定成員的 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="95a0a-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="95a0a-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95a0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="95a0a-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="95a0a-106">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="95a0a-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95a0a-107">備註</span><span class="sxs-lookup"><span data-stu-id="95a0a-107">Remarks</span></span>  
 <span data-ttu-id="95a0a-108">使用`<remarks>`加入類型，補充指定的資訊的相關資訊的標記[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)。</span><span class="sxs-lookup"><span data-stu-id="95a0a-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="95a0a-109">這項資訊會出現在 物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="95a0a-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="95a0a-110">物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="95a0a-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="95a0a-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="95a0a-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95a0a-112">範例</span><span class="sxs-lookup"><span data-stu-id="95a0a-112">Example</span></span>  
 <span data-ttu-id="95a0a-113">這個範例會使用`<remarks>`標記加入至說明`UpdateRecord`方法會執行。</span><span class="sxs-lookup"><span data-stu-id="95a0a-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="95a0a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95a0a-114">See Also</span></span>  
 [<span data-ttu-id="95a0a-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="95a0a-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
