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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="d93e1-103">清單和陣列的重複欄位</span><span class="sxs-lookup"><span data-stu-id="d93e1-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="d93e1-104">通過使用`repeated`首碼關鍵字在協定緩衝區（Protobuf）中指定清單。</span><span class="sxs-lookup"><span data-stu-id="d93e1-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="d93e1-105">下面的示例演示如何創建清單：</span><span class="sxs-lookup"><span data-stu-id="d93e1-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="d93e1-106">在生成的代碼中，`repeated`欄位由泛型型別`Google.Protobuf.Collections.RepeatedField<T>`表示，而不是任何內置 .NET 集合類型。</span><span class="sxs-lookup"><span data-stu-id="d93e1-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span>

<span data-ttu-id="d93e1-107">該`RepeatedField<T>`類型包括將清單序列化並將序列化為二進位導線格式所需的代碼。</span><span class="sxs-lookup"><span data-stu-id="d93e1-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="d93e1-108">它實現所有標準 .NET 集合介面，如<xref:System.Collections.Generic.IList%601><xref:System.Collections.Generic.IEnumerable%601>和 。</span><span class="sxs-lookup"><span data-stu-id="d93e1-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d93e1-109">因此，您可以使用 LINQ 查詢或輕鬆將其轉換為數組或清單。</span><span class="sxs-lookup"><span data-stu-id="d93e1-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d93e1-110">[上一個](protobuf-nested-types.md)
>[下一個](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="d93e1-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
