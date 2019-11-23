---
title: Protobuf 保留的欄位-WCF 開發人員的 gRPC
description: 瞭解跨版本相容性的保留字段。
ms.date: 09/09/2019
ms.openlocfilehash: e589cd38a712ce014fa2c4d847fbde359d538dd0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967305"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="fbf2e-103">Protobuf 保留欄位</span><span class="sxs-lookup"><span data-stu-id="fbf2e-103">Protobuf reserved fields</span></span>

<span data-ttu-id="fbf2e-104">Protobuf 的回溯相容性保證會依賴欄位編號，一律代表相同的資料項目。</span><span class="sxs-lookup"><span data-stu-id="fbf2e-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="fbf2e-105">如果從新的服務版本中的訊息移除欄位，則永遠不應重複使用該欄位編號。</span><span class="sxs-lookup"><span data-stu-id="fbf2e-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="fbf2e-106">您可以使用 `reserved` 關鍵字來強制執行此工作。</span><span class="sxs-lookup"><span data-stu-id="fbf2e-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="fbf2e-107">如果 [`displayName`] 和 [`marketId`] 欄位已從先前定義的 `Stock` 訊息中移除，則應保留其欄位號碼，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fbf2e-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="fbf2e-108">`reserved` 關鍵字也可以做為未來可能加入之欄位的預留位置。</span><span class="sxs-lookup"><span data-stu-id="fbf2e-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="fbf2e-109">連續的欄位數位可以使用 `to` 關鍵字來表示為範圍。</span><span class="sxs-lookup"><span data-stu-id="fbf2e-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="fbf2e-110">[上一頁](protobuf-repeated.md)
>[下一頁](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="fbf2e-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
