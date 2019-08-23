---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 43507ac8e9b5843e8fa9496737a3d77b3a425a7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963775"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
指定可寫入但無法讀取的屬性。  
  
## <a name="remarks"></a>備註  
  
## <a name="rules"></a>規則  
 **宣告內容。** 您只能在模組層級使用 `WriteOnly`。 這表示`WriteOnly`屬性的宣告內容必須是類別、結構或模組, 而且不能是原始程式檔、命名空間或程式。  
  
 您可以將屬性宣告為`WriteOnly`, 但不能宣告為變數。  
  
## <a name="when-to-use-writeonly"></a>使用 WriteOnly 的時機  
 有時候您會想要讓使用中的程式碼能夠設定值, 但不會探索其意義。 例如, 需要保護機密資料 (例如社交註冊號碼或密碼), 使其無法存取未設定它的任何元件。 在這些情況下, 您可以使用`WriteOnly`屬性來設定值。  
  
> [!IMPORTANT]
> 當您定義並使用`WriteOnly`屬性時, 請考慮下列其他保護措施:  
  
- **覆寫.** 如果屬性是類別的成員, 則允許它預設為[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), 而且不會將它`Overridable`宣告為或。 `MustOverride` 這可防止衍生類別透過覆寫進行不想要的存取。  
  
- **存取層級。** 如果您將屬性的機密資料保存在一或多個變數中, 請將其宣告為[私](../../../visual-basic/language-reference/modifiers/private.md)用, 讓其他程式碼都不能存取它們。  
  
- **加密.** 以加密格式儲存所有機密資料, 而不是純文字。 如果惡意程式碼以某種方式取得該記憶體區域的存取權, 就比較難以利用資料。 如果需要將敏感性資料序列化, 加密也很有用。  
  
- **重設.** 當定義屬性的類別、結構或模組被終止時, 會將敏感性資料重設為預設值或其他無意義的值。 當釋放該記憶體區域以供一般存取時, 這會提供額外的保護。  
  
- **暫.** 請勿保存任何機密資料 (例如, 在磁片上), 如果您可以避免它。 此外, 請勿將任何敏感性資料寫入剪貼簿。  
  
 `WriteOnly`修飾詞可以在此內容中使用:  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
