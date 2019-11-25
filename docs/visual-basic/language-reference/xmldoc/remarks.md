---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: b327e548bcdce1522a888855bd88e3150695147b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352253"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="8a612-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a612-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="8a612-102">Specifies a remarks section for the member.</span><span class="sxs-lookup"><span data-stu-id="8a612-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a612-103">語法</span><span class="sxs-lookup"><span data-stu-id="8a612-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a612-104">參數</span><span class="sxs-lookup"><span data-stu-id="8a612-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="8a612-105">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="8a612-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a612-106">備註</span><span class="sxs-lookup"><span data-stu-id="8a612-106">Remarks</span></span>  
 <span data-ttu-id="8a612-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="8a612-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="8a612-108">This information appears in the Object Browser.</span><span class="sxs-lookup"><span data-stu-id="8a612-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="8a612-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="8a612-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="8a612-110">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="8a612-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a612-111">範例</span><span class="sxs-lookup"><span data-stu-id="8a612-111">Example</span></span>  
 <span data-ttu-id="8a612-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span><span class="sxs-lookup"><span data-stu-id="8a612-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="8a612-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a612-113">See also</span></span>

- [<span data-ttu-id="8a612-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="8a612-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
