---
title: 延伸模組
ms.date: 12/13/2019
description: 瞭解如何載入 SQLite 擴充。
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242955"
---
# <a name="extensions"></a><span data-ttu-id="dfb94-103">延伸模組</span><span class="sxs-lookup"><span data-stu-id="dfb94-103">Extensions</span></span>

<span data-ttu-id="dfb94-104">SQLite 支援在運行時載入擴展。</span><span class="sxs-lookup"><span data-stu-id="dfb94-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="dfb94-105">擴展包括其他 SQL 函數、排序規則、虛擬表等。</span><span class="sxs-lookup"><span data-stu-id="dfb94-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="dfb94-106">.NET Core 包括用於在引用的 NuGet 包等其他位置定位本機庫的其他邏輯。</span><span class="sxs-lookup"><span data-stu-id="dfb94-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="dfb94-107">不幸的是,SQLite不能利用這個邏輯;它直接調用平臺 API 來載入庫。</span><span class="sxs-lookup"><span data-stu-id="dfb94-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="dfb94-108">因此,您可能需要在載入 SQLite 擴展之前修改 PATH、LD_LIBRARY_PATH 或DYLD_LIBRARY_PATH環境變數。</span><span class="sxs-lookup"><span data-stu-id="dfb94-108">Because of this, you may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="dfb94-109">GitHub 上有[一個範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs),該示例演示了在引用的 NuGet 包中尋找目前的執行時的二進制檔。</span><span class="sxs-lookup"><span data-stu-id="dfb94-109">There's [a sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="dfb94-110">要載入分機,請調用<xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="dfb94-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="dfb94-111">Microsoft.Data.Sqlite 將確保擴展保持載入狀態,即使連接已關閉並重新打開也是如此。</span><span class="sxs-lookup"><span data-stu-id="dfb94-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="dfb94-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfb94-112">See also</span></span>

* [<span data-ttu-id="dfb94-113">執行時可載入擴充</span><span class="sxs-lookup"><span data-stu-id="dfb94-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
