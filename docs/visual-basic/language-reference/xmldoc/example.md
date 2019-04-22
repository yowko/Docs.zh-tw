---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 510b00d2220b9c65b0e2b8fa3ead70925a9f54ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821916"
---
# <a name="example-visual-basic"></a><span data-ttu-id="e7ac1-102">\<範例 > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7ac1-102">\<example> (Visual Basic)</span></span>
<span data-ttu-id="e7ac1-103">指定成員的範例。</span><span class="sxs-lookup"><span data-stu-id="e7ac1-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ac1-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7ac1-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7ac1-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7ac1-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e7ac1-106">程式碼範例的描述。</span><span class="sxs-lookup"><span data-stu-id="e7ac1-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7ac1-107">備註</span><span class="sxs-lookup"><span data-stu-id="e7ac1-107">Remarks</span></span>  
 <span data-ttu-id="e7ac1-108">`<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。</span><span class="sxs-lookup"><span data-stu-id="e7ac1-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="e7ac1-109">這通常需要使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="e7ac1-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="e7ac1-110">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="e7ac1-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7ac1-111">範例</span><span class="sxs-lookup"><span data-stu-id="e7ac1-111">Example</span></span>  
 <span data-ttu-id="e7ac1-112">這個範例會使用`<example>`包含使用的範例標記`ID`欄位。</span><span class="sxs-lookup"><span data-stu-id="e7ac1-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e7ac1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7ac1-113">See also</span></span>

- [<span data-ttu-id="e7ac1-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="e7ac1-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
