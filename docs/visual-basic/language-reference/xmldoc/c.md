---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 4ea19ed5330dcbb8fcd84708d1546a81d909b04e
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523936"
---
# <a name="c-visual-basic"></a><span data-ttu-id="bdce0-102">\<c > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="bdce0-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="bdce0-103">表示描述中的文字是程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdce0-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdce0-104">語法</span><span class="sxs-lookup"><span data-stu-id="bdce0-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdce0-105">參數</span><span class="sxs-lookup"><span data-stu-id="bdce0-105">Parameters</span></span>  
  
|<span data-ttu-id="bdce0-106">參數</span><span class="sxs-lookup"><span data-stu-id="bdce0-106">Parameter</span></span>|<span data-ttu-id="bdce0-107">描述</span><span class="sxs-lookup"><span data-stu-id="bdce0-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="bdce0-108">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="bdce0-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdce0-109">備註</span><span class="sxs-lookup"><span data-stu-id="bdce0-109">Remarks</span></span>  
 <span data-ttu-id="bdce0-110">@No__t_0 標籤可讓您指定描述中的文字應該標記為程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdce0-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="bdce0-111">請使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdce0-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="bdce0-112">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="bdce0-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdce0-113">範例</span><span class="sxs-lookup"><span data-stu-id="bdce0-113">Example</span></span>  
 <span data-ttu-id="bdce0-114">這個範例會使用 [摘要] 區段中的 [`<c>`] 標籤，指出 `Counter` 是程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdce0-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bdce0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="bdce0-115">See also</span></span>

- [<span data-ttu-id="bdce0-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="bdce0-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
