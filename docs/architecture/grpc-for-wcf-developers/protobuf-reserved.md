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
# <a name="protobuf-reserved-fields"></a>Protobuf 保留欄位

Protobuf 的回溯相容性保證會依賴欄位編號，一律代表相同的資料項目。 如果從新的服務版本中的訊息移除欄位，則永遠不應重複使用該欄位編號。 您可以使用 `reserved` 關鍵字來強制執行此工作。 如果 [`displayName`] 和 [`marketId`] 欄位已從先前定義的 `Stock` 訊息中移除，則應保留其欄位號碼，如下列範例所示。

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved` 關鍵字也可以做為未來可能加入之欄位的預留位置。 連續的欄位數位可以使用 `to` 關鍵字來表示為範圍。

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[上一頁](protobuf-repeated.md)
>[下一頁](protobuf-any-oneof.md)
