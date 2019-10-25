---
title: 適用于字典的 Protobuf 對應-針對 WCF 開發人員的 gRPC
description: 瞭解如何使用 Protobuf 對應來表示。NET 的字典類型。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: aef6b0f378e7a63f362ec42642cae15b32d49a08
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846329"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="70a3c-103">適用於字典的 Protobuf 對應</span><span class="sxs-lookup"><span data-stu-id="70a3c-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="70a3c-104">務必要能夠在訊息中表示任何已命名的值集合。</span><span class="sxs-lookup"><span data-stu-id="70a3c-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="70a3c-105">在 .NET 中，這通常是使用字典類型來處理。</span><span class="sxs-lookup"><span data-stu-id="70a3c-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="70a3c-106">Protobuf 對等的 .NET <xref:System.Collections.Generic.IDictionary%602> 類型是 `map<key_type, value_type>` 類型。</span><span class="sxs-lookup"><span data-stu-id="70a3c-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="70a3c-107">本節說明如何在 Protobuf 中宣告 `map`，以及如何使用產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="70a3c-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="70a3c-108">在產生的程式碼中，`map` 欄位會使用 `Google.Protobuf.Collections.MapField<TKey, TValue>` 類別，它會實作為標準 .NET 集合介面，包括 <xref:System.Collections.Generic.IDictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="70a3c-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="70a3c-109">在訊息定義中無法直接重複對應欄位，但是您可以建立包含對應的嵌套訊息，並在訊息類型上使用 `repeated`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="70a3c-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="70a3c-110">在程式碼中使用 MapField 屬性</span><span class="sxs-lookup"><span data-stu-id="70a3c-110">Using MapField properties in code</span></span>

<span data-ttu-id="70a3c-111">從 `map` 欄位產生的 `MapField` 屬性是唯讀的，而且永遠不會 `null`。</span><span class="sxs-lookup"><span data-stu-id="70a3c-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="70a3c-112">若要設定對應屬性，請使用空白 `MapField` 屬性上的 `Add(IDictionary<TKey,TValue> values)` 方法，從任何 .NET 字典中複製值。</span><span class="sxs-lookup"><span data-stu-id="70a3c-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="70a3c-113">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="70a3c-113">Further reading</span></span>

<span data-ttu-id="70a3c-114">如需 Protobuf 的詳細資訊，請參閱官方[Protobuf 檔](https://developers.google.com/protocol-buffers/docs/overview)。</span><span class="sxs-lookup"><span data-stu-id="70a3c-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="70a3c-115">[上一頁](protobuf-enums.md)
>[下一頁](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="70a3c-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
