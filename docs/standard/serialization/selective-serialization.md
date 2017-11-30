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
# <a name="selective-serialization"></a><span data-ttu-id="8ed6f-102">選擇式序列化</span><span class="sxs-lookup"><span data-stu-id="8ed6f-102">Selective serialization</span></span>
<span data-ttu-id="8ed6f-103">類別經常包含不應序列化的欄位。</span><span class="sxs-lookup"><span data-stu-id="8ed6f-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="8ed6f-104">例如，假設類別在成員變數中儲存執行緖 ID。</span><span class="sxs-lookup"><span data-stu-id="8ed6f-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="8ed6f-105">當類別還原序列化時，類別在序列化時儲存識別碼的執行緒可能已不再執行，因此序列化此值就沒有意義。</span><span class="sxs-lookup"><span data-stu-id="8ed6f-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="8ed6f-106">您可以使用 [NonSerialized](xref:System.NonSerializedAttribute) 屬性標示成員變數，避免成員變數遭到序列化，如下所示。</span><span class="sxs-lookup"><span data-stu-id="8ed6f-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="8ed6f-107">如果可能的話，讓可能含有安全性顧慮資料的物件不可序列化。</span><span class="sxs-lookup"><span data-stu-id="8ed6f-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="8ed6f-108">如果必須序列化物件，請將 `NonSerialized` 屬性套用至儲存敏感性資料的特定欄位。</span><span class="sxs-lookup"><span data-stu-id="8ed6f-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="8ed6f-109">如果您未將這些欄位排除在序列化範圍外，請留意它們所儲存的資料可能會公開給擁有序列化權限的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="8ed6f-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="8ed6f-110">如需撰寫安全序列化程式碼的詳細資訊，請參閱[安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="8ed6f-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="8ed6f-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ed6f-111">See also</span></span>  
 [<span data-ttu-id="8ed6f-112">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="8ed6f-112">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="8ed6f-113">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="8ed6f-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
 [<span data-ttu-id="8ed6f-114">安全性和序列化</span><span class="sxs-lookup"><span data-stu-id="8ed6f-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)