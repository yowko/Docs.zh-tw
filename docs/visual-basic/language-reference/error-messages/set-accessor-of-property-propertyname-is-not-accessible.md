---
title: 無法存取屬性 '<propertyname>' 的 'Set' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 077533a5b1fe241b61ded9516ad8f450d7dbbf5e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400340"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>無法存取屬性 '\<propertyname>' 的 'Set' 存取子
當語句無法存取屬性的程式時，會嘗試儲存屬性的值 `Set` 。  
  
 如果[Set 語句](../statements/set-statement.md)標示的存取層級比其[屬性語句](../statements/property-statement.md)更嚴格，則在下列情況中，嘗試設定屬性值可能會失敗：  
  
- `Set`語句標示為[私](../modifiers/private.md)用，而呼叫程式碼位於定義屬性的類別或結構外。  
  
- `Set`語句已標示為[受保護](../modifiers/protected.md)，而呼叫程式碼不在定義屬性的類別或結構中，也不在衍生類別中。  
  
- `Set`語句已標記為[Friend](../modifiers/friend.md) ，而呼叫程式碼不在定義該屬性的相同元件中。  
  
 **錯誤識別碼：** BC31102  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果您可以控制定義屬性的原始程式碼，請考慮 `Set` 使用與屬性本身相同的存取層級來宣告程式。  
  
- 如果您無法控制定義屬性的原始程式碼，或您必須限制程式 `Set` 存取層級，而不是屬性本身，請嘗試將設定屬性值的語句，移至具有更佳存取屬性的程式碼區域。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
- [如何：宣告混合存取層級的屬性](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
