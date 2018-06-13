---
title: '&lt;值&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: f33a4ec32b45d8996bd39f0cc49097b5fd9252e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602454"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="6217e-102">&lt;值&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6217e-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="6217e-103">指定屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="6217e-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6217e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6217e-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6217e-105">參數</span><span class="sxs-lookup"><span data-stu-id="6217e-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="6217e-106">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="6217e-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6217e-107">備註</span><span class="sxs-lookup"><span data-stu-id="6217e-107">Remarks</span></span>  
 <span data-ttu-id="6217e-108">使用`<value>`標記來描述屬性。</span><span class="sxs-lookup"><span data-stu-id="6217e-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="6217e-109">請注意，當您將該屬性在 Visual Studio 開發環境中使用的程式碼精靈，它會新增[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)新屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="6217e-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="6217e-110">接著，您應該手動加入`<value>`標記來描述此屬性代表的值。</span><span class="sxs-lookup"><span data-stu-id="6217e-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="6217e-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="6217e-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6217e-112">範例</span><span class="sxs-lookup"><span data-stu-id="6217e-112">Example</span></span>  
 <span data-ttu-id="6217e-113">這個範例會使用`<value>`標記來描述哪些值`Counter`屬性會保存。</span><span class="sxs-lookup"><span data-stu-id="6217e-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6217e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6217e-114">See Also</span></span>  
 [<span data-ttu-id="6217e-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="6217e-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
