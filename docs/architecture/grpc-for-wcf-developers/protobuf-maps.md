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
# <a name="protobuf-maps-for-dictionaries"></a>適用于字典的 Protobuf 對應

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

務必要能夠在訊息中表示任何已命名的值集合。 在 .NET 中，這通常是使用字典類型來處理。 Protobuf 對等的 .net <xref:System.Collections.Generic.IDictionary%602>類型`map<key_type, value_type>`是型別。 本節說明如何`map`在 Protobuf 中宣告，以及如何使用產生的程式碼。

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

在產生的程式碼`map`中，欄位`Google.Protobuf.Collections.MapField<TKey, TValue>`會使用可實作為標準 .net 集合介面的類別<xref:System.Collections.Generic.IDictionary%602>，包括。

在訊息定義中無法直接重複對應欄位，但是您可以建立包含對應的嵌套訊息，並在訊息`repeated`類型上使用，如下列範例所示：

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>在程式碼中使用 MapField 屬性

`null`從`MapField` 欄位產生的屬性是唯讀的，而且永遠不會是。`map` 若要設定對應屬性，請使用`Add(IDictionary<TKey,TValue> values)`空白`MapField`屬性上的方法，從任何 .net 字典複製值。

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>進一步閱讀

如需 Protobuf 的詳細資訊，請參閱官方[Protobuf 檔](https://developers.google.com/protocol-buffers/docs/overview)。

>[!div class="step-by-step"]
>[上一頁](protobuf-enums.md)
>[下一頁](wcf-services-to-grpc-comparison.md)
