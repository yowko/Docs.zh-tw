---
title: 清單和陣列的重複欄位-適用于 WCF 開發人員的 gRPC
description: 瞭解集合如何由 Protobuf 處理，以及它們如何與 .NET 集合產生關聯。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ad06551bf3eaec795865af227815b78c9601d0db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184180"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>清單和陣列的重複欄位

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

清單是使用`repeated` prefix 關鍵字在 Protobuf 中指定的。 下列範例顯示如何建立清單：

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

在產生的`Google.Protobuf.Collections.RepeatedField<T>`程式碼`repeated`中，欄位是以泛型型別表示，而不是任何內建的 .net 集合類型。 `RepeatedField<T>`類型包含將清單序列化和還原序列化為二進位電傳格式所需的程式碼。 它會執行所有標準的 .net 集合介面（ <xref:System.Collections.Generic.IList%601>例如<xref:System.Collections.Generic.IEnumerable%601>和），因此您可以使用 LINQ 查詢，或輕鬆地將它轉換成陣列或清單。

>[!div class="step-by-step"]
>[上一頁](protobuf-nested-types.md)
>[下一頁](protobuf-reserved.md)
