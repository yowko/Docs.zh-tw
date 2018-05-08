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
ms.openlocfilehash: 4f34f7f4ada3f8d61c9d855eab1b8b073a3d5ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
指定可寫入屬性，但無法讀取。  
  
## <a name="remarks"></a>備註  
  
## <a name="rules"></a>規則  
 **宣告內容。** 您只能在模組層級使用 `WriteOnly`。 這表示宣告內容`WriteOnly`屬性必須是類別、 結構或模組，而且不能是原始程式檔、 命名空間或程序。  
  
 您可以宣告為屬性`WriteOnly`，但不是變數。  
  
## <a name="when-to-use-writeonly"></a>何時使用 WriteOnly  
 有時候您會想使用的程式碼，可以設定的值，但不是會發現它是什麼。 例如，敏感性資料，例如社交的註冊號碼或密碼，需要存取從受未設定任何元件。 在這些情況下，您可以使用`WriteOnly`屬性設定的值。  
  
> [!IMPORTANT]
>  當您定義和使用`WriteOnly`屬性，請考慮下列額外的保護措施：  
  
-   **覆寫。** 如果屬性是類別的成員，讓它預設為[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)，並不會宣告`Overridable`或`MustOverride`。 這可防止在衍生的類別進行覆寫透過不良的存取。  
  
-   **存取層級。** 如果您屬性的機密資料保留在一個或多個變數，將其宣告[私人](../../../visual-basic/language-reference/modifiers/private.md)，讓其他程式碼可以存取它們。  
  
-   **加密。** 儲存所有的機密資料，以加密形式，而不是以純文字。 如果惡意程式碼以某種方式取得存取權的記憶體該區域，就更難以將使用的資料。 加密也很有用，如果需要序列化的機密資料。  
  
-   **重設。** 正在終止類別、 結構或模組定義該屬性時，重設的敏感性資料，預設值或其他無意義的值。 該區域的記憶體已釋放的一般存取時，這會提供額外的保護。  
  
-   **持續性。** 不會保存任何敏感性資料，例如在磁碟上，如果可以避免。 此外，不寫入任何機密資料到剪貼簿。  
  
 `WriteOnly`修飾詞可用於此內容：  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
