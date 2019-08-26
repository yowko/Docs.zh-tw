---
title: <paramref> - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: e442b6829859ebc4dce6a0f5b6cd6cb777ab1400
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587902"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="20d89-102">\<paramref> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="20d89-102">\<paramref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="20d89-103">語法</span><span class="sxs-lookup"><span data-stu-id="20d89-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="20d89-104">參數</span><span class="sxs-lookup"><span data-stu-id="20d89-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="20d89-105">要參考的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="20d89-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="20d89-106">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="20d89-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20d89-107">備註</span><span class="sxs-lookup"><span data-stu-id="20d89-107">Remarks</span></span>  
 <span data-ttu-id="20d89-108">\<paramref> 標記提供一種方法來表示在程式碼註解中的字組，例如 \<summary> 或 \<remarks> 區塊中的字組指的是參數。</span><span class="sxs-lookup"><span data-stu-id="20d89-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="20d89-109">若要以某種不同方式 (例如，粗體或斜體字型) 格式化這個字組，您可以處理 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="20d89-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="20d89-110">編譯搭配 [/doc](../../language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="20d89-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20d89-111">範例</span><span class="sxs-lookup"><span data-stu-id="20d89-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="20d89-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20d89-112">See also</span></span>

- [<span data-ttu-id="20d89-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="20d89-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="20d89-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="20d89-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
