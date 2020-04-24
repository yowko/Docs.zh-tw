---
title: Blob I/O
ms.date: 12/13/2019
description: 瞭解如何使用 SQLite 的 BLOB i/o 功能。
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447045"
---
# <a name="blob-io"></a><span data-ttu-id="9461e-103">Blob I/O</span><span class="sxs-lookup"><span data-stu-id="9461e-103">Blob I/O</span></span>

<span data-ttu-id="9461e-104">在讀取和寫入大型物件時，您可以藉由將資料流程入或輸出到資料庫，來減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="9461e-104">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="9461e-105">當剖析或轉換資料時，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="9461e-105">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="9461e-106">一開始請先以一般方式插入資料列。</span><span class="sxs-lookup"><span data-stu-id="9461e-106">Start by inserting a row as normal.</span></span> <span data-ttu-id="9461e-107">使用`zeroblob()` SQL 函數來設定資料庫中的空間，以保存大型物件。</span><span class="sxs-lookup"><span data-stu-id="9461e-107">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="9461e-108">`last_insert_rowid()`函式提供便利的方式來取得其 rowid。</span><span class="sxs-lookup"><span data-stu-id="9461e-108">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="9461e-109">插入資料列之後，請使用<xref:Microsoft.Data.Sqlite.SqliteBlob>來開啟資料流程，以寫入大型物件。</span><span class="sxs-lookup"><span data-stu-id="9461e-109">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="9461e-110">若要從資料庫將大型物件串流，除了大型物件的資料行之外，您還必須選取 [rowid] 或它的其中一個別名做為 [顯示于此處]。</span><span class="sxs-lookup"><span data-stu-id="9461e-110">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="9461e-111">如果您未選取 [rowid]，整個物件就會載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="9461e-111">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="9461e-112">當正確完成時`GetStream()` ，所傳回的物件將會是。 `SqliteBlob`</span><span class="sxs-lookup"><span data-stu-id="9461e-112">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
