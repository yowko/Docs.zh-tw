---
title: <example> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f28dbf19bc03cb9d91323e9fa43a7081c1990db
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524013"
---
# <a name="example-visual-basic"></a><span data-ttu-id="21c5f-102">\<example > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="21c5f-102">\<example> (Visual Basic)</span></span>
<span data-ttu-id="21c5f-103">指定成員的範例。</span><span class="sxs-lookup"><span data-stu-id="21c5f-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="21c5f-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="21c5f-105">參數</span><span class="sxs-lookup"><span data-stu-id="21c5f-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="21c5f-106">程式碼範例的描述。</span><span class="sxs-lookup"><span data-stu-id="21c5f-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21c5f-107">備註</span><span class="sxs-lookup"><span data-stu-id="21c5f-107">Remarks</span></span>  
 <span data-ttu-id="21c5f-108">@No__t_0 標記可讓您指定如何使用方法或其他程式庫成員的範例。</span><span class="sxs-lookup"><span data-stu-id="21c5f-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="21c5f-109">這通常需要使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="21c5f-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="21c5f-110">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="21c5f-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21c5f-111">範例</span><span class="sxs-lookup"><span data-stu-id="21c5f-111">Example</span></span>  
 <span data-ttu-id="21c5f-112">這個範例會使用 `<example>` 標記來包含使用 `ID` 欄位的範例。</span><span class="sxs-lookup"><span data-stu-id="21c5f-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="21c5f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="21c5f-113">See also</span></span>

- [<span data-ttu-id="21c5f-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="21c5f-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
