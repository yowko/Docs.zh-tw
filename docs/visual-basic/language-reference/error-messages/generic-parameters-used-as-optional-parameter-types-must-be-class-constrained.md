---
title: 用來做為選擇性參數類型的泛型參數必須受到類別條件約束
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 5e0d4eaf7557eb9a544a8845299f3d69dbb78486
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163216"
---
# <a name="bc32124-generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>BC32124：用來當做選擇性參數類型的泛型參數必須是類別條件約束

使用選擇性參數宣告程式，此參數使用的類型參數不受限於參考型別。

 您必須一律為每個選擇性參數提供預設值。 如果參數是參考型別，則選擇性的值必須是 `Nothing` ，也就是任何參考型別的有效值。 但是，如果參數是實值型別，則該型別必須是 Visual Basic 預先定義的基本資料型別。 這是因為複合實值型別（例如使用者定義的結構）沒有有效的預設值。

 當您針對選擇性參數使用型別參數時，必須保證它是參考型別，以避免實值型別的可能沒有有效的預設值。 這表示您必須使用 `Class` 關鍵字或特定類別的名稱來限制類型參數。

 **錯誤識別碼：** BC32124

## <a name="to-correct-this-error"></a>更正這個錯誤

- 將型別參數限制為只接受參考型別，或不要將它用於選擇性參數。

## <a name="see-also"></a>另請參閱

- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Type List](../statements/type-list.md)
- [Class 陳述式](../statements/class-statement.md)
- [選擇性參數](../../programming-guide/language-features/procedures/optional-parameters.md)
- [結構](../../programming-guide/language-features/data-types/structures.md)
- [什麼](../nothing.md)
