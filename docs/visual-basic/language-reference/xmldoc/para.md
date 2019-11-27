---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 8f28ecc33eea99150509bb4bade047489b4b826b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352308"
---
# <a name="para-visual-basic"></a><span data-ttu-id="10886-101">\<段落 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="10886-101">\<para> (Visual Basic)</span></span>
<span data-ttu-id="10886-102">指定將內容格式化為段落。</span><span class="sxs-lookup"><span data-stu-id="10886-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10886-103">語法</span><span class="sxs-lookup"><span data-stu-id="10886-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="10886-104">參數</span><span class="sxs-lookup"><span data-stu-id="10886-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="10886-105">段落的文字。</span><span class="sxs-lookup"><span data-stu-id="10886-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10886-106">備註</span><span class="sxs-lookup"><span data-stu-id="10886-106">Remarks</span></span>  
 <span data-ttu-id="10886-107">`<para>` 標記用於標記內部，例如[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)、 [\<備註 >](../../../visual-basic/language-reference/xmldoc/remarks.md)或\<會傳回[>](../../../visual-basic/language-reference/xmldoc/returns.md)，並可讓您將結構新增至文字。</span><span class="sxs-lookup"><span data-stu-id="10886-107">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="10886-108">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="10886-108">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10886-109">範例</span><span class="sxs-lookup"><span data-stu-id="10886-109">Example</span></span>  
 <span data-ttu-id="10886-110">這個範例會使用 `<para>` 標記，將 `UpdateRecord` 方法的備註區段分割成兩個段落。</span><span class="sxs-lookup"><span data-stu-id="10886-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="10886-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="10886-111">See also</span></span>

- [<span data-ttu-id="10886-112">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="10886-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
