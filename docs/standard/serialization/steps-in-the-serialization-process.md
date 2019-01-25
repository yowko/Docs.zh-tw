---
title: 序列化程序中的步驟
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: b697e8c590d0865b26eaa9f66a333504a5faece2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517353"
---
# <a name="steps-in-the-serialization-process"></a>序列化程序中的步驟
在[格式子](xref:System.Runtime.Serialization.Formatter)上呼叫 <xref:System.Runtime.Serialization.Formatter.Serialize*> 方法時，物件序列化會遵循下列規則順序繼續進行：

- 進行檢查以判斷格式子是否有代理選取器。 若格式子有代理選取器，檢查代理選取器是否處理指定型別的物件。 若選取器可處理物件類型，會對代理選取器呼叫 <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType>。

- 若無代理選取器，或它不處理物件類型，則檢查以判斷物件是否以 [Serializable](xref:System.SerializableAttribute) 屬性標記。 如果物件不是，就會擲回 <xref:System.Runtime.Serialization.SerializationException>。

- 若物件有適當地標記，檢查物件是否實作 <xref:System.Runtime.Serialization.ISerializable> 介面。 若物件實作，會對物件呼叫 <xref:System.Runtime.Serialization.ISerializable.GetObjectData*>。
  
- 若物件未實作 <xref:System.Runtime.Serialization.ISerializable>，且使用預設序列化原則，則會序列化所有未標記為 [NonSerialized](xref:System.NonSerializedAttribute) 的欄位。

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>另請參閱

- [二進位序列化](binary-serialization.md)
- [XML 和 SOAP 序列化](xml-and-soap-serialization.md)
