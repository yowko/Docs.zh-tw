---
title: 無法存取屬性 '<propertyname>' 的 'Get' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: cb953671e624d5b9170aa0b3a9dd80c7ba8337e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402910"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>無法存取屬性 '\<propertyname>' 的 'Get' 存取子
當語句無法存取屬性的程式時，會嘗試抓取屬性的值 `Get` 。  
  
 如果[Get 語句](../statements/get-statement.md)標示的存取層級比它的[Property 語句](../statements/property-statement.md)更嚴格，則嘗試讀取屬性值可能會在下列情況下失敗：  
  
- `Get`語句標示為[私](../modifiers/private.md)用，而呼叫程式碼位於定義屬性的類別或結構外。  
  
- `Get`語句已標示為[受保護](../modifiers/protected.md)，而呼叫程式碼不在定義屬性的類別或結構中，也不在衍生類別中。  
  
- `Get`語句已標記為[Friend](../modifiers/friend.md) ，而呼叫程式碼不在定義該屬性的相同元件中。  
  
 **錯誤識別碼：** BC31103  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果您可以控制定義屬性的原始程式碼，請考慮 `Get` 使用與屬性本身相同的存取層級來宣告程式。  
  
- 如果您無法控制定義屬性的原始程式碼，或是必須限制程式 `Get` 存取層級，而不是屬性本身，請嘗試將讀取屬性值的語句移至可更佳存取屬性的程式碼區域。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
- [如何：宣告混合存取層級的屬性](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
