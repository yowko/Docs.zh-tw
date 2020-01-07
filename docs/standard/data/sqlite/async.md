---
title: 非同步限制
ms.date: 12/13/2019
description: 說明非同步 Api 的限制，以及您可以改用的一些替代方案。
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447080"
---
# <a name="async-limitations"></a>非同步限制

SQLite 不支援非同步 i/o。 非同步 ADO.NET 方法會在 Microsoft. Sqlite 中以同步方式執行。 請避免呼叫它們。

相反地，請使用[預先寫入記錄](https://www.sqlite.org/wal.html)來改善效能和平行存取。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> 在使用[Entity Framework Core](/ef/core/)建立的資料庫上，預設會啟用預先寫入記錄。
