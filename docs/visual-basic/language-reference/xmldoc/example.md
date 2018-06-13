---
title: '&lt;範例&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8c09ab934ee7457fdff39a63c58f2546cda4d643
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598546"
---
# <a name="ltexamplegt-visual-basic"></a><span data-ttu-id="da0fc-102">&lt;範例&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da0fc-102">&lt;example&gt; (Visual Basic)</span></span>
<span data-ttu-id="da0fc-103">指定成員的範例。</span><span class="sxs-lookup"><span data-stu-id="da0fc-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da0fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="da0fc-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da0fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="da0fc-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="da0fc-106">程式碼範例的描述。</span><span class="sxs-lookup"><span data-stu-id="da0fc-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da0fc-107">備註</span><span class="sxs-lookup"><span data-stu-id="da0fc-107">Remarks</span></span>  
 <span data-ttu-id="da0fc-108">`<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。</span><span class="sxs-lookup"><span data-stu-id="da0fc-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="da0fc-109">這通常需要使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="da0fc-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="da0fc-110">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="da0fc-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da0fc-111">範例</span><span class="sxs-lookup"><span data-stu-id="da0fc-111">Example</span></span>  
 <span data-ttu-id="da0fc-112">這個範例會使用`<example>`標記来包含的範例使用`ID`欄位。</span><span class="sxs-lookup"><span data-stu-id="da0fc-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="da0fc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da0fc-113">See Also</span></span>  
 [<span data-ttu-id="da0fc-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="da0fc-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
