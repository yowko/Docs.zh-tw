---
title: '&lt;值&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: ef14836c438cf6a1de300270d9882c1e53e716ee
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855929"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="5468d-102">&lt;值&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5468d-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="5468d-103">指定屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="5468d-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5468d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5468d-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5468d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5468d-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="5468d-106">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="5468d-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5468d-107">備註</span><span class="sxs-lookup"><span data-stu-id="5468d-107">Remarks</span></span>  
 <span data-ttu-id="5468d-108">使用`<value>`標記來描述屬性。</span><span class="sxs-lookup"><span data-stu-id="5468d-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="5468d-109">請注意，當您新增屬性，在 Visual Studio 開發環境中使用的程式碼精靈，它會新增[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)新屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="5468d-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="5468d-110">接著，您應該手動新增`<value>`標記來描述所代表之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5468d-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="5468d-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="5468d-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5468d-112">範例</span><span class="sxs-lookup"><span data-stu-id="5468d-112">Example</span></span>  
 <span data-ttu-id="5468d-113">這個範例會使用`<value>`標記來描述哪些值`Counter`屬性會保存。</span><span class="sxs-lookup"><span data-stu-id="5468d-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5468d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5468d-114">See Also</span></span>  
 [<span data-ttu-id="5468d-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="5468d-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
