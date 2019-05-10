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
ms.openlocfilehash: 163ec17f3ea96744290c54a73054ab132f842127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647666"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
指定可寫入屬性，但無法讀取。  
  
## <a name="remarks"></a>備註  
  
## <a name="rules"></a>規則  
 **宣告內容。** 您只能在模組層級使用 `WriteOnly`。 這表示的宣告內容`WriteOnly`屬性必須是類別、 結構或模組，並不能是原始程式檔、 命名空間或程序。  
  
 您可以宣告為屬性`WriteOnly`，但不是變數。  
  
## <a name="when-to-use-writeonly"></a>何時使用 WriteOnly  
 有時您想要能夠設定的值，但不是會探索什麼是使用的程式碼。 比方說，機密資料，例如社會的註冊碼或密碼，必須要防範未設定任何元件的存取。 在這些情況下，您可以使用`WriteOnly`屬性來設定的值。  
  
> [!IMPORTANT]
>  當您定義並使用`WriteOnly`屬性，請考慮下列的額外保護措施：  
  
- **覆寫。** 如果屬性是類別的成員，讓它預設為[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)，並不會將宣告`Overridable`或`MustOverride`。 這可防止衍生的類別進行覆寫透過不良的存取。  
  
- **存取層級。** 如果您在兩個變數中有一或多個保留屬性的機密資料，請宣告這些[私人](../../../visual-basic/language-reference/modifiers/private.md)，讓其他的程式碼可以存取它們。  
  
- **加密。** 儲存所有的機密資料，以加密形式中，而不是以純文字。 如果惡意程式碼以某種方式取得對該區域的記憶體存取，就更難進行資料的使用。 也很有用，如果必須序列化的敏感性資料加密。  
  
- **正在重設。** 正在終止類別、 結構或模組定義該屬性時，重設的敏感性資料，預設值或其他無意義的值。 釋放該記憶體區域的一般存取時，這會提供額外的保護。  
  
- **持續性。** 不會保存任何敏感性資料，例如在磁碟上，如果您可以避免它。 此外，不寫入任何機密資料到剪貼簿。  
  
 `WriteOnly`修飾詞，請使用此內容中：  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
