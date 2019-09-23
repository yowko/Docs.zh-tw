---
title: 適用于字典的 Protobuf 對應-針對 WCF 開發人員的 gRPC
description: 瞭解如何使用 Protobuf 對應來表示。NET 的字典類型。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6a71fb7940145571a94eaf5c8bae9dfc91a30db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184208"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="8510d-103">適用于字典的 Protobuf 對應</span><span class="sxs-lookup"><span data-stu-id="8510d-103">Protobuf maps for dictionaries</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="8510d-104">務必要能夠在訊息中表示任何已命名的值集合。</span><span class="sxs-lookup"><span data-stu-id="8510d-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="8510d-105">在 .NET 中，這通常是使用字典類型來處理。</span><span class="sxs-lookup"><span data-stu-id="8510d-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="8510d-106">Protobuf 對等的 .net <xref:System.Collections.Generic.IDictionary%602>類型`map<key_type, value_type>`是型別。</span><span class="sxs-lookup"><span data-stu-id="8510d-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="8510d-107">本節說明如何`map`在 Protobuf 中宣告，以及如何使用產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8510d-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="8510d-108">在產生的程式碼`map`中，欄位`Google.Protobuf.Collections.MapField<TKey, TValue>`會使用可實作為標準 .net 集合介面的類別<xref:System.Collections.Generic.IDictionary%602>，包括。</span><span class="sxs-lookup"><span data-stu-id="8510d-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="8510d-109">在訊息定義中無法直接重複對應欄位，但是您可以建立包含對應的嵌套訊息，並在訊息`repeated`類型上使用，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8510d-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="8510d-110">在程式碼中使用 MapField 屬性</span><span class="sxs-lookup"><span data-stu-id="8510d-110">Using MapField properties in code</span></span>

<span data-ttu-id="8510d-111">`null`從`MapField` 欄位產生的屬性是唯讀的，而且永遠不會是。`map`</span><span class="sxs-lookup"><span data-stu-id="8510d-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="8510d-112">若要設定對應屬性，請使用`Add(IDictionary<TKey,TValue> values)`空白`MapField`屬性上的方法，從任何 .net 字典複製值。</span><span class="sxs-lookup"><span data-stu-id="8510d-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="8510d-113">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="8510d-113">Further reading</span></span>

<span data-ttu-id="8510d-114">如需 Protobuf 的詳細資訊，請參閱官方[Protobuf 檔](https://developers.google.com/protocol-buffers/docs/overview)。</span><span class="sxs-lookup"><span data-stu-id="8510d-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8510d-115">[上一頁](protobuf-enums.md)
>[下一頁](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="8510d-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
