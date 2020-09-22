---
title: "'<keyword>' 只能出現在執行個體方法中"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: af436b8fd57ff0d2747c766a64af175760931009
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873898"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>'\<keyword>' 只能出現在執行個體方法中

`Me`、 `MyClass` 和關鍵字會 `MyBase` 參考特定的類別實例。 您無法在共用或程式中使用它們 `Function` `Sub` 。  
  
 **錯誤識別碼：** BC30043  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請從程式中移除關鍵字，或從程式 `Shared` 聲明中移除關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [物件變數指派](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase 及 MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
