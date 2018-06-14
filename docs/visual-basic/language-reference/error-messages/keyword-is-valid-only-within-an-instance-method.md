---
title: '&#39;&lt;關鍵字&gt;&#39;只能在執行個體方法'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 2d9e26aa7dccf1b9c6390a20a59b10a0d248969d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586356"
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>&#39;&lt;關鍵字&gt;&#39;只能在執行個體方法
`Me`， `MyClass`，和`MyBase`關鍵字參考特定的類別執行個體。 您無法使用它們內共用`Function`或`Sub`程序。  
  
 **錯誤 ID:** BC30043  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除程序中的關鍵字，或移除`Shared`程序宣告中的關鍵字。  
  
## <a name="see-also"></a>另請參閱  
 [物件變數指派](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
