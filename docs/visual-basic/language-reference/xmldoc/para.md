---
title: <para> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: aa4e4c14717b69b9ca4595e20c768a2b91aac1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524735"
---
# <a name="para-visual-basic"></a><span data-ttu-id="4b869-102">\<para > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4b869-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="4b869-103">指定將內容格式化為段落。</span><span class="sxs-lookup"><span data-stu-id="4b869-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b869-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b869-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b869-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b869-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="4b869-106">段落的文字。</span><span class="sxs-lookup"><span data-stu-id="4b869-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b869-107">備註</span><span class="sxs-lookup"><span data-stu-id="4b869-107">Remarks</span></span>  
 <span data-ttu-id="4b869-108">@No__t_0 標記是用於標記內（例如[\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md)、 [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)或[\<returns >](../../../visual-basic/language-reference/xmldoc/returns.md)），並可讓您將結構新增至文字。</span><span class="sxs-lookup"><span data-stu-id="4b869-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="4b869-109">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="4b869-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b869-110">範例</span><span class="sxs-lookup"><span data-stu-id="4b869-110">Example</span></span>  
 <span data-ttu-id="4b869-111">這個範例會使用 `<para>` 標記，將 `UpdateRecord` 方法的備註區段分割成兩個段落。</span><span class="sxs-lookup"><span data-stu-id="4b869-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4b869-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b869-112">See also</span></span>

- [<span data-ttu-id="4b869-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="4b869-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
