---
title: 原托布夫保留字段 - gRPC 面向 WCF 開發人員
description: 瞭解跨版本相容性的保留字段。
ms.date: 09/09/2019
ms.openlocfilehash: f89513c4659a02cbc94e1c659baecb9e750acbdc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111032"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="74a31-103">Protobuf 保留欄位</span><span class="sxs-lookup"><span data-stu-id="74a31-103">Protobuf reserved fields</span></span>

<span data-ttu-id="74a31-104">協定緩衝區 （Protobuf） 中的向後相容性保證依賴于始終表示相同資料項目的欄位編號。</span><span class="sxs-lookup"><span data-stu-id="74a31-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="74a31-105">如果從服務新版本中的消息中刪除了欄位，則不應重複使用該欄位編號。</span><span class="sxs-lookup"><span data-stu-id="74a31-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="74a31-106">您可以使用`reserved`關鍵字強制執行此情況。</span><span class="sxs-lookup"><span data-stu-id="74a31-106">You can enforce this by using the `reserved` keyword.</span></span>

<span data-ttu-id="74a31-107">如果`displayName`從`marketId`前面定義`Stock`的消息中刪除 和 欄位，則應保留其欄位編號，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="74a31-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="74a31-108">您還可以將`reserved`關鍵字用作將來可能添加的欄位的預留位置。</span><span class="sxs-lookup"><span data-stu-id="74a31-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="74a31-109">您可以使用`to`關鍵字將連續欄位數表示為範圍。</span><span class="sxs-lookup"><span data-stu-id="74a31-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="74a31-110">[上一個](protobuf-repeated.md)
>[下一個](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="74a31-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
