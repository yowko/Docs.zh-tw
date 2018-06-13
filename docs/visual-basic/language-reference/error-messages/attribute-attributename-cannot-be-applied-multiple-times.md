---
title: 屬性&#39; &lt;attributename&gt; &#39;不可套用多次
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: df97a4e391406661db98eb1c958c0e12e45b6c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584855"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="58099-102">屬性&#39; &lt;attributename&gt; &#39;不可套用多次</span><span class="sxs-lookup"><span data-stu-id="58099-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="58099-103">屬性只能套用一次。</span><span class="sxs-lookup"><span data-stu-id="58099-103">The attribute can only be applied once.</span></span> <span data-ttu-id="58099-104">`AttributeUsage`屬性會決定是否可以多次套用屬性。</span><span class="sxs-lookup"><span data-stu-id="58099-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="58099-105">**錯誤 ID:** BC30663</span><span class="sxs-lookup"><span data-stu-id="58099-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58099-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="58099-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="58099-107">請確定屬性只能套用一次。</span><span class="sxs-lookup"><span data-stu-id="58099-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="58099-108">如果您使用的您開發的自訂屬性，請考慮變更其`AttributeUsage`屬性，以允許多個屬性使用方式，如同下列範例。</span><span class="sxs-lookup"><span data-stu-id="58099-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58099-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58099-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="58099-110">建立自訂屬性</span><span class="sxs-lookup"><span data-stu-id="58099-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="58099-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="58099-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
