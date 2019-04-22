---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c5c088472ae09a416953d9c0829cad1cb48646b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833486"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="78a6e-102">\<備註 > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78a6e-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="78a6e-103">指定成員的 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="78a6e-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="78a6e-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="78a6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="78a6e-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="78a6e-106">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="78a6e-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78a6e-107">備註</span><span class="sxs-lookup"><span data-stu-id="78a6e-107">Remarks</span></span>  
 <span data-ttu-id="78a6e-108">使用`<remarks>`類型，補充使用指定的資訊的相關資訊，將標記[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)。</span><span class="sxs-lookup"><span data-stu-id="78a6e-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="78a6e-109">這項資訊會出現在 物件瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="78a6e-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="78a6e-110">物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="78a6e-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="78a6e-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="78a6e-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78a6e-112">範例</span><span class="sxs-lookup"><span data-stu-id="78a6e-112">Example</span></span>  
 <span data-ttu-id="78a6e-113">這個範例會使用`<remarks>`標記來解釋什麼`UpdateRecord`方法會執行。</span><span class="sxs-lookup"><span data-stu-id="78a6e-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="78a6e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78a6e-114">See also</span></span>

- [<span data-ttu-id="78a6e-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="78a6e-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
