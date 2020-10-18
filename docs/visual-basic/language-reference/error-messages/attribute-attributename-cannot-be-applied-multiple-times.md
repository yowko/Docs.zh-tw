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
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a>BC30663：無法多次套用屬性 ' \<attributename> '

屬性只能套用一次。 `AttributeUsage`屬性可判斷屬性是否可以套用一次以上。

 **錯誤識別碼：** BC30663

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 請確定屬性只套用一次。

2. 如果您要使用您所開發的自訂屬性，請考慮將其 `AttributeUsage` 屬性變更為允許多個屬性使用方式，如下列範例所示。

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a>另請參閱

- <xref:System.AttributeUsageAttribute>
- [建立自訂屬性](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../programming-guide/concepts/attributes/attributeusage.md)
