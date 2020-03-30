---
title: 記憶體內部資料庫
ms.date: 12/13/2019
description: 瞭解如何使用記憶體中 SQLite 資料庫。
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391204"
---
# <a name="in-memory-databases"></a>記憶體內部資料庫

SQLite 記憶體中資料庫是完全存儲在記憶體中的資料庫，而不是存儲在磁片上。 使用特殊的資料來源檔案名`:memory:`創建記憶體中資料庫。 關閉連接時，將刪除資料庫。 使用`:memory:`時，每個連接將創建其自己的資料庫。

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>可共用記憶體中資料庫

記憶體中資料庫可以通過使用`Mode=Memory`和`Cache=Shared`在連接字串中在多個連接之間共用。 關鍵字`Data Source`用於為記憶體中資料庫指定名稱。 使用相同名稱的連接字串將訪問相同的記憶體內資料庫。 只要資料庫至少保持一個連接保持打開狀態，資料庫就將保持不變。 GitHub 上提供了演示此[示例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)。

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
