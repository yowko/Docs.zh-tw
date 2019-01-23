---
title: '&lt;程式碼&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 8a4708a7b50b0e221c1ebe7f95d4f8ff80cd1ebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566303"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="eed62-102">&lt;程式碼&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eed62-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="eed62-103">指出文字是多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="eed62-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed62-104">語法</span><span class="sxs-lookup"><span data-stu-id="eed62-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eed62-105">參數</span><span class="sxs-lookup"><span data-stu-id="eed62-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="eed62-106">要標記為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="eed62-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eed62-107">備註</span><span class="sxs-lookup"><span data-stu-id="eed62-107">Remarks</span></span>  
 <span data-ttu-id="eed62-108">使用`<code>`多行指定為程式碼的標記。</span><span class="sxs-lookup"><span data-stu-id="eed62-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="eed62-109">[\<c>](../../../visual-basic/language-reference/xmldoc/c.md) 則用來指出在一段描述中應該標記為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="eed62-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="eed62-110">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="eed62-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eed62-111">範例</span><span class="sxs-lookup"><span data-stu-id="eed62-111">Example</span></span>  
 <span data-ttu-id="eed62-112">這個範例會使用\<程式碼 > 標記來包含程式碼範例使用`ID`欄位。</span><span class="sxs-lookup"><span data-stu-id="eed62-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eed62-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eed62-113">See also</span></span>
- [<span data-ttu-id="eed62-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="eed62-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
