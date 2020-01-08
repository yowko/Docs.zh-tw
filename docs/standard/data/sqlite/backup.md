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
# <a name="online-backup"></a><span data-ttu-id="cbc0f-103">線上備份</span><span class="sxs-lookup"><span data-stu-id="cbc0f-103">Online backup</span></span>

<span data-ttu-id="cbc0f-104">SQLite 可以在應用程式正在執行時備份資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="cbc0f-105">這項功能可在 `SqliteConnection`上的 <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> 方法中，以資料 Sqlite 的形式提供。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="cbc0f-106">目前，`BackupDatabase` 會儘快備份資料庫，並封鎖其他連接，使其無法寫入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="cbc0f-107">問題[#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834)會提供替代的 API，以在背景中備份資料庫，並允許其他連接中斷備份並寫入資料庫。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-107">Issue [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="cbc0f-108">如果您有興趣，請提供有關問題的意見反應。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-108">If you're interested, provide feedback on the issue.</span></span>
