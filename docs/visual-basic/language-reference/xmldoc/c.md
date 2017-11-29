---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e57cae8fd4b93fee59992d717135ad7d3d78be5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="8b254-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b254-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="8b254-103">描述內的文字表示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b254-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b254-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b254-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b254-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b254-105">Parameters</span></span>  
  
|<span data-ttu-id="8b254-106">參數</span><span class="sxs-lookup"><span data-stu-id="8b254-106">Parameter</span></span>|<span data-ttu-id="8b254-107">說明</span><span class="sxs-lookup"><span data-stu-id="8b254-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="8b254-108">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="8b254-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b254-109">備註</span><span class="sxs-lookup"><span data-stu-id="8b254-109">Remarks</span></span>  
 <span data-ttu-id="8b254-110">`<c>`標籤會提供一個方法來指示描述內的文字應該標記為程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b254-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="8b254-111">請使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b254-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="8b254-112">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="8b254-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b254-113">範例</span><span class="sxs-lookup"><span data-stu-id="8b254-113">Example</span></span>  
 <span data-ttu-id="8b254-114">這個範例會使用`<c>`表示摘要區段中的標記`Counter`是程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b254-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8b254-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b254-115">See Also</span></span>  
 [<span data-ttu-id="8b254-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="8b254-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
