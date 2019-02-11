---
title: <typeparamref> - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 834aff6e4673a306559daa1b9517e11538e90ad0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273344"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="5f503-102">\<typeparamref> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="5f503-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="5f503-103">語法</span><span class="sxs-lookup"><span data-stu-id="5f503-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f503-104">參數</span><span class="sxs-lookup"><span data-stu-id="5f503-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5f503-105">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f503-105">The name of the type parameter.</span></span> <span data-ttu-id="5f503-106">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="5f503-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f503-107">備註</span><span class="sxs-lookup"><span data-stu-id="5f503-107">Remarks</span></span>  
 <span data-ttu-id="5f503-108">如需泛型型別和方法中型別參數的詳細資訊，請參閱[泛型](../../../csharp/programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5f503-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="5f503-109">使用這個標記，讓文件檔案的取用者以某種明顯方式格式化單字，例如斜體。</span><span class="sxs-lookup"><span data-stu-id="5f503-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="5f503-110">使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="5f503-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f503-111">範例</span><span class="sxs-lookup"><span data-stu-id="5f503-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5f503-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f503-112">See also</span></span>

- [<span data-ttu-id="5f503-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5f503-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5f503-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="5f503-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
