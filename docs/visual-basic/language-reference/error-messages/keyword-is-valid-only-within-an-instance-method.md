---
title: "'<keyword>' 只能出現在執行個體方法中"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: af3bc95e2db88577c7c53e4b58fb60aed8a83453
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267637"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>'\<關鍵字 >' 只能在執行個體方法
`Me`， `MyClass`，和`MyBase`關鍵字參考特定的類別執行個體。 您無法使用它們在共用`Function`或`Sub`程序。  
  
 **錯誤 ID:** BC30043  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   從程序中移除關鍵字，或移除`Shared`從程序宣告的關鍵字。  
  
## <a name="see-also"></a>另請參閱
- [物件變數指派](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
