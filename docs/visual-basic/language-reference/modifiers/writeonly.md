---
title: WriteOnly
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
ms.openlocfilehash: 12a1030a423359a3e4122eea98e223a1a02f680c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867614"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)

指定可寫入但無法讀取的屬性。  
  
## <a name="remarks"></a>備註  
  
## <a name="rules"></a>規則  

 **宣告內容。** 您只能在模組層級使用 `WriteOnly`。 這表示屬性的宣告內容 `WriteOnly` 必須是類別、結構或模組，且不能是原始程式檔、命名空間或程式。  
  
 您可以將屬性宣告為 `WriteOnly` ，而不是變數。  
  
## <a name="when-to-use-writeonly"></a>使用 WriteOnly 的時機  

 有時候您會想要使用程式碼來設定值，但不能找出它的值。 例如，機密資料（例如社交註冊號碼或密碼）必須受到保護，使其無法存取未設定它的任何元件。 在這些情況下，您可以使用 `WriteOnly` 屬性來設定值。  
  
> [!IMPORTANT]
> 當您定義並使用 `WriteOnly` 屬性時，請考慮下列額外的保護措施：  
  
- **重寫。** 如果屬性是類別的成員，則可讓它預設為 [NotOverridable](notoverridable.md)，而且不會將它宣告為 `Overridable` 或 `MustOverride` 。 這可防止衍生類別透過覆寫進行不想要的存取。  
  
- **存取層級。** 如果您將屬性的機密資料保存在一或多個變數中，請將其宣告為 [私](private.md) 用，讓其他程式碼無法存取它們。  
  
- **加密。** 以加密形式儲存所有機密資料，而不是以純文字格式儲存。 如果惡意程式碼會以某種方式取得該記憶體區域的存取權，就會更難利用資料。 如果必須序列化機密資料，加密也會很有用。  
  
- **重 置。** 當定義屬性的類別、結構或模組結束時，請將機密資料重設為預設值或其他無意義的值。 當釋放該記憶體區域以進行一般存取時，這會提供額外的保護。  
  
- **堅持。** 請勿保存任何機密資料（例如，在磁片上，如果您可以避免的話）。 此外，請勿將任何敏感性資料寫入剪貼簿。  
  
 `WriteOnly`修飾詞可用於此內容中：  
  
 [Property Statement](../statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [ReadOnly](readonly.md)
- [私人](private.md)
- [關鍵字](../keywords/index.md)
