---
title: <remarks> - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 3e6625c55a6f5c29fb55bff2eb87959f3237652e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975845"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="39ec8-102">\<remarks> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="39ec8-102">\<remarks> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="39ec8-103">語法</span><span class="sxs-lookup"><span data-stu-id="39ec8-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39ec8-104">參數</span><span class="sxs-lookup"><span data-stu-id="39ec8-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="39ec8-105">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="39ec8-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39ec8-106">備註</span><span class="sxs-lookup"><span data-stu-id="39ec8-106">Remarks</span></span>  
 <span data-ttu-id="39ec8-107">\<remarks> 標記是用來新增類型的資訊，以補充使用 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) 所指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="39ec8-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md).</span></span> <span data-ttu-id="39ec8-108">這項資訊會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="39ec8-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="39ec8-109">使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="39ec8-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39ec8-110">範例</span><span class="sxs-lookup"><span data-stu-id="39ec8-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="39ec8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39ec8-111">See also</span></span>

- [<span data-ttu-id="39ec8-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="39ec8-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="39ec8-113">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="39ec8-113">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
