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
# <a name="encryption"></a><span data-ttu-id="e20b0-103">加密</span><span class="sxs-lookup"><span data-stu-id="e20b0-103">Encryption</span></span>

<span data-ttu-id="e20b0-104">SQLite 預設不支援加密資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="e20b0-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="e20b0-105">相反地，您必須使用已修改的 SQLite 版本，例如， [請參閱](https://www.hwaci.com/sw/sqlite/see.html)、 [SQLCipher](https://www.zetetic.net/sqlcipher/)、 [SQLiteCrypt](http://www.sqlite-crypt.com/)或 [wxSQLite3](https://utelle.github.io/wxsqlite3)。</span><span class="sxs-lookup"><span data-stu-id="e20b0-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="e20b0-106">本文將示範如何使用不支援的 SQLCipher 開放原始碼組建，但資訊也適用于其他解決方案，因為它們通常會遵循相同的模式。</span><span class="sxs-lookup"><span data-stu-id="e20b0-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="e20b0-107">安裝</span><span class="sxs-lookup"><span data-stu-id="e20b0-107">Installation</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="e20b0-108">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="e20b0-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="e20b0-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e20b0-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="e20b0-110">如需使用不同原生程式庫進行加密的詳細資訊，請參閱 [自訂 SQLite 版本](custom-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="e20b0-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="e20b0-111">指定金鑰</span><span class="sxs-lookup"><span data-stu-id="e20b0-111">Specify the key</span></span>

<span data-ttu-id="e20b0-112">若要在新的資料庫上啟用加密，請使用連接字串關鍵字來指定索引鍵 `Password` 。</span><span class="sxs-lookup"><span data-stu-id="e20b0-112">To enable encryption on a new database, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="e20b0-113">用 <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> 來新增或更新使用者輸入的值，並避免連接字串插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="e20b0-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

> [!TIP]
> <span data-ttu-id="e20b0-114">加密和解密現有資料庫的方法會根據您所使用的解決方案而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e20b0-114">The method for encrypting and decrypting existing databases varies depending on which solution you're using.</span></span> <span data-ttu-id="e20b0-115">例如，您需要 `sqlcipher_export()` 在 SQLCipher 上使用函數。</span><span class="sxs-lookup"><span data-stu-id="e20b0-115">For example, you need to use the `sqlcipher_export()` function on SQLCipher.</span></span> <span data-ttu-id="e20b0-116">請查看您解決方案的檔以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e20b0-116">Check your solution's documentation for details.</span></span>

## <a name="rekeying-the-database"></a><span data-ttu-id="e20b0-117">重新加密資料庫</span><span class="sxs-lookup"><span data-stu-id="e20b0-117">Rekeying the database</span></span>

<span data-ttu-id="e20b0-118">如果您想要變更加密資料庫的金鑰，請發出 `PRAGMA rekey` 語句。</span><span class="sxs-lookup"><span data-stu-id="e20b0-118">If you want to change the key of an encrypted database, issue a `PRAGMA rekey` statement.</span></span>

<span data-ttu-id="e20b0-119">可惜的是，SQLite 不支援語句中的參數 `PRAGMA` 。</span><span class="sxs-lookup"><span data-stu-id="e20b0-119">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="e20b0-120">相反地，請使用 `quote()` 函數來防止 SQL 插入。</span><span class="sxs-lookup"><span data-stu-id="e20b0-120">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
