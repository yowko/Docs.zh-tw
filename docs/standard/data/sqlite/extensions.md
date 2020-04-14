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
# <a name="extensions"></a>延伸模組

SQLite 支援在運行時載入擴展。 擴展包括其他 SQL 函數、排序規則、虛擬表等。

.NET Core 包括用於在引用的 NuGet 包等其他位置定位本機庫的其他邏輯。 不幸的是,SQLite不能利用這個邏輯;它直接調用平臺 API 來載入庫。 因此,您可能需要在載入 SQLite 擴展之前修改 PATH、LD_LIBRARY_PATH 或DYLD_LIBRARY_PATH環境變數。 GitHub 上有[一個範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs),該示例演示了在引用的 NuGet 包中尋找目前的執行時的二進制檔。

要載入分機,請調用<xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>方法。 Microsoft.Data.Sqlite 將確保擴展保持載入狀態,即使連接已關閉並重新打開也是如此。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>另請參閱

* [執行時可載入擴充](https://www.sqlite.org/loadext.html)
