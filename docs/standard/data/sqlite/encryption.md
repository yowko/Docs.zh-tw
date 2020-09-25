---
title: 加密
ms.date: 09/08/2020
description: 瞭解如何加密您的資料庫檔案。
ms.openlocfilehash: 1b33e1510a269aba87caba2cd39faab33791aa55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203406"
---
# <a name="encryption"></a>加密

SQLite 預設不支援加密資料庫檔案。 相反地，您必須使用已修改的 SQLite 版本，例如， [請參閱](https://www.hwaci.com/sw/sqlite/see.html)、 [SQLCipher](https://www.zetetic.net/sqlcipher/)、 [SQLiteCrypt](http://www.sqlite-crypt.com/)或 [wxSQLite3](https://utelle.github.io/wxsqlite3)。 本文將示範如何使用不支援的 SQLCipher 開放原始碼組建，但資訊也適用于其他解決方案，因為它們通常會遵循相同的模式。

## <a name="installation"></a>安裝

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

如需使用不同原生程式庫進行加密的詳細資訊，請參閱 [自訂 SQLite 版本](custom-versions.md)。

## <a name="specify-the-key"></a>指定金鑰

若要在新的資料庫上啟用加密，請使用連接字串關鍵字來指定索引鍵 `Password` 。 用 <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> 來新增或更新使用者輸入的值，並避免連接字串插入式攻擊。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

> [!TIP]
> 加密和解密現有資料庫的方法會根據您所使用的解決方案而有所不同。 例如，您需要 `sqlcipher_export()` 在 SQLCipher 上使用函數。 請查看您解決方案的檔以取得詳細資料。

## <a name="rekeying-the-database"></a>重新加密資料庫

如果您想要變更加密資料庫的金鑰，請發出 `PRAGMA rekey` 語句。

可惜的是，SQLite 不支援語句中的參數 `PRAGMA` 。 相反地，請使用 `quote()` 函數來防止 SQL 插入。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
