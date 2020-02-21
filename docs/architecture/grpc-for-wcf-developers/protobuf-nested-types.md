---
title: Protobuf 的巢狀型別-WCF 開發人員的 gRPC
description: 瞭解 Protobuf 和 gRPC 中的嵌套訊息類型，以及它們在中的C#產生方式。
ms.date: 09/09/2019
ms.openlocfilehash: 7b9a331336ebe1ca7bc75fdd164b7b88ae4f9db2
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542842"
---
# <a name="protobuf-nested-types"></a>Protobuf 巢狀型別

如同可C#讓您在其他類別中宣告類別，通訊協定緩衝區（Protobuf）可讓您在其他訊息中嵌套訊息定義。 下列範例顯示如何建立嵌套訊息類型：

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
