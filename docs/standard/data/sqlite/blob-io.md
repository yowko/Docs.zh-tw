---
title: Blob I/O
ms.date: 12/08/2020
description: 瞭解如何使用 SQLite 的 BLOB i/o 功能。
ms.openlocfilehash: 8b305669f3155d2366215e9a05beb5ed51533d81
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110041"
---
# <a name="blob-io"></a><span data-ttu-id="93342-103">Blob I/O</span><span class="sxs-lookup"><span data-stu-id="93342-103">Blob I/O</span></span>

> [!NOTE]
> <span data-ttu-id="93342-104">SqliteBlob 類別已新增至3.0 版。</span><span class="sxs-lookup"><span data-stu-id="93342-104">The SqliteBlob class was added in version 3.0.</span></span>

<span data-ttu-id="93342-105">您可以藉由將資料流程入和移出資料庫的方式，在讀取和寫入大型物件時減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="93342-105">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="93342-106">當剖析或轉換資料時，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="93342-106">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="93342-107">首先，將資料列插入正常。</span><span class="sxs-lookup"><span data-stu-id="93342-107">Start by inserting a row as normal.</span></span> <span data-ttu-id="93342-108">您 `zeroblob()` 可以使用 SQL 函數，在資料庫中配置空間來保存大型物件。</span><span class="sxs-lookup"><span data-stu-id="93342-108">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="93342-109">函式 `last_insert_rowid()` 提供便利的方式來取得其 rowid。</span><span class="sxs-lookup"><span data-stu-id="93342-109">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="93342-110">插入資料列之後，請使用開啟資料流程來寫入大型物件 <xref:Microsoft.Data.Sqlite.SqliteBlob> 。</span><span class="sxs-lookup"><span data-stu-id="93342-110">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="93342-111">若要從資料庫串流大型物件，除了大型物件的資料行之外，您還必須選取 rowid 或其中一個別名，如這裡所示。</span><span class="sxs-lookup"><span data-stu-id="93342-111">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="93342-112">如果您未選取 rowid，則整個物件將會載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="93342-112">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="93342-113">`GetStream()`當正確完成時，所傳回的物件會是 `SqliteBlob` 。</span><span class="sxs-lookup"><span data-stu-id="93342-113">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
