---
title: 屬性 '<attributename>' 不可以多次套用
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 27cbe6d0043179c4a5d52baae06bad805f9d1d3a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162657"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="a244e-102">BC30663：無法多次套用屬性 ' \<attributename> '</span><span class="sxs-lookup"><span data-stu-id="a244e-102">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="a244e-103">屬性只能套用一次。</span><span class="sxs-lookup"><span data-stu-id="a244e-103">The attribute can only be applied once.</span></span> <span data-ttu-id="a244e-104">`AttributeUsage`屬性可判斷屬性是否可以套用一次以上。</span><span class="sxs-lookup"><span data-stu-id="a244e-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="a244e-105">**錯誤識別碼：** BC30663</span><span class="sxs-lookup"><span data-stu-id="a244e-105">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a244e-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a244e-106">To correct this error</span></span>

1. <span data-ttu-id="a244e-107">請確定屬性只套用一次。</span><span class="sxs-lookup"><span data-stu-id="a244e-107">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="a244e-108">如果您要使用您所開發的自訂屬性，請考慮將其 `AttributeUsage` 屬性變更為允許多個屬性使用方式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a244e-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="a244e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a244e-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="a244e-110">建立自訂屬性</span><span class="sxs-lookup"><span data-stu-id="a244e-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="a244e-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="a244e-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
