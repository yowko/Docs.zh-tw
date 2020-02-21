---
title: 適用于字典的 Protobuf 對應-針對 WCF 開發人員的 gRPC
description: 瞭解如何在 .NET 中使用 Protobuf 對應來代表字典類型。
ms.date: 09/09/2019
ms.openlocfilehash: bf848bbc7e3618f6d78e280fcd85d5eb88d5cfae
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543127"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="d2575-103">適用於字典的 Protobuf 對應</span><span class="sxs-lookup"><span data-stu-id="d2575-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="d2575-104">務必要能夠在訊息中表示任何已命名的值集合。</span><span class="sxs-lookup"><span data-stu-id="d2575-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="d2575-105">在 .NET 中，這通常是透過字典類型來處理。</span><span class="sxs-lookup"><span data-stu-id="d2575-105">In .NET, this is commonly handled through dictionary types.</span></span> <span data-ttu-id="d2575-106">在通訊協定緩衝區（Protobuf）中，.NET <xref:System.Collections.Generic.IDictionary%602> 類型的對應項是 `map<key_type, value_type>` 類型。</span><span class="sxs-lookup"><span data-stu-id="d2575-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="d2575-107">本節說明如何在 Protobuf 中宣告 `map` 類型，以及如何使用產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d2575-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="d2575-108">在產生的程式碼中，`map` 欄位會使用 `Google.Protobuf.Collections.MapField<TKey, TValue>` 類別。</span><span class="sxs-lookup"><span data-stu-id="d2575-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class.</span></span> <span data-ttu-id="d2575-109">這個類別會實作為標準 .NET 集合介面，包括 <xref:System.Collections.Generic.IDictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="d2575-109">This class implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="d2575-110">在訊息定義中無法直接重複對應欄位。</span><span class="sxs-lookup"><span data-stu-id="d2575-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="d2575-111">但是，您可以建立包含對應的嵌套訊息，並在訊息類型上使用 `repeated`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d2575-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="d2575-112">在程式碼中使用 MapField 屬性</span><span class="sxs-lookup"><span data-stu-id="d2575-112">Using MapField properties in code</span></span>

<span data-ttu-id="d2575-113">從 `map` 欄位產生的 `MapField` 屬性是唯讀的，而且永遠不會 `null`。</span><span class="sxs-lookup"><span data-stu-id="d2575-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="d2575-114">若要設定對應屬性，請使用空白 `MapField` 屬性上的 `Add(IDictionary<TKey,TValue> values)` 方法，從任何 .NET 字典中複製值。</span><span class="sxs-lookup"><span data-stu-id="d2575-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="d2575-115">深入閱讀</span><span class="sxs-lookup"><span data-stu-id="d2575-115">Further reading</span></span>

<span data-ttu-id="d2575-116">如需 Protobuf 的詳細資訊，請參閱官方[Protobuf 檔](https://developers.google.com/protocol-buffers/docs/overview)。</span><span class="sxs-lookup"><span data-stu-id="d2575-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d2575-117">[上一頁](protobuf-enums.md)
>[下一頁](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="d2575-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
