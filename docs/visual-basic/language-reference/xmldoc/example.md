---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8d1c2a958fa148238eaeedb9c2af3df2cb86d33d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502601"
---
# <a name="example-visual-basic"></a><span data-ttu-id="6b7fb-102">\<範例 > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b7fb-102">\<example> (Visual Basic)</span></span>
<span data-ttu-id="6b7fb-103">指定成員的範例。</span><span class="sxs-lookup"><span data-stu-id="6b7fb-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b7fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b7fb-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b7fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b7fb-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="6b7fb-106">程式碼範例的描述。</span><span class="sxs-lookup"><span data-stu-id="6b7fb-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b7fb-107">備註</span><span class="sxs-lookup"><span data-stu-id="6b7fb-107">Remarks</span></span>  
 <span data-ttu-id="6b7fb-108">`<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。</span><span class="sxs-lookup"><span data-stu-id="6b7fb-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="6b7fb-109">這通常需要使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="6b7fb-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="6b7fb-110">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="6b7fb-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b7fb-111">範例</span><span class="sxs-lookup"><span data-stu-id="6b7fb-111">Example</span></span>  
 <span data-ttu-id="6b7fb-112">這個範例會使用`<example>`包含使用的範例標記`ID`欄位。</span><span class="sxs-lookup"><span data-stu-id="6b7fb-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6b7fb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b7fb-113">See also</span></span>
- [<span data-ttu-id="6b7fb-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="6b7fb-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
