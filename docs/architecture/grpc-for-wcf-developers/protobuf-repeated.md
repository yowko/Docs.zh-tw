---
title: 清單和陣列的重複欄位-適用于 WCF 開發人員的 gRPC
description: 瞭解 Protobuf 如何處理集合，以及它們與 .NET 集合之間的關聯性。
ms.date: 09/09/2019
ms.openlocfilehash: 7320c76ddc58bcf5cd81150923e8cb635e510047
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867499"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>清單和陣列的重複欄位

您可以使用 prefix 關鍵字 (Protobuf) 指定通訊協定緩衝區中的清單 `repeated` 。 下列範例顯示如何建立清單：

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

在產生的程式碼中， `repeated` 欄位是以類型的唯讀屬性 [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] （而非任何內建的 .net 集合類型）表示。 此類型會執行所有標準的 .NET 集合介面，例如 <xref:System.Collections.Generic.IList%601> 和 <xref:System.Collections.Generic.IEnumerable%601> 。 因此，您可以使用 LINQ 查詢，或輕鬆地將它轉換成陣列或清單。

此 `RepeatedField<T>` 類型包含將清單序列化和還原序列化為二進位電傳格式所需的程式碼。

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
>[上一個](protobuf-nested-types.md) 
>[下一步](protobuf-reserved.md)
