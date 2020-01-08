---
title: Blob i/o
ms.date: 12/13/2019
description: 瞭解如何使用 SQLite 的 BLOB i/o 功能。
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447045"
---
# <a name="blob-io"></a>Blob i/o

在讀取和寫入大型物件時，您可以藉由將資料流程入或輸出到資料庫，來減少記憶體使用量。 當剖析或轉換資料時，這會特別有用。

一開始請先以一般方式插入資料列。 使用 `zeroblob()` SQL 函數，在資料庫中配置空間來保存大型物件。 `last_insert_rowid()` 函式提供一個便利的方式來取得其 rowid。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

插入資料列之後，使用 <xref:Microsoft.Data.Sqlite.SqliteBlob>開啟資料流程來寫入大型物件。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

若要從資料庫將大型物件串流，除了大型物件的資料行之外，您還必須選取 [rowid] 或它的其中一個別名做為 [顯示于此處]。 如果您未選取 [rowid]，整個物件就會載入記憶體中。 當正確完成時，`GetStream()` 傳回的物件將會是 `SqliteBlob`。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
