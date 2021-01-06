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
# <a name="protobuf-maps-for-dictionaries"></a>適用於字典的 Protobuf 對應

務必要能夠在訊息中表示任意的命名值集合。 在 .NET 中，這項活動通常會透過字典類型來處理。 <xref:System.Collections.Generic.IDictionary%602>通訊協定緩衝區 () Protobuf 中的 .net 型別等同于 `map<key_type, value_type>` 型別。 本節說明如何 `map` 在 Protobuf 中宣告型別，以及如何使用產生的程式碼。

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

在產生的程式碼中， `map` 欄位是以類型的唯讀屬性表示 [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] 。 此類型會實作為標準的 .NET 集合介面，包括 <xref:System.Collections.Generic.IDictionary%602> 。

在訊息定義中無法直接重複對應欄位。 但是，您可以建立包含對應的嵌套訊息，然後 `repeated` 在訊息類型上使用，如下列範例所示：

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>在程式碼中使用 MapField 屬性

`MapField`從欄位產生的 `map` 屬性是唯讀的，而且永遠不會是 `null` 。 若要設定 map 屬性，請 `Add(IDictionary<TKey,TValue> values)` 在 empty 屬性上使用方法 `MapField` 來複製任何 .net 字典的值。

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>進階閱讀

如需 Protobuf 的詳細資訊，請參閱官方 [Protobuf 檔](https://developers.google.com/protocol-buffers/docs/overview)。

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
>[上一個](protobuf-enums.md) 
>[下一步](wcf-services-to-grpc-comparison.md)
