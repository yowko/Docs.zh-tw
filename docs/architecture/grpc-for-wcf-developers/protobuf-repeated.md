---
title: 清單和陣列的重複欄位 - 適用于 WCF 開發人員的 gRPC
description: 瞭解 Protobuf 如何處理集合以及它們與 .NET 集合的關係。
ms.date: 09/09/2019
ms.openlocfilehash: 63d99532d14deea7800673dd5a6350dd9362ad54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147967"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>清單和陣列的重複欄位

通過使用`repeated`首碼關鍵字在協定緩衝區（Protobuf）中指定清單。 下面的示例演示如何創建清單：

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

在生成的代碼中，`repeated`欄位由泛型型別`Google.Protobuf.Collections.RepeatedField<T>`表示，而不是任何內置 .NET 集合類型。

該`RepeatedField<T>`類型包括將清單序列化並將序列化為二進位導線格式所需的代碼。 它實現所有標準 .NET 集合介面，如<xref:System.Collections.Generic.IList%601><xref:System.Collections.Generic.IEnumerable%601>和 。 因此，您可以使用 LINQ 查詢或輕鬆將其轉換為數組或清單。

>[!div class="step-by-step"]
>[上一個](protobuf-nested-types.md)
>[下一個](protobuf-reserved.md)
