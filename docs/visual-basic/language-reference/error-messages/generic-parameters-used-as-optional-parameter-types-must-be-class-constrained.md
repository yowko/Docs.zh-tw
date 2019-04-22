---
title: 用來做為選擇性參數類型的泛型參數必須受到類別條件約束
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 9b0293472f5eda74c2bf8fb215e15ae5cf8d8b98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813895"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>用來做為選擇性參數類型的泛型參數必須受到類別條件約束
程序會宣告使用不受限制是參考類型的型別參數的選擇性參數。  
  
 您一律必須提供每個選擇性參數的預設值。 如果參數是參考型別，選擇性的值必須是`Nothing`，這是任何參考型別的有效的值。 不過，如果參數是實值類型，該類型必須是基本資料類型預先定義的 Visual basic。 這是因為複合值類型，例如使用者定義的結構，沒有任何有效的預設值。  
  
 當您使用的型別參數為選擇性的參數時，您必須保證它是為了避免沒有有效的預設值的實值類型為參考型別。 這表示您必須使用限制的型別參數`Class`關鍵字或特定類別的名稱。  
  
 **錯誤 ID:** BC32124  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   限制類型參數接受僅參考型別，或請勿使用它在選擇性參數。  
  
## <a name="see-also"></a>另請參閱

- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [類型清單](../../../visual-basic/language-reference/statements/type-list.md)
- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)
- [選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
