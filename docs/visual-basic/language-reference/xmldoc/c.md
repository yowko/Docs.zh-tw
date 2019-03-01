---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 5f07b9cc084c73a7dcaf8c4d5f631519e550781e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979480"
---
# <a name="c-visual-basic"></a><span data-ttu-id="c6626-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6626-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="c6626-103">表示描述內的文字是程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6626-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6626-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6626-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6626-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6626-105">Parameters</span></span>  
  
|<span data-ttu-id="c6626-106">參數</span><span class="sxs-lookup"><span data-stu-id="c6626-106">Parameter</span></span>|<span data-ttu-id="c6626-107">描述</span><span class="sxs-lookup"><span data-stu-id="c6626-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="c6626-108">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="c6626-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6626-109">備註</span><span class="sxs-lookup"><span data-stu-id="c6626-109">Remarks</span></span>  
 <span data-ttu-id="c6626-110">`<c>`標記可讓您一個方法來指示應該標記為程式碼，在一段描述的文字。</span><span class="sxs-lookup"><span data-stu-id="c6626-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="c6626-111">請使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6626-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="c6626-112">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="c6626-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6626-113">範例</span><span class="sxs-lookup"><span data-stu-id="c6626-113">Example</span></span>  
 <span data-ttu-id="c6626-114">這個範例會使用`<c>`表示的摘要區段中的標記`Counter`是程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6626-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c6626-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6626-115">See also</span></span>
- [<span data-ttu-id="c6626-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="c6626-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
