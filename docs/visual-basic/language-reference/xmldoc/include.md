---
title: <include> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: ea14cc8182b8917a0805fbc509a0000c6df67462
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267036"
---
# <a name="include-visual-basic"></a><span data-ttu-id="eb216-102">\<包含 > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb216-102">\<include> (Visual Basic)</span></span>
<span data-ttu-id="eb216-103">參考描述的類型和成員在原始程式碼中的另一個檔案。</span><span class="sxs-lookup"><span data-stu-id="eb216-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb216-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb216-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb216-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb216-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="eb216-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="eb216-106">Required.</span></span> <span data-ttu-id="eb216-107">包含文件的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="eb216-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="eb216-108">檔案名稱可以使用路徑進行限定。</span><span class="sxs-lookup"><span data-stu-id="eb216-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="eb216-109">括住`filename`以雙引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="eb216-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="eb216-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="eb216-110">Required.</span></span> <span data-ttu-id="eb216-111">`filename` 中導致 `name` 標記的標記路徑。</span><span class="sxs-lookup"><span data-stu-id="eb216-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="eb216-112">請將路徑括在雙引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="eb216-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="eb216-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="eb216-113">Required.</span></span> <span data-ttu-id="eb216-114">在註解前面的標記名稱規範。</span><span class="sxs-lookup"><span data-stu-id="eb216-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="eb216-115">`Name` 將會有`id`。</span><span class="sxs-lookup"><span data-stu-id="eb216-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="eb216-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="eb216-116">Required.</span></span> <span data-ttu-id="eb216-117">位在註解前面的標記識別碼。</span><span class="sxs-lookup"><span data-stu-id="eb216-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="eb216-118">請將識別碼括在單引號 (' ')。</span><span class="sxs-lookup"><span data-stu-id="eb216-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb216-119">備註</span><span class="sxs-lookup"><span data-stu-id="eb216-119">Remarks</span></span>  
 <span data-ttu-id="eb216-120">使用`<include>`標記來參考另一個檔案中描述的類型的註解和在原始程式碼中的成員。</span><span class="sxs-lookup"><span data-stu-id="eb216-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="eb216-121">這是將文件註解直接放在原始程式碼檔中的替代方案。</span><span class="sxs-lookup"><span data-stu-id="eb216-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="eb216-122">`<include>`標記使用 W3C XML 路徑語言 (XPath) 1.0 版建議事項。</span><span class="sxs-lookup"><span data-stu-id="eb216-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="eb216-123">如需有關如何自訂您`<include>`使用，請參閱<https://www.w3.org/TR/xpath>。</span><span class="sxs-lookup"><span data-stu-id="eb216-123">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb216-124">範例</span><span class="sxs-lookup"><span data-stu-id="eb216-124">Example</span></span>  
 <span data-ttu-id="eb216-125">這個範例會使用`<include>`從名為的檔案匯入成員文件註解的標記`commentFile.xml`。</span><span class="sxs-lookup"><span data-stu-id="eb216-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="eb216-126">格式`commentFile.xml`如下所示。</span><span class="sxs-lookup"><span data-stu-id="eb216-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb216-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb216-127">See also</span></span>
- [<span data-ttu-id="eb216-128">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="eb216-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
