---
title: Protobuf 保留的欄位-WCF 開發人員的 gRPC
description: 瞭解跨版本相容性的保留字段。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 34697371299bdc5d9a58c0696c1ce7d19816ca87
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846322"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="a8c5b-103">Protobuf 保留欄位</span><span class="sxs-lookup"><span data-stu-id="a8c5b-103">Protobuf reserved fields</span></span>

<span data-ttu-id="a8c5b-104">Protobuf 的回溯相容性保證會依賴欄位編號，一律代表相同的資料項目。</span><span class="sxs-lookup"><span data-stu-id="a8c5b-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="a8c5b-105">如果從新的服務版本中的訊息移除欄位，則永遠不應重複使用該欄位編號。</span><span class="sxs-lookup"><span data-stu-id="a8c5b-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="a8c5b-106">您可以使用 `reserved` 關鍵字來強制執行此工作。</span><span class="sxs-lookup"><span data-stu-id="a8c5b-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="a8c5b-107">如果 [`displayName`] 和 [`marketId`] 欄位已從先前定義的 `Stock` 訊息中移除，則應保留其欄位號碼，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a8c5b-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="a8c5b-108">`reserved` 關鍵字也可以做為未來可能加入之欄位的預留位置。</span><span class="sxs-lookup"><span data-stu-id="a8c5b-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="a8c5b-109">連續的欄位數位可以使用 `to` 關鍵字來表示為範圍。</span><span class="sxs-lookup"><span data-stu-id="a8c5b-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="a8c5b-110">[上一頁](protobuf-repeated.md)
>[下一頁](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="a8c5b-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
