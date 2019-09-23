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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="ae47b-103">清單和陣列的重複欄位</span><span class="sxs-lookup"><span data-stu-id="ae47b-103">Repeated fields for lists and arrays</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ae47b-104">清單是使用`repeated` prefix 關鍵字在 Protobuf 中指定的。</span><span class="sxs-lookup"><span data-stu-id="ae47b-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="ae47b-105">下列範例顯示如何建立清單：</span><span class="sxs-lookup"><span data-stu-id="ae47b-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="ae47b-106">在產生的`Google.Protobuf.Collections.RepeatedField<T>`程式碼`repeated`中，欄位是以泛型型別表示，而不是任何內建的 .net 集合類型。</span><span class="sxs-lookup"><span data-stu-id="ae47b-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="ae47b-107">`RepeatedField<T>`類型包含將清單序列化和還原序列化為二進位電傳格式所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae47b-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="ae47b-108">它會執行所有標準的 .net 集合介面（ <xref:System.Collections.Generic.IList%601>例如<xref:System.Collections.Generic.IEnumerable%601>和），因此您可以使用 LINQ 查詢，或輕鬆地將它轉換成陣列或清單。</span><span class="sxs-lookup"><span data-stu-id="ae47b-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ae47b-109">[上一頁](protobuf-nested-types.md)
>[下一頁](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="ae47b-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
