---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 3bc4393d2fa14f804c6383780e238b1ac2610a94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352207"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="cd657-101">\<摘要 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="cd657-101">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="cd657-102">指定成員的摘要。</span><span class="sxs-lookup"><span data-stu-id="cd657-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd657-103">語法</span><span class="sxs-lookup"><span data-stu-id="cd657-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd657-104">參數</span><span class="sxs-lookup"><span data-stu-id="cd657-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="cd657-105">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="cd657-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd657-106">備註</span><span class="sxs-lookup"><span data-stu-id="cd657-106">Remarks</span></span>  
 <span data-ttu-id="cd657-107">使用 `<summary>` 標記來描述類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="cd657-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="cd657-108">使用 [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) 新增類型描述的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="cd657-108">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="cd657-109">`<summary>` 標記的文字是 IntelliSense 中類型的唯一資訊來源，也會顯示在物件瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="cd657-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="cd657-110">如需物件瀏覽器的相關資訊，請參閱[查看程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="cd657-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="cd657-111">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="cd657-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd657-112">範例</span><span class="sxs-lookup"><span data-stu-id="cd657-112">Example</span></span>  
 <span data-ttu-id="cd657-113">這個範例會使用 `<summary>` 標記來描述 `ResetCounter` 方法和 `Counter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd657-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cd657-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd657-114">See also</span></span>

- [<span data-ttu-id="cd657-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="cd657-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
