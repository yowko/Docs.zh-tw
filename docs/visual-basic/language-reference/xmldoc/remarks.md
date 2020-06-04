---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400017"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="9c537-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c537-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="9c537-102">指定成員的備註區段。</span><span class="sxs-lookup"><span data-stu-id="9c537-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c537-103">語法</span><span class="sxs-lookup"><span data-stu-id="9c537-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c537-104">參數</span><span class="sxs-lookup"><span data-stu-id="9c537-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="9c537-105">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="9c537-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c537-106">備註</span><span class="sxs-lookup"><span data-stu-id="9c537-106">Remarks</span></span>  
 <span data-ttu-id="9c537-107">使用 `<remarks>` 標記來加入類型的相關資訊，並補充以指定的資訊 [\<summary>](summary.md) 。</span><span class="sxs-lookup"><span data-stu-id="9c537-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="9c537-108">這項資訊會出現在物件瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="9c537-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="9c537-109">如需物件瀏覽器的相關資訊，請參閱[查看程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="9c537-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="9c537-110">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="9c537-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c537-111">範例</span><span class="sxs-lookup"><span data-stu-id="9c537-111">Example</span></span>  
 <span data-ttu-id="9c537-112">這個範例會使用 `<remarks>` 標記來說明方法的用途 `UpdateRecord` 。</span><span class="sxs-lookup"><span data-stu-id="9c537-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="9c537-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c537-113">See also</span></span>

- [<span data-ttu-id="9c537-114">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="9c537-114">XML Comment Tags</span></span>](index.md)
