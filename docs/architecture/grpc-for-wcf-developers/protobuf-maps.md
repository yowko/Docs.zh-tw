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
# <a name="protobuf-maps-for-dictionaries"></a>適用於字典的 Protobuf 對應

務必要能夠在訊息中表示任何已命名的值集合。 在 .NET 中，這通常是透過字典類型來處理。 在通訊協定緩衝區（Protobuf）中，.NET <xref:System.Collections.Generic.IDictionary%602> 類型的對應項是 `map<key_type, value_type>` 類型。 本節說明如何在 Protobuf 中宣告 `map` 類型，以及如何使用產生的程式碼。

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

在產生的程式碼中，`map` 欄位會使用 `Google.Protobuf.Collections.MapField<TKey, TValue>` 類別。 這個類別會實作為標準 .NET 集合介面，包括 <xref:System.Collections.Generic.IDictionary%602>。

在訊息定義中無法直接重複對應欄位。 但是，您可以建立包含對應的嵌套訊息，並在訊息類型上使用 `repeated`，如下列範例所示：

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>在程式碼中使用 MapField 屬性

從 `map` 欄位產生的 `MapField` 屬性是唯讀的，而且永遠不會 `null`。 若要設定對應屬性，請使用空白 `MapField` 屬性上的 `Add(IDictionary<TKey,TValue> values)` 方法，從任何 .NET 字典中複製值。

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>深入閱讀

如需 Protobuf 的詳細資訊，請參閱官方[Protobuf 檔](https://developers.google.com/protocol-buffers/docs/overview)。

>[!div class="step-by-step"]
>[上一頁](protobuf-enums.md)
>[下一頁](wcf-services-to-grpc-comparison.md)
