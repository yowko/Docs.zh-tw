---
title: '[加密]'
ms.date: 12/13/2019
description: 瞭解如何加密您的資料庫檔案。
ms.openlocfilehash: ccdd4b6b8642b3cde1c2667c9ca432a9b0ef21f2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447262"
---
# <a name="encryption"></a>[加密]

SQLite 預設不支援加密資料庫檔案。 相反地，您需要使用已修改的 SQLite 版本，如[參閱](https://www.hwaci.com/sw/sqlite/see.html)、 [SQLCipher](https://www.zetetic.net/sqlcipher/)、 [SQLiteCrypt](http://www.sqlite-crypt.com/)或[wxSQLite3](https://utelle.github.io/wxsqlite3)。 本文示範如何使用不受支援的開放原始碼 SQLCipher 組建，但這些資訊也適用于其他解決方案，因為它們通常會遵循相同的模式。

## <a name="installation"></a>安裝

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

如需有關使用不同的原生程式庫進行加密的詳細資訊，請參閱[自訂 SQLite 版本](custom-versions.md)。

## <a name="specify-the-key"></a>指定金鑰

若要啟用加密，請使用 `Password` 連接字串關鍵字來指定金鑰。 使用 <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> 來新增或更新使用者輸入的值，並避免連接字串插入式攻擊。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a>重新加密資料庫

如果您想要變更資料庫的加密金鑰，請發出 `PRAGMA rekey` 語句。 若要解密資料庫，請指定 `NULL`。

可惜的是，SQLite 不支援 `PRAGMA` 語句中的參數。 請改用 `quote()` 函數來防止 SQL 插入式攻擊。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
