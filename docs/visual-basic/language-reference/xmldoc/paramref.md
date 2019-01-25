---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 44b8124068a8cfb507fcbe389c19ff0c9168b5db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700243"
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="1b03c-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b03c-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="1b03c-103">格式化文字，做為參數。</span><span class="sxs-lookup"><span data-stu-id="1b03c-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b03c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b03c-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b03c-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b03c-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1b03c-106">要參考的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="1b03c-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="1b03c-107">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="1b03c-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b03c-108">備註</span><span class="sxs-lookup"><span data-stu-id="1b03c-108">Remarks</span></span>  
 <span data-ttu-id="1b03c-109">`<paramref>`標記可讓您指出文字是否為參數的方法。</span><span class="sxs-lookup"><span data-stu-id="1b03c-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="1b03c-110">以某種明顯方式格式化此參數，就可以處理 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1b03c-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="1b03c-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="1b03c-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b03c-112">範例</span><span class="sxs-lookup"><span data-stu-id="1b03c-112">Example</span></span>  
 <span data-ttu-id="1b03c-113">這個範例會使用`<paramref>`參考的標記`id`參數。</span><span class="sxs-lookup"><span data-stu-id="1b03c-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1b03c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b03c-114">See also</span></span>
- [<span data-ttu-id="1b03c-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="1b03c-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
