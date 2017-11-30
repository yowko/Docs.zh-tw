---
title: "選擇式序列化"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f583c0c7f2895b16ac0aea883dd98b4768179127
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="selective-serialization"></a>選擇式序列化
類別經常包含不應序列化的欄位。 例如，假設類別在成員變數中儲存執行緖 ID。 當類別還原序列化時，類別在序列化時儲存識別碼的執行緒可能已不再執行，因此序列化此值就沒有意義。 您可以使用 [NonSerialized](xref:System.NonSerializedAttribute) 屬性標示成員變數，避免成員變數遭到序列化，如下所示。  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

如果可能的話，讓可能含有安全性顧慮資料的物件不可序列化。 如果必須序列化物件，請將 `NonSerialized` 屬性套用至儲存敏感性資料的特定欄位。 如果您未將這些欄位排除在序列化範圍外，請留意它們所儲存的資料可能會公開給擁有序列化權限的所有程式碼。 如需撰寫安全序列化程式碼的詳細資訊，請參閱[安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)。

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>請參閱  
 [二進位序列化](binary-serialization.md)  
 [XML 和 SOAP 序列化](xml-and-soap-serialization.md)  
 [安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)