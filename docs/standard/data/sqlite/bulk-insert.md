---
title: Bulk insert
ms.date: 12/13/2019
description: 當您對資料庫進行大量變更時，可以使用的效能秘訣。
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447038"
---
# <a name="bulk-insert"></a>Bulk insert

SQLite 沒有任何特殊的方式可大量插入資料。 若要在插入或更新資料時獲得最佳效能，請務必執行下列動作：

- 使用交易。
- 重複使用相同的參數化命令。 後續執行會重複使用第一個執行的編譯。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
