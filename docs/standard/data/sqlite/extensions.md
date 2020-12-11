---
title: 延伸模組
ms.date: 12/08/2020
description: 瞭解如何載入 SQLite 擴充功能。
ms.openlocfilehash: 68d31093662f373d6ebf4460d6a5d44029c27c5c
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110841"
---
# <a name="extensions"></a><span data-ttu-id="5f48a-103">延伸模組</span><span class="sxs-lookup"><span data-stu-id="5f48a-103">Extensions</span></span>

<span data-ttu-id="5f48a-104">SQLite 支援在執行時間載入擴充功能。</span><span class="sxs-lookup"><span data-stu-id="5f48a-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="5f48a-105">擴充功能包括其他 SQL 函數、定序、虛擬資料表等專案。</span><span class="sxs-lookup"><span data-stu-id="5f48a-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="5f48a-106">.NET Core 包含額外的邏輯，可在其他位置（例如參考的 NuGet 套件）中尋找原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="5f48a-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="5f48a-107">可惜的是，SQLite 無法利用這個邏輯;它會直接呼叫平臺 API 來載入程式庫。</span><span class="sxs-lookup"><span data-stu-id="5f48a-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="5f48a-108">因此，您可能需要先修改路徑、LD_LIBRARY_PATH 或 DYLD_LIBRARY_PATH 環境變數，然後再載入 SQLite 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="5f48a-108">Because of this, you may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="5f48a-109">GitHub 上有 [一個範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) ，示範如何在參考的 NuGet 套件內尋找目前執行時間的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="5f48a-109">There's [a sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="5f48a-110">若要載入擴充功能，請呼叫 <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5f48a-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="5f48a-111">如果連接已關閉並重新開啟，則會確保延伸模組仍維持載入。</span><span class="sxs-lookup"><span data-stu-id="5f48a-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

> [!NOTE]
> <span data-ttu-id="5f48a-112">LoadExtension 方法已新增至3.0 版。</span><span class="sxs-lookup"><span data-stu-id="5f48a-112">The LoadExtension method was added in version 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f48a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f48a-113">See also</span></span>

* [<span data-ttu-id="5f48a-114">執行時間可載入的擴充功能</span><span class="sxs-lookup"><span data-stu-id="5f48a-114">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
