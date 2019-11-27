---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348516"
---
# <a name="c-visual-basic"></a><span data-ttu-id="59e4e-101">\<c > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="59e4e-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="59e4e-102">表示描述中的文字是程式碼。</span><span class="sxs-lookup"><span data-stu-id="59e4e-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e4e-103">語法</span><span class="sxs-lookup"><span data-stu-id="59e4e-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="59e4e-104">參數</span><span class="sxs-lookup"><span data-stu-id="59e4e-104">Parameters</span></span>  
  
|<span data-ttu-id="59e4e-105">參數</span><span class="sxs-lookup"><span data-stu-id="59e4e-105">Parameter</span></span>|<span data-ttu-id="59e4e-106">描述</span><span class="sxs-lookup"><span data-stu-id="59e4e-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="59e4e-107">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="59e4e-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59e4e-108">備註</span><span class="sxs-lookup"><span data-stu-id="59e4e-108">Remarks</span></span>  
 <span data-ttu-id="59e4e-109">`<c>` 標籤可讓您指定描述中的文字應該標記為程式碼。</span><span class="sxs-lookup"><span data-stu-id="59e4e-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="59e4e-110">請使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="59e4e-110">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="59e4e-111">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="59e4e-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59e4e-112">範例</span><span class="sxs-lookup"><span data-stu-id="59e4e-112">Example</span></span>  
 <span data-ttu-id="59e4e-113">這個範例會使用 [摘要] 區段中的 [`<c>`] 標籤，指出 `Counter` 是程式碼。</span><span class="sxs-lookup"><span data-stu-id="59e4e-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="59e4e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="59e4e-114">See also</span></span>

- [<span data-ttu-id="59e4e-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="59e4e-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
