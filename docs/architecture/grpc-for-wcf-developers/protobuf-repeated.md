---
title: 清單和陣列的重複欄位-適用于 WCF 開發人員的 gRPC
description: 瞭解 Protobuf 如何處理集合，以及它們如何與 .NET 集合產生關聯。
ms.date: 09/09/2019
ms.openlocfilehash: 16f2b5a54b032f32c8fcb9d572d5284fe589cb01
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542955"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>清單和陣列的重複欄位

您可以使用 `repeated` prefix 關鍵字來指定通訊協定緩衝區（Protobuf）中的清單。 下列範例顯示如何建立清單：

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

在產生的程式碼中，`repeated` 欄位是以 `Google.Protobuf.Collections.RepeatedField<T>` 泛型型別來表示，而不是任何內建的 .NET 集合類型。 

`RepeatedField<T>` 類型包含將清單序列化和還原序列化為二進位電傳格式所需的程式碼。 它會實行所有標準 .NET 集合介面，例如 <xref:System.Collections.Generic.IList%601> 和 <xref:System.Collections.Generic.IEnumerable%601>。 因此，您可以使用 LINQ 查詢，或輕鬆地將它轉換成陣列或清單。

>[!div class="step-by-step"]
>[上一頁](protobuf-nested-types.md)
>[下一頁](protobuf-reserved.md)
