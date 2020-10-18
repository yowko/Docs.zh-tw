---
title: 無法存取屬性 '<propertyname>' 的 'Get' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: bd6830e16ba3d1f76c61519b4456832a2efec716
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162904"
---
# <a name="bc31103-get-accessor-of-property-propertyname-is-not-accessible"></a>BC31103：無法存取屬性 ' ' 的 ' Get ' 存取子 \<propertyname>

當語句無法存取屬性的程式時，它會嘗試取得屬性的值 `Get` 。

 如果 [Get 語句](../statements/get-statement.md) 標示了更嚴格的存取層級，而不是其 [Property 語句](../statements/property-statement.md)，則在下列情況下，嘗試讀取屬性值可能會失敗：

- `Get`語句標示為[私](../modifiers/private.md)用，而且呼叫程式碼位於定義屬性的類別或結構之外。

- `Get`語句標示為[受保護](../modifiers/protected.md)，而且呼叫程式碼不在定義屬性的類別或結構中，也不在衍生類別中。

- `Get`語句標示為[Friend](../modifiers/friend.md) ，而且呼叫程式碼不在定義該屬性的相同元件中。

 **錯誤識別碼：** BC31103

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果您有定義該屬性之原始程式碼的控制權，請考慮使用與 `Get` 屬性本身相同的存取層級來宣告程式。

- 如果您沒有定義此屬性之原始程式碼的控制權，或您必須將 `Get` 程式存取層級限制在屬性本身之外，請嘗試將讀取屬性值的語句移至對屬性有較佳存取權的程式碼區域。

## <a name="see-also"></a>另請參閱

- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
- [如何：宣告混合存取層級的屬性](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
