---
title: 自訂 SQLite 版本
ms.date: 12/13/2019
description: 瞭解如何使用自訂版本的原生 SQLite 程式庫。
ms.openlocfilehash: 8a2646138ea9dbecf412a2e8e0e347e2d71a5b0b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447143"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="0d90e-103">自訂 SQLite 版本</span><span class="sxs-lookup"><span data-stu-id="0d90e-103">Custom SQLite versions</span></span>

<span data-ttu-id="0d90e-104">SQLitePCLRaw 是以最上層為基礎。</span><span class="sxs-lookup"><span data-stu-id="0d90e-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="0d90e-105">您可以使用配套或藉由設定 SQLitePCLRaw 提供者，以使用原生 SQLite 程式庫的自訂版本。</span><span class="sxs-lookup"><span data-stu-id="0d90e-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="0d90e-106">組合</span><span class="sxs-lookup"><span data-stu-id="0d90e-106">Bundles</span></span>

<span data-ttu-id="0d90e-107">SQLitePCLRaw 提供配套套件，可讓您輕鬆地在不同的平臺上帶入正確的相依性。</span><span class="sxs-lookup"><span data-stu-id="0d90e-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="0d90e-108">根據預設，SQLitePCLRaw 中會引進主要的 Microsoft 資料 Sqlite 封裝 bundle_e_sqlite3。</span><span class="sxs-lookup"><span data-stu-id="0d90e-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="0d90e-109">若要使用不同的配套，請改為安裝 `Microsoft.Data.Sqlite.Core` 套件，以及您要使用的配套套件。</span><span class="sxs-lookup"><span data-stu-id="0d90e-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="0d90e-110">套件組合會由 Microsoft 自動初始化。</span><span class="sxs-lookup"><span data-stu-id="0d90e-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="0d90e-111">配套</span><span class="sxs-lookup"><span data-stu-id="0d90e-111">Bundle</span></span> | <span data-ttu-id="0d90e-112">描述</span><span class="sxs-lookup"><span data-stu-id="0d90e-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="0d90e-113">SQLitePCLRaw。 bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="0d90e-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="0d90e-114">在所有平臺上提供一致版本的 SQLite。</span><span class="sxs-lookup"><span data-stu-id="0d90e-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="0d90e-115">包含 FTS4、FTS5、JSON1 和</span><span class="sxs-lookup"><span data-stu-id="0d90e-115">Includes the FTS4, FTS5, JSON1, and</span></span> | <span data-ttu-id="0d90e-116">R \* 樹狀目錄延伸模組。</span><span class="sxs-lookup"><span data-stu-id="0d90e-116">R\*Tree extensions.</span></span> <span data-ttu-id="0d90e-117">這是預設設定。</span><span class="sxs-lookup"><span data-stu-id="0d90e-117">This is the default.</span></span> |
| <span data-ttu-id="0d90e-118">SQLitePCLRaw。 bundle_green</span><span class="sxs-lookup"><span data-stu-id="0d90e-118">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="0d90e-119">與 bundle_e_sqlite3 相同，除非在 iOS 上使用系統 SQLite 程式庫。</span><span class="sxs-lookup"><span data-stu-id="0d90e-119">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="0d90e-120">SQLitePCLRaw。 bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="0d90e-120">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="0d90e-121">使用來自 Zetetic 的官方 SQLCipher 組建（不包含）。</span><span class="sxs-lookup"><span data-stu-id="0d90e-121">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="0d90e-122">SQLitePCLRaw。 bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="0d90e-122">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="0d90e-123">會使用 winsqlite3，也就是 Windows 10 上的系統 SQLite 程式庫。</span><span class="sxs-lookup"><span data-stu-id="0d90e-123">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="0d90e-124">SQLitePCLRaw。 bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="0d90e-124">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="0d90e-125">提供 SQLCipher 的非官方開放原始碼組建。</span><span class="sxs-lookup"><span data-stu-id="0d90e-125">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="0d90e-126">例如，若要使用非官方的開放原始碼組建 SQLCipher，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="0d90e-126">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="0d90e-127">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="0d90e-127">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="0d90e-128">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d90e-128">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="0d90e-129">SQLitePCLRaw 提供者</span><span class="sxs-lookup"><span data-stu-id="0d90e-129">SQLitePCLRaw providers</span></span>

<span data-ttu-id="0d90e-130">您可以使用自己的 SQLite 組建，方法是利用 `SQLitePCLRaw.provider.dynamic_cdecl` 套件。</span><span class="sxs-lookup"><span data-stu-id="0d90e-130">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="0d90e-131">在此情況下，您必須負責使用您的應用程式來部署原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="0d90e-131">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="0d90e-132">請注意，使用您的應用程式部署原生程式庫的詳細資料，會根據您所使用的 .NET 平臺和執行時間而有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="0d90e-132">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="0d90e-133">首先，您必須執行 IGetFunctionPointer。</span><span class="sxs-lookup"><span data-stu-id="0d90e-133">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="0d90e-134">在 .NET Core 上執行的方式相當簡單。</span><span class="sxs-lookup"><span data-stu-id="0d90e-134">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="0d90e-135">接下來，設定 SQLitePCLRaw 提供者。</span><span class="sxs-lookup"><span data-stu-id="0d90e-135">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="0d90e-136">請確定已在您的應用程式中使用 Sqlite。</span><span class="sxs-lookup"><span data-stu-id="0d90e-136">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="0d90e-137">此外，請避免使用可能會覆寫您提供者的 SQLitePCLRaw 組合套件。</span><span class="sxs-lookup"><span data-stu-id="0d90e-137">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
