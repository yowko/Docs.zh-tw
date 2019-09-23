---
title: Protobuf 列舉-適用于 WCF 開發人員的 gRPC
description: 瞭解如何在 Protobuf 中宣告和使用列舉。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184236"
---
# <a name="protobuf-enumerations"></a>Protobuf 列舉

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf 支援列舉類型，如上一節中所示，列舉是用來判斷`oneof`欄位的類型。 您可以定義自己的列舉類型，而 Protobuf 會將它們C#編譯成列舉類型。 由於 Protobuf 可以與不同的C#語言搭配使用，因此列舉的命名慣例與慣例不同。 不過，程式碼產生器非常聰明，而且會將名稱轉換C#成傳統案例。 如果與此功能變數名稱相等的 Pascal 大小寫是以列舉名稱開頭，則會將它移除。

例如，在此 Protobuf 列舉中，欄位的前面`ACCOUNT_STATUS`會加上，這相當於 Pascal 案例列舉名稱：。 `AccountStatus`

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

因此，產生器會建立C#相當於下列程式碼的列舉：

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

Protobuf 列舉定義**必須**有零常數做為其第一個欄位。 如同在C#中，您可以宣告多個具有相同值的欄位，但您必須使用列舉中的`allow_alias`選項明確啟用此選項：

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

您可以在`.proto`檔案的最上層宣告列舉，或在訊息定義中宣告。 嵌套的列舉（如 nested 訊息）將會在產生`.Types`之訊息類別的靜態類別中宣告。

沒有任何方法可將[[Flags]](xref:System.FlagsAttribute)屬性套用至 Protobuf 產生的列舉，Protobuf 也不了解位列舉組合。 請看下列範例：

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region availableIn = 1;
}
```

如果您將`product.AvailableIn`設定`Region.NorthAmerica | Region.SouthAmerica`為，則會將它序列化為`3`整數值。 當用戶端或伺服器嘗試將值還原序列化時，它在的 enum 定義`3`中找不到相符的，而且結果會是。 `Region.None`

在 Protobuf 中處理多個列舉值的最佳方式是使用`repeated`列舉類型的欄位。

>[!div class="step-by-step"]
>[上一頁](protobuf-any-oneof.md)
>[下一頁](protobuf-maps.md)
