---
title: 適用于字典的 Protobuf 對應-適用于 WCF 開發人員的 gRPC
description: 瞭解如何使用 Protobuf 對應來代表 .NET 中的字典類型。
ms.date: 12/15/2020
ms.openlocfilehash: d38270d4bc320cf1f758080c18843ed1d716b350
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938542"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="65b8b-103">適用於字典的 Protobuf 對應</span><span class="sxs-lookup"><span data-stu-id="65b8b-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="65b8b-104">務必要能夠在訊息中表示任意的命名值集合。</span><span class="sxs-lookup"><span data-stu-id="65b8b-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="65b8b-105">在 .NET 中，這項活動通常會透過字典類型來處理。</span><span class="sxs-lookup"><span data-stu-id="65b8b-105">In .NET, this activity is commonly handled through dictionary types.</span></span> <span data-ttu-id="65b8b-106"><xref:System.Collections.Generic.IDictionary%602>通訊協定緩衝區 () Protobuf 中的 .net 型別等同于 `map<key_type, value_type>` 型別。</span><span class="sxs-lookup"><span data-stu-id="65b8b-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="65b8b-107">本節說明如何 `map` 在 Protobuf 中宣告型別，以及如何使用產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="65b8b-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="65b8b-108">在產生的程式碼中， `map` 欄位是以類型的唯讀屬性表示 [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] 。</span><span class="sxs-lookup"><span data-stu-id="65b8b-108">In the generated code, `map` fields are represented by read-only properties of the [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] type.</span></span> <span data-ttu-id="65b8b-109">此類型會實作為標準的 .NET 集合介面，包括 <xref:System.Collections.Generic.IDictionary%602> 。</span><span class="sxs-lookup"><span data-stu-id="65b8b-109">This type implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="65b8b-110">在訊息定義中無法直接重複對應欄位。</span><span class="sxs-lookup"><span data-stu-id="65b8b-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="65b8b-111">但是，您可以建立包含對應的嵌套訊息，然後 `repeated` 在訊息類型上使用，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="65b8b-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="65b8b-112">在程式碼中使用 MapField 屬性</span><span class="sxs-lookup"><span data-stu-id="65b8b-112">Using MapField properties in code</span></span>

<span data-ttu-id="65b8b-113">`MapField`從欄位產生的 `map` 屬性是唯讀的，而且永遠不會是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="65b8b-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="65b8b-114">若要設定 map 屬性，請 `Add(IDictionary<TKey,TValue> values)` 在 empty 屬性上使用方法 `MapField` 來複製任何 .net 字典的值。</span><span class="sxs-lookup"><span data-stu-id="65b8b-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="65b8b-115">進階閱讀</span><span class="sxs-lookup"><span data-stu-id="65b8b-115">Further reading</span></span>

<span data-ttu-id="65b8b-116">如需 Protobuf 的詳細資訊，請參閱官方 [Protobuf 檔](https://developers.google.com/protocol-buffers/docs/overview)。</span><span class="sxs-lookup"><span data-stu-id="65b8b-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
><span data-ttu-id="65b8b-117">[上一個](protobuf-enums.md) 
>[下一步](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="65b8b-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
