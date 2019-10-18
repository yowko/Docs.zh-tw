---
title: <remarks> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 38549b2fcce0740b2b9cfd42d950e56b343e7a30
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524672"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="d1c91-102">\<remarks > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d1c91-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="d1c91-103">指定成員的備註區段。</span><span class="sxs-lookup"><span data-stu-id="d1c91-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c91-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1c91-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1c91-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1c91-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="d1c91-106">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="d1c91-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1c91-107">備註</span><span class="sxs-lookup"><span data-stu-id="d1c91-107">Remarks</span></span>  
 <span data-ttu-id="d1c91-108">使用 `<remarks>` 標記來新增類型的相關資訊，並補充[\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md)所指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="d1c91-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="d1c91-109">這項資訊會出現在物件瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="d1c91-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="d1c91-110">如需物件瀏覽器的相關資訊，請參閱[查看程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="d1c91-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="d1c91-111">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="d1c91-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1c91-112">範例</span><span class="sxs-lookup"><span data-stu-id="d1c91-112">Example</span></span>  
 <span data-ttu-id="d1c91-113">這個範例會使用 `<remarks>` 標記來說明 `UpdateRecord` 方法的用途。</span><span class="sxs-lookup"><span data-stu-id="d1c91-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="d1c91-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c91-114">See also</span></span>

- [<span data-ttu-id="d1c91-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="d1c91-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
