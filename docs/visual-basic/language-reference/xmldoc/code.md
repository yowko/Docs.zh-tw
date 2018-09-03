---
title: '&lt;程式碼&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: e66aebe35dd8f6443fefe3b07842b37270159e6e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475981"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="903f6-102">&lt;程式碼&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="903f6-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="903f6-103">指出文字是多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="903f6-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="903f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="903f6-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="903f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="903f6-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="903f6-106">要標記為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="903f6-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="903f6-107">備註</span><span class="sxs-lookup"><span data-stu-id="903f6-107">Remarks</span></span>  
 <span data-ttu-id="903f6-108">使用`<code>`多行指定為程式碼的標記。</span><span class="sxs-lookup"><span data-stu-id="903f6-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="903f6-109">[\<c>](../../../visual-basic/language-reference/xmldoc/c.md) 則用來指出在一段描述中應該標記為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="903f6-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="903f6-110">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="903f6-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="903f6-111">範例</span><span class="sxs-lookup"><span data-stu-id="903f6-111">Example</span></span>  
 <span data-ttu-id="903f6-112">這個範例會使用\<程式碼 > 標記來包含程式碼範例使用`ID`欄位。</span><span class="sxs-lookup"><span data-stu-id="903f6-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="903f6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="903f6-113">See Also</span></span>  
 [<span data-ttu-id="903f6-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="903f6-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
