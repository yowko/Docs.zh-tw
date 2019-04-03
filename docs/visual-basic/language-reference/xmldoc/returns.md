---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 5a0ff0da7cf26a1cea75a5b2e4678593d9b72f54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827158"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="18204-102">\<傳回 > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18204-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="18204-103">指定屬性或函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="18204-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18204-104">語法</span><span class="sxs-lookup"><span data-stu-id="18204-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="18204-105">參數</span><span class="sxs-lookup"><span data-stu-id="18204-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="18204-106">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="18204-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18204-107">備註</span><span class="sxs-lookup"><span data-stu-id="18204-107">Remarks</span></span>  
 <span data-ttu-id="18204-108">使用`<returns>`標記來描述傳回值的方法宣告的註解中。</span><span class="sxs-lookup"><span data-stu-id="18204-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="18204-109">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="18204-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18204-110">範例</span><span class="sxs-lookup"><span data-stu-id="18204-110">Example</span></span>  
 <span data-ttu-id="18204-111">這個範例會使用`<returns>`標記來解釋什麼`DoesRecordExist`函式會傳回。</span><span class="sxs-lookup"><span data-stu-id="18204-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="18204-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18204-112">See also</span></span>

- [<span data-ttu-id="18204-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="18204-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
