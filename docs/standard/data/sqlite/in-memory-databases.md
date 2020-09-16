---
title: 記憶體內部資料庫
ms.date: 12/13/2019
description: 瞭解如何使用記憶體中的 SQLite 資料庫。
ms.openlocfilehash: fbda5787d95a9ce462752b985f847af0b0551fa6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555363"
---
# <a name="in-memory-databases"></a>記憶體內部資料庫

SQLite 記憶體內部資料庫是完全儲存在記憶體中的資料庫，而不是儲存在磁片上。 使用特殊的資料來源檔案名 `:memory:` 來建立記憶體中的資料庫。 當連接關閉時，就會刪除資料庫。 使用時 `:memory:` ，每個連接都會建立自己的資料庫。

```connectionstring
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>可共用的記憶體內部資料庫

在連接字串中使用和，可以在多個連接之間共用記憶體內部資料庫 `Mode=Memory` `Cache=Shared` 。 `Data Source`關鍵字是用來提供記憶體中資料庫的名稱。 使用相同名稱的連接字串將會存取相同的記憶體內資料庫。 只要至少有一個連接維持開啟狀態，資料庫就會持續存在。 您可以在 GitHub 上取得示範這項功能的 [範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) 。

```connectionstring
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
