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
ms.openlocfilehash: b290315cd9c36281c110bbf0c6246468a1a899b2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259159"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="cd843-102">\<remarks> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="cd843-102">\<remarks> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="cd843-103">語法</span><span class="sxs-lookup"><span data-stu-id="cd843-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd843-104">參數</span><span class="sxs-lookup"><span data-stu-id="cd843-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="cd843-105">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="cd843-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd843-106">備註</span><span class="sxs-lookup"><span data-stu-id="cd843-106">Remarks</span></span>  
 <span data-ttu-id="cd843-107">\<remarks> 標記是用來新增類型的資訊，以補充使用 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) 所指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="cd843-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md).</span></span> <span data-ttu-id="cd843-108">這項資訊會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="cd843-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="cd843-109">使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="cd843-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd843-110">範例</span><span class="sxs-lookup"><span data-stu-id="cd843-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cd843-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd843-111">See also</span></span>

- [<span data-ttu-id="cd843-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cd843-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cd843-113">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="cd843-113">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
