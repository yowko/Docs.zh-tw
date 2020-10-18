---
title: 無法存取屬性 '<propertyname>' 的 'Set' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3cf828eb5f11090a74a65388e2b89a191046a456
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162241"
---
# <a name="bc31102-set-accessor-of-property-propertyname-is-not-accessible"></a>BC31102：無法存取屬性 ' ' 的 ' Set ' 存取子 \<propertyname>

當語句無法存取屬性的程式時，語句會嘗試儲存屬性的值 `Set` 。

 如果 [Set 語句](../statements/set-statement.md) 標示了更嚴格的存取層級，而不是其 [Property 語句](../statements/property-statement.md)，則在下列情況下，嘗試設定屬性值可能會失敗：

- `Set`語句標示為[私](../modifiers/private.md)用，而且呼叫程式碼位於定義屬性的類別或結構之外。

- `Set`語句標示為[受保護](../modifiers/protected.md)，而且呼叫程式碼不在定義屬性的類別或結構中，也不在衍生類別中。

- `Set`語句標示為[Friend](../modifiers/friend.md) ，而且呼叫程式碼不在定義該屬性的相同元件中。

 **錯誤識別碼：** BC31102

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果您有定義該屬性之原始程式碼的控制權，請考慮使用與 `Set` 屬性本身相同的存取層級來宣告程式。

- 如果您沒有定義此屬性之原始程式碼的控制權，或您必須將程式 `Set` 存取層級限制在屬性本身之外，請試著將設定屬性值的語句移至對屬性具有更佳存取權的程式碼區域。

## <a name="see-also"></a>另請參閱

- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
- [如何：宣告混合存取層級的屬性](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
