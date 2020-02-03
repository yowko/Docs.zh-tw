---
title: 自訂 SQLite 版本
ms.date: 12/13/2019
description: 瞭解如何使用自訂版本的原生 SQLite 程式庫。
ms.openlocfilehash: dd27278c1dbe17b12e5067d04d19043bf259b1e8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746986"
---
# <a name="custom-sqlite-versions"></a>自訂 SQLite 版本

SQLitePCLRaw 是以最上層為基礎。 您可以使用配套或藉由設定 SQLitePCLRaw 提供者，以使用原生 SQLite 程式庫的自訂版本。

## <a name="bundles"></a>組合

SQLitePCLRaw 提供配套套件，可讓您輕鬆地在不同的平臺上帶入正確的相依性。

根據預設，SQLitePCLRaw 中會引進主要的 Microsoft 資料 Sqlite 封裝 bundle_e_sqlite3。

若要使用不同的配套，請改為安裝 `Microsoft.Data.Sqlite.Core` 套件，以及您要使用的配套套件。 套件組合會由 Microsoft 自動初始化。

| 組合 | 描述 |
| --- | --- |
| SQLitePCLRaw。 bundle_e_sqlite3 | 在所有平臺上提供一致版本的 SQLite。 包含 FTS4、FTS5、JSON1 和 R * 樹狀目錄延伸模組。 這是預設值。 |
| SQLitePCLRaw。 bundle_green | 與 bundle_e_sqlite3 相同，除非在 iOS 上使用系統 SQLite 程式庫。 |
| SQLitePCLRaw。 bundle_zetetic | 使用來自 Zetetic 的官方 SQLCipher 組建（不包含）。 |
| SQLitePCLRaw。 bundle_winsqlite3 | 會使用 winsqlite3，也就是 Windows 10 上的系統 SQLite 程式庫。 |
| SQLitePCLRaw。 bundle_e_sqlcipher | 提供 SQLCipher 的非官方開放原始碼組建。 |

例如，若要使用非官方的開放原始碼組建 SQLCipher，請使用下列命令。

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a>SQLitePCLRaw 提供者

您可以使用自己的 SQLite 組建，方法是利用 `SQLitePCLRaw.provider.dynamic_cdecl` 套件。 在此情況下，您必須負責使用您的應用程式來部署原生程式庫。 請注意，使用您的應用程式部署原生程式庫的詳細資料，會根據您所使用的 .NET 平臺和執行時間而有很大的差異。

首先，您必須執行 IGetFunctionPointer。 在 .NET Core 上執行的方式相當簡單。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

接下來，設定 SQLitePCLRaw 提供者。 請確定已在您的應用程式中使用 Sqlite。 此外，請避免使用可能會覆寫您提供者的 SQLitePCLRaw 組合套件。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
