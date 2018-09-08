---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: fa11c713a5ed5793b50865753f8bcdeaabf56e83
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132353"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="05ef5-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05ef5-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="05ef5-103">指定的內容會格式化為一個段落。</span><span class="sxs-lookup"><span data-stu-id="05ef5-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ef5-104">語法</span><span class="sxs-lookup"><span data-stu-id="05ef5-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05ef5-105">參數</span><span class="sxs-lookup"><span data-stu-id="05ef5-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="05ef5-106">段落的文字。</span><span class="sxs-lookup"><span data-stu-id="05ef5-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05ef5-107">備註</span><span class="sxs-lookup"><span data-stu-id="05ef5-107">Remarks</span></span>  
 <span data-ttu-id="05ef5-108">`<para>`標記是供使用的標記內，例如[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)， [\<備註 >](../../../visual-basic/language-reference/xmldoc/remarks.md)，或[\<傳回 >](../../../visual-basic/language-reference/xmldoc/returns.md)，並可讓您加入文字的結構。</span><span class="sxs-lookup"><span data-stu-id="05ef5-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="05ef5-109">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="05ef5-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05ef5-110">範例</span><span class="sxs-lookup"><span data-stu-id="05ef5-110">Example</span></span>  
 <span data-ttu-id="05ef5-111">這個範例會使用`<para>`分割的 remarks 區段標記`UpdateRecord`方法分成兩個段落。</span><span class="sxs-lookup"><span data-stu-id="05ef5-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="05ef5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05ef5-112">See Also</span></span>  
 [<span data-ttu-id="05ef5-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="05ef5-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
