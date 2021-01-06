---
title: Protobuf 保留的欄位-WCF 開發人員的 gRPC
description: 瞭解跨版本相容性的保留字段。
ms.date: 12/15/2020
ms.openlocfilehash: d82043d619c5b3b81091ae4ea381e4778c1cf6ba
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938516"
---
# <a name="protobuf-reserved-fields"></a>Protobuf 保留欄位

通訊協定緩衝區中的回溯相容性保證 (Protobuf) 依賴欄位號碼永遠代表相同的資料項目。 如果從新的服務版本的訊息中移除欄位，則永遠不應重複使用該欄位編號。 您可以使用關鍵字來強制執行此行為 `reserved` 。

如果 `displayName` 和 `marketId` 欄位已從稍早定義的訊息中移除 `Stock` ，則應該保留其欄位編號，如下列範例所示。

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

您也可以使用 `reserved` 關鍵字做為未來可能加入之欄位的預留位置。 您可以使用關鍵字將連續的欄位編號表示為範圍 `to` 。

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[上一個](protobuf-repeated.md) 
>[下一步](protobuf-any-oneof.md)
