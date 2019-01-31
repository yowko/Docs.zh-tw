---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 1ef8d76699534a7408912424bcdea651d8314364
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283981"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="a0a1e-102">\<paramref > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0a1e-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="a0a1e-103">格式化文字，做為參數。</span><span class="sxs-lookup"><span data-stu-id="a0a1e-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a1e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0a1e-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0a1e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0a1e-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a0a1e-106">要參考的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a0a1e-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="a0a1e-107">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="a0a1e-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0a1e-108">備註</span><span class="sxs-lookup"><span data-stu-id="a0a1e-108">Remarks</span></span>  
 <span data-ttu-id="a0a1e-109">`<paramref>`標記可讓您指出文字是否為參數的方法。</span><span class="sxs-lookup"><span data-stu-id="a0a1e-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="a0a1e-110">以某種明顯方式格式化此參數，就可以處理 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="a0a1e-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="a0a1e-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="a0a1e-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0a1e-112">範例</span><span class="sxs-lookup"><span data-stu-id="a0a1e-112">Example</span></span>  
 <span data-ttu-id="a0a1e-113">這個範例會使用`<paramref>`參考的標記`id`參數。</span><span class="sxs-lookup"><span data-stu-id="a0a1e-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a0a1e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0a1e-114">See also</span></span>
- [<span data-ttu-id="a0a1e-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="a0a1e-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
