---
title: "'<keyword>' 只能出現在執行個體方法中"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 5ff82b932f9bea4c7fd087651e34277ef94bc27c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946636"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>'\<關鍵字 >' 只能在執行個體方法
`Me`， `MyClass`，和`MyBase`關鍵字參考特定的類別執行個體。 您無法使用它們在共用`Function`或`Sub`程序。  
  
 **錯誤 ID:** BC30043  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 從程序中移除關鍵字，或移除`Shared`從程序宣告的關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [物件變數指派](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
