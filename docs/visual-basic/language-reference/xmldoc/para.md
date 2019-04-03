---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 16d10b2f955a4d9a02075ee4cc40dfa2b18c3541
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814506"
---
# <a name="para-visual-basic"></a><span data-ttu-id="2402f-102">\<para > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2402f-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="2402f-103">指定的內容會格式化為一個段落。</span><span class="sxs-lookup"><span data-stu-id="2402f-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2402f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2402f-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2402f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2402f-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="2402f-106">段落的文字。</span><span class="sxs-lookup"><span data-stu-id="2402f-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2402f-107">備註</span><span class="sxs-lookup"><span data-stu-id="2402f-107">Remarks</span></span>  
 <span data-ttu-id="2402f-108">`<para>`標記是供使用的標記內，例如[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)， [\<備註 >](../../../visual-basic/language-reference/xmldoc/remarks.md)，或[\<傳回 >](../../../visual-basic/language-reference/xmldoc/returns.md)，並可讓您加入文字的結構。</span><span class="sxs-lookup"><span data-stu-id="2402f-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="2402f-109">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="2402f-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2402f-110">範例</span><span class="sxs-lookup"><span data-stu-id="2402f-110">Example</span></span>  
 <span data-ttu-id="2402f-111">這個範例會使用`<para>`分割的 remarks 區段標記`UpdateRecord`方法分成兩個段落。</span><span class="sxs-lookup"><span data-stu-id="2402f-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2402f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2402f-112">See also</span></span>

- [<span data-ttu-id="2402f-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="2402f-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
