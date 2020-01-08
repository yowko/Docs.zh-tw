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
# <a name="encryption"></a><span data-ttu-id="48606-103">[加密]</span><span class="sxs-lookup"><span data-stu-id="48606-103">Encryption</span></span>

<span data-ttu-id="48606-104">SQLite 預設不支援加密資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="48606-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="48606-105">相反地，您需要使用已修改的 SQLite 版本，如[參閱](https://www.hwaci.com/sw/sqlite/see.html)、 [SQLCipher](https://www.zetetic.net/sqlcipher/)、 [SQLiteCrypt](http://www.sqlite-crypt.com/)或[wxSQLite3](https://utelle.github.io/wxsqlite3)。</span><span class="sxs-lookup"><span data-stu-id="48606-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="48606-106">本文示範如何使用不受支援的開放原始碼 SQLCipher 組建，但這些資訊也適用于其他解決方案，因為它們通常會遵循相同的模式。</span><span class="sxs-lookup"><span data-stu-id="48606-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="48606-107">安裝</span><span class="sxs-lookup"><span data-stu-id="48606-107">Installation</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="48606-108">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="48606-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="48606-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="48606-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="48606-110">如需有關使用不同的原生程式庫進行加密的詳細資訊，請參閱[自訂 SQLite 版本](custom-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="48606-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="48606-111">指定金鑰</span><span class="sxs-lookup"><span data-stu-id="48606-111">Specify the key</span></span>

<span data-ttu-id="48606-112">若要啟用加密，請使用 `Password` 連接字串關鍵字來指定金鑰。</span><span class="sxs-lookup"><span data-stu-id="48606-112">To enable encryption, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="48606-113">使用 <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> 來新增或更新使用者輸入的值，並避免連接字串插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="48606-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a><span data-ttu-id="48606-114">重新加密資料庫</span><span class="sxs-lookup"><span data-stu-id="48606-114">Rekeying the database</span></span>

<span data-ttu-id="48606-115">如果您想要變更資料庫的加密金鑰，請發出 `PRAGMA rekey` 語句。</span><span class="sxs-lookup"><span data-stu-id="48606-115">If you want to change the encryption key of a database, issue a `PRAGMA rekey` statement.</span></span> <span data-ttu-id="48606-116">若要解密資料庫，請指定 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="48606-116">To decrypt the database, specify `NULL`.</span></span>

<span data-ttu-id="48606-117">可惜的是，SQLite 不支援 `PRAGMA` 語句中的參數。</span><span class="sxs-lookup"><span data-stu-id="48606-117">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="48606-118">請改用 `quote()` 函數來防止 SQL 插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="48606-118">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
