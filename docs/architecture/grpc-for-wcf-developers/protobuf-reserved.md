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
# <a name="protobuf-reserved-fields"></a>Protobuf 保留字段

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf 的回溯相容性保證會依賴欄位編號，一律代表相同的資料項目。 如果從新的服務版本中的訊息移除欄位，則永遠不應重複使用該欄位編號。 這可以使用`reserved`關鍵字來強制執行。 `displayName`如果和`marketId`欄位已從稍早定義`Stock`的訊息中移除，則其欄位號碼應保留，如下列範例所示。

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved`關鍵字也可以做為未來可能加入之欄位的預留位置。 連續的`to`欄位編號可以使用關鍵字來表示為範圍。

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
