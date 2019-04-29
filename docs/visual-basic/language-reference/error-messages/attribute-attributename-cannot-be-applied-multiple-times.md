---
title: 屬性 '<attributename>' 不可以多次套用
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: da4a766e2617308cb33b9673a88db9e7a954152a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935313"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="d073f-102">屬性 '\<屬性名稱 >' 不可套用多次</span><span class="sxs-lookup"><span data-stu-id="d073f-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>
<span data-ttu-id="d073f-103">屬性只能套用一次。</span><span class="sxs-lookup"><span data-stu-id="d073f-103">The attribute can only be applied once.</span></span> <span data-ttu-id="d073f-104">`AttributeUsage`屬性會決定是否可以多次套用屬性。</span><span class="sxs-lookup"><span data-stu-id="d073f-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="d073f-105">**錯誤 ID:** BC30663</span><span class="sxs-lookup"><span data-stu-id="d073f-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d073f-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d073f-106">To correct this error</span></span>  
  
1. <span data-ttu-id="d073f-107">請確定屬性只能套用一次。</span><span class="sxs-lookup"><span data-stu-id="d073f-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="d073f-108">如果您使用的您開發的自訂屬性，請考慮變更其`AttributeUsage`屬性，以允許多個屬性使用方式，如同下列範例。</span><span class="sxs-lookup"><span data-stu-id="d073f-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d073f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d073f-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="d073f-110">建立自訂屬性</span><span class="sxs-lookup"><span data-stu-id="d073f-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="d073f-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="d073f-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
