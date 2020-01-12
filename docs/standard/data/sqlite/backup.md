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
# <a name="online-backup"></a><span data-ttu-id="31072-103">線上備份</span><span class="sxs-lookup"><span data-stu-id="31072-103">Online backup</span></span>

<span data-ttu-id="31072-104">SQLite 可以在應用程式正在執行時備份資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="31072-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="31072-105">這項功能可在 `SqliteConnection`上的 <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> 方法中，以資料 Sqlite 的形式提供。</span><span class="sxs-lookup"><span data-stu-id="31072-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="31072-106">目前，`BackupDatabase` 會儘快備份資料庫，並封鎖其他連接，使其無法寫入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="31072-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="31072-107">問題[#13834](https://github.com/dotnet/efcore/issues/13834)會提供替代的 API，以在背景中備份資料庫，並允許其他連接中斷備份並寫入資料庫。</span><span class="sxs-lookup"><span data-stu-id="31072-107">Issue [#13834](https://github.com/dotnet/efcore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="31072-108">如果您有興趣，請提供有關問題的意見反應。</span><span class="sxs-lookup"><span data-stu-id="31072-108">If you're interested, provide feedback on the issue.</span></span>
