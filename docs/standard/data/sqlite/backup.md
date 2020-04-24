---
title: 線上備份
ms.date: 12/13/2019
description: 瞭解如何使用 SQLite 的線上備份功能。
ms.openlocfilehash: d857dcb69f2b2d10b034a0abf222b30c2e20bb41
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901276"
---
# <a name="online-backup"></a>線上備份

SQLite 可以在應用程式正在執行時備份資料庫檔案。 這項功能會在中提供，做為上<xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> `SqliteConnection`的方法。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

目前， `BackupDatabase`會儘快備份資料庫，並封鎖其他連接寫入資料庫。 問題[#13834](https://github.com/dotnet/efcore/issues/13834)會提供替代的 API，以在背景中備份資料庫，並允許其他連接中斷備份並寫入資料庫。 如果您有興趣，請提供有關問題的意見反應。
