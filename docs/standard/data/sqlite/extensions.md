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
# <a name="extensions"></a>延伸模組

SQLite 支援在執行時間載入擴充功能。 擴充功能包括其他 SQL 函數、定序、虛擬資料表等專案。

.NET Core 包含額外的邏輯，可在其他位置（例如參考的 NuGet 套件）中尋找原生程式庫。 可惜的是，SQLite 無法利用這個邏輯;它會直接呼叫平臺 API 來載入程式庫。 因此，您可能需要先修改路徑、LD_LIBRARY_PATH 或 DYLD_LIBRARY_PATH 環境變數，然後再載入 SQLite 擴充功能。 GitHub 上有 [一個範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) ，示範如何在參考的 NuGet 套件內尋找目前執行時間的二進位檔。

若要載入擴充功能，請呼叫 <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> 方法。 如果連接已關閉並重新開啟，則會確保延伸模組仍維持載入。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

> [!NOTE]
> LoadExtension 方法已新增至3.0 版。

## <a name="see-also"></a>另請參閱

* [執行時間可載入的擴充功能](https://www.sqlite.org/loadext.html)
