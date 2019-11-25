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
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>屬性 '\<attributename > ' 不能多次套用

屬性只能套用一次。 `AttributeUsage` 屬性會判斷屬性是否可以套用一次以上。  
  
 **錯誤識別碼：** BC30663  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定屬性只套用一次。  
  
2. 如果您使用的是您所開發的自訂屬性，請考慮將其 `AttributeUsage` 屬性變更為允許多個屬性使用，如下列範例所示。  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.AttributeUsageAttribute>
- [建立自訂屬性](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
