---
title: 批次處理
ms.date: 12/13/2019
description: 瞭解如何在單一命令中執行 SQL 語句的批次。
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447052"
---
# <a name="batching"></a><span data-ttu-id="3c193-103">批次處理</span><span class="sxs-lookup"><span data-stu-id="3c193-103">Batching</span></span>

<span data-ttu-id="3c193-104">SQLite 原本就不支援將 SQL 語句一起批次處理成單一命令。</span><span class="sxs-lookup"><span data-stu-id="3c193-104">SQLite doesn't natively support batching SQL statements together into a single command.</span></span> <span data-ttu-id="3c193-105">但是因為沒有涉及的網路，所以還是不會真正協助效能。</span><span class="sxs-lookup"><span data-stu-id="3c193-105">But because there's no network involved, it wouldn't really help performance anyway.</span></span> <span data-ttu-id="3c193-106">不過，Sqlite 會將語句批次處理實作為便利，使其行為更像其他 ADO.NET 提供者。</span><span class="sxs-lookup"><span data-stu-id="3c193-106">Microsoft.Data.Sqlite does, however, implement statement batching as a convenience to make it behave more like other ADO.NET providers.</span></span>

<span data-ttu-id="3c193-107">當呼叫<xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>時，語句會執行到第一個傳回結果的。</span><span class="sxs-lookup"><span data-stu-id="3c193-107">When calling <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, statements are executed up to the first one that returns results.</span></span> <span data-ttu-id="3c193-108">呼叫<xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType>會繼續執行語句，直到下一個會傳回結果，或直到到達批次結尾為止。</span><span class="sxs-lookup"><span data-stu-id="3c193-108">Calling <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> continues executing statements until the next one that returns results or until it reaches the end of the batch.</span></span> <span data-ttu-id="3c193-109">呼叫<xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType>或<xref:System.Data.Common.DbDataReader.Close%2A>執行任何未使用的其餘語句`NextResult()`。</span><span class="sxs-lookup"><span data-stu-id="3c193-109">Calling <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> or <xref:System.Data.Common.DbDataReader.Close%2A> executes any remaining statements that haven't been consumed by `NextResult()`.</span></span> <span data-ttu-id="3c193-110">如果您未處置資料讀取器，完成項會嘗試執行其餘的語句，但它遇到的任何錯誤都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="3c193-110">If you don't dispose a data reader, the finalizer tries to execute the remaining statements, but any errors it encounters are ignored.</span></span> <span data-ttu-id="3c193-111">因此，在使用批次時，請`DbDataReader`務必處置物件。</span><span class="sxs-lookup"><span data-stu-id="3c193-111">Because of this, it's important to dispose `DbDataReader` objects when using batches.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a><span data-ttu-id="3c193-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c193-112">See also</span></span>

* [<span data-ttu-id="3c193-113">Bulk Insert</span><span class="sxs-lookup"><span data-stu-id="3c193-113">Bulk Insert</span></span>](bulk-insert.md)
