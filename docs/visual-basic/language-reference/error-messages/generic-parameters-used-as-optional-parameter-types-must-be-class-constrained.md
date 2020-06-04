---
title: 用來做為選擇性參數類型的泛型參數必須受到類別條件約束
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 273ea592e73be5d76a4ffef077e691014a108347
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402923"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>用來做為選擇性參數類型的泛型參數必須受到類別條件約束
使用選擇性參數宣告的程式，該參數使用不受限於參考型別的類型參數。  
  
 您一定要為每個選擇性參數提供預設值。 如果參數是參考型別，則選擇性的值必須是 `Nothing` ，這是任何參考型別的有效值。 不過，如果參數是實值型別，則該型別必須是由 Visual Basic 預先定義的基本資料型別。 這是因為複合實值型別（例如使用者定義的結構）沒有有效的預設值。  
  
 當您針對選擇性參數使用型別參數時，必須保證它是參考型別，以避免實值型別沒有有效預設值的可能性。 這表示您必須使用 `Class` 關鍵字或特定類別的名稱來限制型別參數。  
  
 **錯誤識別碼：** BC32124  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將類型參數限制為只接受參考型別，或不要將它用於選擇性參數。  
  
## <a name="see-also"></a>另請參閱

- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Type List](../statements/type-list.md)
- [Class 陳述式](../statements/class-statement.md)
- [選擇性參數](../../programming-guide/language-features/procedures/optional-parameters.md)
- [結構](../../programming-guide/language-features/data-types/structures.md)
- [Nothing](../nothing.md)
