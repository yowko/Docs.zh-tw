---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 70078752495240ab8c72fe1bbecdca554166fb22
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866427"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="bc922-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc922-101">\<remarks> (Visual Basic)</span></span>

<span data-ttu-id="bc922-102">指定成員的備註區段。</span><span class="sxs-lookup"><span data-stu-id="bc922-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc922-103">語法</span><span class="sxs-lookup"><span data-stu-id="bc922-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc922-104">參數</span><span class="sxs-lookup"><span data-stu-id="bc922-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="bc922-105">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="bc922-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc922-106">備註</span><span class="sxs-lookup"><span data-stu-id="bc922-106">Remarks</span></span>  

 <span data-ttu-id="bc922-107">您 `<remarks>` 可以使用標記來新增類型的相關資訊，以補充以指定的資訊 [\<summary>](summary.md) 。</span><span class="sxs-lookup"><span data-stu-id="bc922-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="bc922-108">這項資訊會出現在 [物件瀏覽器] 中。</span><span class="sxs-lookup"><span data-stu-id="bc922-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="bc922-109">如需物件瀏覽器的詳細資訊，請參閱 [查看程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="bc922-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="bc922-110">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="bc922-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc922-111">範例</span><span class="sxs-lookup"><span data-stu-id="bc922-111">Example</span></span>  

 <span data-ttu-id="bc922-112">此範例會使用 `<remarks>` 標記來說明方法的用途 `UpdateRecord` 。</span><span class="sxs-lookup"><span data-stu-id="bc922-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="bc922-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc922-113">See also</span></span>

- [<span data-ttu-id="bc922-114">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="bc922-114">XML Comment Tags</span></span>](index.md)
