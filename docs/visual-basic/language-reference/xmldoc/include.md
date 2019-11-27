---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348454"
---
# <a name="include-visual-basic"></a><span data-ttu-id="99d93-101">\<包含 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="99d93-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="99d93-102">指的是描述原始程式碼中類型和成員的另一個檔案。</span><span class="sxs-lookup"><span data-stu-id="99d93-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d93-103">語法</span><span class="sxs-lookup"><span data-stu-id="99d93-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="99d93-104">參數</span><span class="sxs-lookup"><span data-stu-id="99d93-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="99d93-105">必要。</span><span class="sxs-lookup"><span data-stu-id="99d93-105">Required.</span></span> <span data-ttu-id="99d93-106">包含文件的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="99d93-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="99d93-107">檔案名稱可以使用路徑進行限定。</span><span class="sxs-lookup"><span data-stu-id="99d93-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="99d93-108">以雙引號（""）括住 `filename`。</span><span class="sxs-lookup"><span data-stu-id="99d93-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="99d93-109">必要。</span><span class="sxs-lookup"><span data-stu-id="99d93-109">Required.</span></span> <span data-ttu-id="99d93-110">`filename` 中導致 `name` 標記的標記路徑。</span><span class="sxs-lookup"><span data-stu-id="99d93-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="99d93-111">以雙引號（""）括住路徑。</span><span class="sxs-lookup"><span data-stu-id="99d93-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="99d93-112">必要。</span><span class="sxs-lookup"><span data-stu-id="99d93-112">Required.</span></span> <span data-ttu-id="99d93-113">標記中批註前面的名稱規範。</span><span class="sxs-lookup"><span data-stu-id="99d93-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="99d93-114">`Name` 將會有 `id`。</span><span class="sxs-lookup"><span data-stu-id="99d93-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="99d93-115">必要。</span><span class="sxs-lookup"><span data-stu-id="99d93-115">Required.</span></span> <span data-ttu-id="99d93-116">位在註解前面的標記識別碼。</span><span class="sxs-lookup"><span data-stu-id="99d93-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="99d93-117">以單引號（' '）括住識別碼。</span><span class="sxs-lookup"><span data-stu-id="99d93-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99d93-118">備註</span><span class="sxs-lookup"><span data-stu-id="99d93-118">Remarks</span></span>  
 <span data-ttu-id="99d93-119">使用 `<include>` 標記來參考另一個檔案中描述原始程式碼中類型和成員的批註。</span><span class="sxs-lookup"><span data-stu-id="99d93-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="99d93-120">這是將文件註解直接放在原始程式碼檔中的替代方案。</span><span class="sxs-lookup"><span data-stu-id="99d93-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="99d93-121">`<include>` 標記會使用 W3C XML 路徑語言（XPath）1.0 版建議。</span><span class="sxs-lookup"><span data-stu-id="99d93-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="99d93-122">如需自訂 `<include>` 使用方式的詳細資訊，請參閱 <https://www.w3.org/TR/xpath>。</span><span class="sxs-lookup"><span data-stu-id="99d93-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99d93-123">範例</span><span class="sxs-lookup"><span data-stu-id="99d93-123">Example</span></span>  
 <span data-ttu-id="99d93-124">這個範例會使用 `<include>` 標記，從稱為 `commentFile.xml`的檔案匯入成員檔批註。</span><span class="sxs-lookup"><span data-stu-id="99d93-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="99d93-125">`commentFile.xml` 的格式如下所示。</span><span class="sxs-lookup"><span data-stu-id="99d93-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99d93-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="99d93-126">See also</span></span>

- [<span data-ttu-id="99d93-127">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="99d93-127">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
