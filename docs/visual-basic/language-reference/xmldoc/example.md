---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f36ac1337dd0d1400180fbd3deae2bb24ad9c58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348486"
---
# <a name="example-visual-basic"></a><span data-ttu-id="27f05-101">\<範例 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="27f05-101">\<example> (Visual Basic)</span></span>
<span data-ttu-id="27f05-102">指定成員的範例。</span><span class="sxs-lookup"><span data-stu-id="27f05-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f05-103">語法</span><span class="sxs-lookup"><span data-stu-id="27f05-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="27f05-104">參數</span><span class="sxs-lookup"><span data-stu-id="27f05-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="27f05-105">程式碼範例的描述。</span><span class="sxs-lookup"><span data-stu-id="27f05-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27f05-106">備註</span><span class="sxs-lookup"><span data-stu-id="27f05-106">Remarks</span></span>  
 <span data-ttu-id="27f05-107">`<example>` 標記可讓您指定如何使用方法或其他程式庫成員的範例。</span><span class="sxs-lookup"><span data-stu-id="27f05-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="27f05-108">這通常需要使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="27f05-108">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="27f05-109">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="27f05-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27f05-110">範例</span><span class="sxs-lookup"><span data-stu-id="27f05-110">Example</span></span>  
 <span data-ttu-id="27f05-111">這個範例會使用 `<example>` 標記來包含使用 `ID` 欄位的範例。</span><span class="sxs-lookup"><span data-stu-id="27f05-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="27f05-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27f05-112">See also</span></span>

- [<span data-ttu-id="27f05-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="27f05-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
