---
title: 線上備份
ms.date: 12/13/2019
description: 瞭解如何使用 SQLite 的線上備份功能。
ms.openlocfilehash: 885aa2c5555b58deb2551c0a4e6933742a093457
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447094"
---
# <a name="online-backup"></a>線上備份

SQLite 可以在應用程式正在執行時備份資料庫檔案。 這項功能可在 `SqliteConnection`上的 <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> 方法中，以資料 Sqlite 的形式提供。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

目前，`BackupDatabase` 會儘快備份資料庫，並封鎖其他連接，使其無法寫入至資料庫。 問題[#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834)會提供替代的 API，以在背景中備份資料庫，並允許其他連接中斷備份並寫入資料庫。 如果您有興趣，請提供有關問題的意見反應。
