---
title: '&lt;typeparamref&gt; (C# 程式設計手冊)'
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 36e5a8998018839214da00287a2bf8dc2c5925a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356259"
---
# <a name="lttypeparamrefgt-c-programming-guide"></a><span data-ttu-id="a0236-102">&lt;typeparamref&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a0236-102">&lt;typeparamref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a0236-103">語法</span><span class="sxs-lookup"><span data-stu-id="a0236-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0236-104">參數</span><span class="sxs-lookup"><span data-stu-id="a0236-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a0236-105">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0236-105">The name of the type parameter.</span></span> <span data-ttu-id="a0236-106">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="a0236-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0236-107">備註</span><span class="sxs-lookup"><span data-stu-id="a0236-107">Remarks</span></span>  
 <span data-ttu-id="a0236-108">如需泛型型別和方法中型別參數的詳細資訊，請參閱[泛型](../../../csharp/programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a0236-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="a0236-109">使用這個標記，讓文件檔案的取用者以某種明顯方式格式化單字，例如斜體。</span><span class="sxs-lookup"><span data-stu-id="a0236-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="a0236-110">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="a0236-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0236-111">範例</span><span class="sxs-lookup"><span data-stu-id="a0236-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a0236-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0236-112">See Also</span></span>  
 [<span data-ttu-id="a0236-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a0236-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a0236-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="a0236-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
