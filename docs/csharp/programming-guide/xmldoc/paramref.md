---
title: "&lt;paramref&gt; (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fff532c02538f121ebe399e1780d8c19d9d6633a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="e3511-102">&lt;paramref&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e3511-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e3511-103">語法</span><span class="sxs-lookup"><span data-stu-id="e3511-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3511-104">參數</span><span class="sxs-lookup"><span data-stu-id="e3511-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e3511-105">要參考的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="e3511-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="e3511-106">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="e3511-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3511-107">備註</span><span class="sxs-lookup"><span data-stu-id="e3511-107">Remarks</span></span>  
 <span data-ttu-id="e3511-108">\<paramref> 標記提供一種方法來表示在程式碼註解中的字組，例如 \<summary> 或 \<remarks> 區塊中的字組指的是參數。</span><span class="sxs-lookup"><span data-stu-id="e3511-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="e3511-109">若要以某種不同方式 (例如，粗體或斜體字型) 格式化這個字組，您可以處理 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3511-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="e3511-110">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="e3511-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3511-111">範例</span><span class="sxs-lookup"><span data-stu-id="e3511-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e3511-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3511-112">See Also</span></span>  
 [<span data-ttu-id="e3511-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e3511-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3511-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="e3511-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
