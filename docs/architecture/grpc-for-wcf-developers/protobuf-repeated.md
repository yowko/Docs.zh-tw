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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="59748-103">清單和陣列的重複欄位</span><span class="sxs-lookup"><span data-stu-id="59748-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="59748-104">您可以使用 `repeated` prefix 關鍵字來指定通訊協定緩衝區（Protobuf）中的清單。</span><span class="sxs-lookup"><span data-stu-id="59748-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="59748-105">下列範例顯示如何建立清單：</span><span class="sxs-lookup"><span data-stu-id="59748-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="59748-106">在產生的程式碼中，`repeated` 欄位是以 `Google.Protobuf.Collections.RepeatedField<T>` 泛型型別來表示，而不是任何內建的 .NET 集合類型。</span><span class="sxs-lookup"><span data-stu-id="59748-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> 

<span data-ttu-id="59748-107">`RepeatedField<T>` 類型包含將清單序列化和還原序列化為二進位電傳格式所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="59748-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="59748-108">它會實行所有標準 .NET 集合介面，例如 <xref:System.Collections.Generic.IList%601> 和 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="59748-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="59748-109">因此，您可以使用 LINQ 查詢，或輕鬆地將它轉換成陣列或清單。</span><span class="sxs-lookup"><span data-stu-id="59748-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="59748-110">[上一頁](protobuf-nested-types.md)
>[下一頁](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="59748-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
