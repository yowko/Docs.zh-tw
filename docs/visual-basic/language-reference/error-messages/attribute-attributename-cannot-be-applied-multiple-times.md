---
title: 屬性 '<attributename>' 不可以多次套用
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968231"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="0b684-102">屬性 '\<attributename > ' 不能多次套用</span><span class="sxs-lookup"><span data-stu-id="0b684-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="0b684-103">屬性只能套用一次。</span><span class="sxs-lookup"><span data-stu-id="0b684-103">The attribute can only be applied once.</span></span> <span data-ttu-id="0b684-104">`AttributeUsage` 屬性會判斷屬性是否可以套用一次以上。</span><span class="sxs-lookup"><span data-stu-id="0b684-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="0b684-105">**錯誤識別碼：** BC30663</span><span class="sxs-lookup"><span data-stu-id="0b684-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0b684-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0b684-106">To correct this error</span></span>  
  
1. <span data-ttu-id="0b684-107">請確定屬性只套用一次。</span><span class="sxs-lookup"><span data-stu-id="0b684-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="0b684-108">如果您使用的是您所開發的自訂屬性，請考慮將其 `AttributeUsage` 屬性變更為允許多個屬性使用，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0b684-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b684-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b684-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="0b684-110">建立自訂屬性</span><span class="sxs-lookup"><span data-stu-id="0b684-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="0b684-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="0b684-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
