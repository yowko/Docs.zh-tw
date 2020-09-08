---
title: 非同步限制
ms.date: 09/04/2020
description: 說明非同步 Api 的限制，以及您可以改用的一些替代方案。
ms.openlocfilehash: 8b14fcfeb12d331d8d43ca6d77332007a12ae5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515991"
---
# <a name="async-limitations"></a>非同步限制

SQLite 不支援非同步 i/o。 非同步 ADO.NET 方法會在 Microsoft 中以同步方式執行。 避免呼叫它們。

相反地，請使用 [共用](connection-strings.md#cache) 快取和預先 [寫入記錄](https://www.sqlite.org/wal.html) ，以改善效能和平行存取。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> 依預設，會在使用 [Entity Framework Core](/ef/core/)建立的資料庫上啟用預先寫入記錄。
