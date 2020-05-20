---
title: 自訂 SQLite 版本
ms.date: 05/14/2020
description: 瞭解如何使用自訂版本的原生 SQLite 程式庫。
ms.openlocfilehash: 15db10db26bc7c5017313ca020a0e1e528ba207a
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83440833"
---
# <a name="custom-sqlite-versions"></a>自訂 SQLite 版本

`Microsoft.Data.Sqlite`建置於之上 `SQLitePCLRaw` 。 您可以使用配套或設定提供者，以使用原生 SQLite 程式庫的自訂版本 `SQLitePCLRaw` 。

## <a name="bundles"></a>組合

`SQLitePCLRaw`提供便利的組合套件，可讓您輕鬆地在不同的平臺上帶入正確的相依性。 主要 `Microsoft.Data.Sqlite` 套件預設會帶入 `SQLitePCLRaw.bundle_e_sqlite3` 。 若要使用不同的配套，請將 `Microsoft.Data.Sqlite.Core` 套件與您要使用的配套套件一起安裝。 套件組合會由自動初始化 `Microsoft.Data.Sqlite` 。

| 套件組合 | 說明 |
|--|--|
| [SQLitePCLRaw。 bundle_e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | 在所有平臺上提供一致版本的 SQLite。 包含 FTS4、FTS5、JSON1 和 R * 樹狀目錄延伸模組。 此為預設值。 |
| [SQLitePCLRaw。 bundle_e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | 提供的非官方開放原始碼組建 `SQLCipher` 。 |
| [SQLitePCLRaw。 bundle_green](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | 與相同 `bundle_e_sqlite3` ，除非在 iOS 上使用系統 SQLite 程式庫。 |
| [SQLitePCLRaw。 bundle_winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | 使用 `winsqlite3.dll` ，Windows 10 上的系統 SQLite 程式庫。 |
| [SQLitePCLRaw。 bundle_zetetic](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | 使用 `SQLCipher` 來自 Zetetic 的官方組建（不包含）。 |

例如，若要使用非官方的開放原始碼組建，請 `SQLCipher` 使用下列命令。

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a>SQLitePCLRaw 可用的提供者

當不依賴配套時，您可以使用 SQLite 的可用提供者搭配核心元件。

| 提供者 | 說明 |
|--|--|
| [SQLitePCLRaw。 dynamic](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | `dynamic`提供者會載入原生程式庫，而不是使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> 屬性。 如需使用此提供者的詳細資訊，請參閱[使用動態提供者](#use-the-dynamic-provider)。 |
| [SQLitePCLRaw。 e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | `e_sqlite3`是預設提供者。 |
| [SQLitePCLRaw。 e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | `e_sqlcipher`提供者是非官方和不支援的 `SQLCipher` 。 |
| [SQLitePCLRaw. provider. db.sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | `sqlite3`提供者是 `SQLite` 針對 IOS、MacOS 和 Linux 提供的系統。 |
| [SQLitePCLRaw. provider. sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | `sqlcipher`提供者是來自的官方 `SQLCipher` 組建 `Zetetic` 。 |
| [SQLitePCLRaw. provider. winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | `winsqlite3`提供者適用于 Windows 10 環境。 |

若要使用 `sqlite3` 提供者，請使用下列命令：

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

安裝封裝之後，您就可以將提供者設定為 `sqlite3` 實例。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a>使用動態提供者

您可以利用套件來使用自己的 SQLite 組建 `SQLitePCLRaw.provider.dynamic_cdecl` 。 在此情況下，您必須負責使用您的應用程式來部署原生程式庫。 請注意，使用您的應用程式部署原生程式庫的詳細資料，會根據您所使用的 .NET 平臺和執行時間而有很大的差異。

首先，您必須執行 `IGetFunctionPointer` 。 .NET Core 上的實作為如下所示：

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

接下來，設定 `SQLitePCLRaw` 提供者。 請確定已 `Microsoft.Data.Sqlite` 在應用程式中使用之前完成這項作業。 此外，請避免使用 `SQLitePCLRaw` 可能會覆寫您提供者的組合套件。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
