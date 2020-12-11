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
# <a name="blob-io"></a>Blob I/O

> [!NOTE]
> SqliteBlob 類別已新增至3.0 版。

您可以藉由將資料流程入和移出資料庫的方式，在讀取和寫入大型物件時減少記憶體使用量。 當剖析或轉換資料時，這會特別有用。

首先，將資料列插入正常。 您 `zeroblob()` 可以使用 SQL 函數，在資料庫中配置空間來保存大型物件。 函式 `last_insert_rowid()` 提供便利的方式來取得其 rowid。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

插入資料列之後，請使用開啟資料流程來寫入大型物件 <xref:Microsoft.Data.Sqlite.SqliteBlob> 。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

若要從資料庫串流大型物件，除了大型物件的資料行之外，您還必須選取 rowid 或其中一個別名，如這裡所示。 如果您未選取 rowid，則整個物件將會載入記憶體中。 `GetStream()`當正確完成時，所傳回的物件會是 `SqliteBlob` 。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
