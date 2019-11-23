---
title: Protobuf 的巢狀型別-WCF 開發人員的 gRPC
description: 瞭解 Protobuf 和 gRPC 中的嵌套訊息類型，以及它們在中的C#產生方式。
ms.date: 09/09/2019
ms.openlocfilehash: bbc7ed41516d29f867bbc9da5b258f6a3c9ff261
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967391"
---
# <a name="protobuf-nested-types"></a>Protobuf 巢狀型別

就像C#可讓您在其他類別中宣告類別，Protobuf 可讓您在其他訊息中嵌套訊息定義。 下列範例顯示如何建立嵌套訊息類型：

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

在產生C#的程式碼中，`Inner` 類型將會在 `HelloRequest` 類別內的嵌套靜態 `Types` 類別中宣告：

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[上一頁](protobuf-data-types.md)
>[下一頁](protobuf-repeated.md)
