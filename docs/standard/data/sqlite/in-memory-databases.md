---
title: 記憶體內部資料庫
ms.date: 12/13/2019
description: 瞭解如何使用記憶體內部的 SQLite 資料庫。
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391204"
---
# <a name="in-memory-databases"></a>記憶體內部資料庫

SQLite 記憶體內部資料庫是完全儲存在記憶體中的資料庫，而不是在磁片上。 使用特殊的資料來源檔案名`:memory:`來建立記憶體內部資料庫。 當連接關閉時，就會刪除資料庫。 使用`:memory:`時，每個連接都會建立自己的資料庫。

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>可共用的記憶體內部資料庫

記憶體內部資料庫可以在連接字串中使用`Mode=Memory`和， `Cache=Shared`在多個連接之間共用。 `Data Source`關鍵字是用來提供記憶體中的資料庫名稱。 使用相同名稱的連接字串將會存取相同的記憶體內部資料庫。 只要至少有一個連接保持開啟狀態，資料庫就會持續存在。 GitHub 上提供示範此功能的[範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)。

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
