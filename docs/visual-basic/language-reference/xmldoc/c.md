---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 06c6899895f278fdf652725a05ecc7229805f4d4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43854726"
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="9fc06-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fc06-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="9fc06-103">表示描述內的文字是程式碼。</span><span class="sxs-lookup"><span data-stu-id="9fc06-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fc06-104">語法</span><span class="sxs-lookup"><span data-stu-id="9fc06-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fc06-105">參數</span><span class="sxs-lookup"><span data-stu-id="9fc06-105">Parameters</span></span>  
  
|<span data-ttu-id="9fc06-106">參數</span><span class="sxs-lookup"><span data-stu-id="9fc06-106">Parameter</span></span>|<span data-ttu-id="9fc06-107">描述</span><span class="sxs-lookup"><span data-stu-id="9fc06-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="9fc06-108">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="9fc06-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fc06-109">備註</span><span class="sxs-lookup"><span data-stu-id="9fc06-109">Remarks</span></span>  
 <span data-ttu-id="9fc06-110">`<c>`標記可讓您一個方法來指示應該標記為程式碼，在一段描述的文字。</span><span class="sxs-lookup"><span data-stu-id="9fc06-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="9fc06-111">請使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="9fc06-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="9fc06-112">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="9fc06-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fc06-113">範例</span><span class="sxs-lookup"><span data-stu-id="9fc06-113">Example</span></span>  
 <span data-ttu-id="9fc06-114">這個範例會使用`<c>`表示的摘要區段中的標記`Counter`是程式碼。</span><span class="sxs-lookup"><span data-stu-id="9fc06-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9fc06-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fc06-115">See Also</span></span>  
 [<span data-ttu-id="9fc06-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="9fc06-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
