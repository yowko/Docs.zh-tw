---
title: <typeparamref> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 3e96d55d7cf60b2a9085cf065ef3b8193b173c5d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711671"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="22dc3-102">\<typeparamref> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="22dc3-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="22dc3-103">語法</span><span class="sxs-lookup"><span data-stu-id="22dc3-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="22dc3-104">參數</span><span class="sxs-lookup"><span data-stu-id="22dc3-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="22dc3-105">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="22dc3-105">The name of the type parameter.</span></span> <span data-ttu-id="22dc3-106">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="22dc3-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22dc3-107">備註</span><span class="sxs-lookup"><span data-stu-id="22dc3-107">Remarks</span></span>  
 <span data-ttu-id="22dc3-108">如需泛型型別和方法中型別參數的詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="22dc3-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="22dc3-109">使用這個標記，讓文件檔案的取用者以某種明顯方式格式化單字，例如斜體。</span><span class="sxs-lookup"><span data-stu-id="22dc3-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="22dc3-110">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="22dc3-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22dc3-111">範例</span><span class="sxs-lookup"><span data-stu-id="22dc3-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="22dc3-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="22dc3-112">See also</span></span>

- [<span data-ttu-id="22dc3-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="22dc3-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="22dc3-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="22dc3-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
