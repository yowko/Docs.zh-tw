---
title: 延伸模組
ms.date: 12/13/2019
description: 瞭解如何載入 SQLite 延伸模組。
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242955"
---
# <a name="extensions"></a>延伸模組

SQLite 支援在執行時間載入擴充功能。 延伸模組包括其他 SQL 函數、定序、虛擬資料表等專案。

.NET Core 包含額外的邏輯，可在其他地方尋找原生程式庫，例如參考的 NuGet 套件。 可惜的是，SQLite 無法利用這個邏輯;它會直接呼叫平臺 API 來載入程式庫。 因此，在載入 SQLite 擴充功能之前，您可能需要修改路徑、LD_LIBRARY_PATH 或 DYLD_LIBRARY_PATH 環境變數。 GitHub 上有[一個範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs)，示範如何在參考的 NuGet 套件內尋找目前執行時間的二進位檔。

若要載入擴充功能，請<xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>呼叫方法。 如果連接已關閉並重新開啟，則 Sqlite 會確保延伸模組保持載入。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>另請參閱

* [執行時間可載入的擴充功能](https://www.sqlite.org/loadext.html)
