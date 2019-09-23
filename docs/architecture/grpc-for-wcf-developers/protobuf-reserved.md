---
title: Protobuf 保留的欄位-WCF 開發人員的 gRPC
description: 瞭解跨版本相容性的保留字段。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d4d40ca12d41ec37e0baebf10de9d0690e4297cc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184173"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="e6c91-103">Protobuf 保留字段</span><span class="sxs-lookup"><span data-stu-id="e6c91-103">Protobuf reserved fields</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e6c91-104">Protobuf 的回溯相容性保證會依賴欄位編號，一律代表相同的資料項目。</span><span class="sxs-lookup"><span data-stu-id="e6c91-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="e6c91-105">如果從新的服務版本中的訊息移除欄位，則永遠不應重複使用該欄位編號。</span><span class="sxs-lookup"><span data-stu-id="e6c91-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="e6c91-106">這可以使用`reserved`關鍵字來強制執行。</span><span class="sxs-lookup"><span data-stu-id="e6c91-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="e6c91-107">`displayName`如果和`marketId`欄位已從稍早定義`Stock`的訊息中移除，則其欄位號碼應保留，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e6c91-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="e6c91-108">`reserved`關鍵字也可以做為未來可能加入之欄位的預留位置。</span><span class="sxs-lookup"><span data-stu-id="e6c91-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="e6c91-109">連續的`to`欄位編號可以使用關鍵字來表示為範圍。</span><span class="sxs-lookup"><span data-stu-id="e6c91-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="e6c91-110">[上一頁](protobuf-repeated.md)
>[下一頁](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="e6c91-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
