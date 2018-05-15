---
title: '&lt;傳回&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: effc55bd65ae6c54575b7931529499505a9523cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="55f4a-102">&lt;傳回&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55f4a-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="55f4a-103">指定屬性或函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="55f4a-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f4a-104">語法</span><span class="sxs-lookup"><span data-stu-id="55f4a-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55f4a-105">參數</span><span class="sxs-lookup"><span data-stu-id="55f4a-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="55f4a-106">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="55f4a-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55f4a-107">備註</span><span class="sxs-lookup"><span data-stu-id="55f4a-107">Remarks</span></span>  
 <span data-ttu-id="55f4a-108">使用`<returns>`標記來描述傳回值的方法宣告的註解中。</span><span class="sxs-lookup"><span data-stu-id="55f4a-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="55f4a-109">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="55f4a-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55f4a-110">範例</span><span class="sxs-lookup"><span data-stu-id="55f4a-110">Example</span></span>  
 <span data-ttu-id="55f4a-111">這個範例會使用`<returns>`標記加入至說明`DoesRecordExist`函式會傳回。</span><span class="sxs-lookup"><span data-stu-id="55f4a-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="55f4a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55f4a-112">See Also</span></span>  
 [<span data-ttu-id="55f4a-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="55f4a-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
