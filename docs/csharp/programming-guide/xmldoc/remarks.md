---
title: "&lt;remarks&gt; (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- remarks
- <remarks>
dev_langs:
- CSharp
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cd11865fb0d4c8d21294107542fe39ad7e2b690a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="ltremarksgt-c-programming-guide"></a><span data-ttu-id="81d9f-102">&lt;remarks&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="81d9f-102">&lt;remarks&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="81d9f-103">語法</span><span class="sxs-lookup"><span data-stu-id="81d9f-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81d9f-104">參數</span><span class="sxs-lookup"><span data-stu-id="81d9f-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="81d9f-105">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="81d9f-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81d9f-106">備註</span><span class="sxs-lookup"><span data-stu-id="81d9f-106">Remarks</span></span>  
 <span data-ttu-id="81d9f-107">\<remarks> 標記是用來新增類型的資訊，以補充使用 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) 所指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="81d9f-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md).</span></span> <span data-ttu-id="81d9f-108">這項資訊會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="81d9f-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="81d9f-109">使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="81d9f-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81d9f-110">範例</span><span class="sxs-lookup"><span data-stu-id="81d9f-110">Example</span></span>  
 <span data-ttu-id="81d9f-111">[!code-cs[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="81d9f-111">[!code-cs[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d9f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81d9f-112">See Also</span></span>  
 <span data-ttu-id="81d9f-113">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="81d9f-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="81d9f-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="81d9f-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

