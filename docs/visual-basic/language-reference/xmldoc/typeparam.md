---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 014623be84f9d7eb8a25ac4aadcce450f158c154
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827233"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="5fcbf-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fcbf-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="5fcbf-103">定義的型別參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="5fcbf-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fcbf-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fcbf-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fcbf-105">參數</span><span class="sxs-lookup"><span data-stu-id="5fcbf-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5fcbf-106">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5fcbf-106">The name of the type parameter.</span></span> <span data-ttu-id="5fcbf-107">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="5fcbf-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="5fcbf-108">型別參數的描述。</span><span class="sxs-lookup"><span data-stu-id="5fcbf-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fcbf-109">備註</span><span class="sxs-lookup"><span data-stu-id="5fcbf-109">Remarks</span></span>  
 <span data-ttu-id="5fcbf-110">使用`<typeparam>`泛型類型或泛型成員宣告來描述的其中一個類型參數的註解中的標記。</span><span class="sxs-lookup"><span data-stu-id="5fcbf-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="5fcbf-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="5fcbf-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fcbf-112">範例</span><span class="sxs-lookup"><span data-stu-id="5fcbf-112">Example</span></span>  
 <span data-ttu-id="5fcbf-113">這個範例會使用`<typeparam>`標記來描述`id`參數。</span><span class="sxs-lookup"><span data-stu-id="5fcbf-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="5fcbf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fcbf-114">See also</span></span>

- [<span data-ttu-id="5fcbf-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="5fcbf-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
