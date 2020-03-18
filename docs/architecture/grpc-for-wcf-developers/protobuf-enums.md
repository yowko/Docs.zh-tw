---
title: 原數枚 - gRPC 面向 WCF 開發人員
description: 瞭解如何在 Protobuf 中聲明和使用枚舉。
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148071"
---
# <a name="protobuf-enumerations"></a>Protobuf 列舉

Protobuf 支援枚舉類型。 您在上一節中看到了此支援，其中使用枚舉來確定`Oneof`欄位的類型。 您可以定義自己的枚舉類型，Protobuf 將將它們編譯為 C# 枚舉類型。

由於您可以將 Protobuf 用於各種語言，因此枚舉的命名約定與 C# 約定不同。 但是，代碼產生器將名稱轉換為傳統的 C# 大小寫。 如果欄位名稱的 Pascal 大小寫以枚舉名稱開頭，則將其刪除。

例如，在下面的 Protobuf 枚舉中，欄位用 預綴為`ACCOUNT_STATUS`。 此首碼等效于 Pascal 大小寫枚舉名稱`AccountStatus`。

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

產生器創建等效于以下代碼的 C# 枚舉：

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

Protobuf 枚舉定義*必須*具有零常量作為第一個欄位。 與 C# 中一樣，您可以聲明具有相同值的多個欄位。 但是，您必須使用枚舉中`allow_alias`的選項顯式啟用此選項：

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

您可以在`.proto`檔中的頂層聲明枚舉，也可以嵌套在消息定義中。 嵌套枚舉（類似于嵌套消息）將在生成的消息類中的`.Types`靜態類中聲明。

無法將[[Flags]](xref:System.FlagsAttribute)屬性應用於 Protobuf 生成的枚舉，並且 Protobuf 不理解位級枚舉組合。 查看以下示例：

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

如果設置為`product.AvailableIn``Region.NorthAmerica | Region.SouthAmerica`，則序列化為整數值`3`。 當用戶端或伺服器嘗試取消序列化該值時，它不會在 的`3`枚舉定義中找到匹配項。 結果將為`Region.None`。

在 Protobuf 中使用多個枚舉值的最佳方法是使用枚舉類型的`repeated`欄位。

>[!div class="step-by-step"]
>[上一個](protobuf-any-oneof.md)
>[下一個](protobuf-maps.md)
