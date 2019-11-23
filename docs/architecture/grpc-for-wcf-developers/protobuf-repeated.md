---
title: 清單和陣列的重複欄位-適用于 WCF 開發人員的 gRPC
description: 瞭解集合如何由 Protobuf 處理，以及它們如何與 .NET 集合產生關聯。
ms.date: 09/09/2019
ms.openlocfilehash: 17c579bc98ba62ea74b9452bdb28efd96fc51406
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967371"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>清單和陣列的重複欄位

清單是使用 `repeated` prefix 關鍵字，在 Protobuf 中指定。 下列範例顯示如何建立清單：

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

在產生的程式碼中，`repeated` 欄位是以 `Google.Protobuf.Collections.RepeatedField<T>` 泛型型別來表示，而不是任何內建的 .NET 集合類型。 `RepeatedField<T>` 類型包含將清單序列化和還原序列化為二進位電傳格式所需的程式碼。 它會實作為所有標準的 .NET 集合介面，例如 <xref:System.Collections.Generic.IList%601> 和 <xref:System.Collections.Generic.IEnumerable%601>，讓您可以使用 LINQ 查詢，或輕鬆地將它轉換成陣列或清單。

>[!div class="step-by-step"]
>[上一頁](protobuf-nested-types.md)
>[下一頁](protobuf-reserved.md)
