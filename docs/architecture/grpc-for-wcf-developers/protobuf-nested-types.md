---
title: Protobuf 的巢狀型別-WCF 開發人員的 gRPC
description: 瞭解 Protobuf 和 gRPC 中的嵌套訊息類型，以及它們在中的C#產生方式。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 39bc52b37cc9e57cfe0ed5a5118c348de5f014d8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184187"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="17223-103">Protobuf 的巢狀型別</span><span class="sxs-lookup"><span data-stu-id="17223-103">Protobuf nested types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="17223-104">就像C#可讓您在其他類別中宣告類別，Protobuf 可讓您在其他訊息中嵌套訊息定義。</span><span class="sxs-lookup"><span data-stu-id="17223-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="17223-105">下列範例顯示如何建立嵌套訊息類型：</span><span class="sxs-lookup"><span data-stu-id="17223-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="17223-106">在產生C#的程式碼中`Inner` ，類型會在`HelloRequest`類別內的嵌套`Types`靜態類別中宣告：</span><span class="sxs-lookup"><span data-stu-id="17223-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="17223-107">[上一頁](protobuf-data-types.md)
>[下一頁](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="17223-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
