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
# <a name="custom-sqlite-versions"></a><span data-ttu-id="aaaa7-103">自訂 SQLite 版本</span><span class="sxs-lookup"><span data-stu-id="aaaa7-103">Custom SQLite versions</span></span>

<span data-ttu-id="aaaa7-104">`Microsoft.Data.Sqlite`建置於之上 `SQLitePCLRaw` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="aaaa7-105">您可以使用配套或設定提供者，以使用原生 SQLite 程式庫的自訂版本 `SQLitePCLRaw` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="aaaa7-106">組合</span><span class="sxs-lookup"><span data-stu-id="aaaa7-106">Bundles</span></span>

<span data-ttu-id="aaaa7-107">`SQLitePCLRaw`提供便利的組合套件，可讓您輕鬆地在不同的平臺上帶入正確的相依性。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="aaaa7-108">主要 `Microsoft.Data.Sqlite` 套件預設會帶入 `SQLitePCLRaw.bundle_e_sqlite3` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="aaaa7-109">若要使用不同的配套，請將 `Microsoft.Data.Sqlite.Core` 套件與您要使用的配套套件一起安裝。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="aaaa7-110">套件組合會由自動初始化 `Microsoft.Data.Sqlite` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="aaaa7-111">套件組合</span><span class="sxs-lookup"><span data-stu-id="aaaa7-111">Bundle</span></span> | <span data-ttu-id="aaaa7-112">說明</span><span class="sxs-lookup"><span data-stu-id="aaaa7-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="aaaa7-113">SQLitePCLRaw。 bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="aaaa7-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="aaaa7-114">在所有平臺上提供一致版本的 SQLite。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="aaaa7-115">包含 FTS4、FTS5、JSON1 和 R \* 樹狀目錄延伸模組。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="aaaa7-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-116">This is the default.</span></span> |
| [<span data-ttu-id="aaaa7-117">SQLitePCLRaw。 bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="aaaa7-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="aaaa7-118">提供的非官方開放原始碼組建 `SQLCipher` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="aaaa7-119">SQLitePCLRaw。 bundle_green</span><span class="sxs-lookup"><span data-stu-id="aaaa7-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="aaaa7-120">與相同 `bundle_e_sqlite3` ，除非在 iOS 上使用系統 SQLite 程式庫。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="aaaa7-121">SQLitePCLRaw。 bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="aaaa7-121">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="aaaa7-122">使用 `winsqlite3.dll` ，Windows 10 上的系統 SQLite 程式庫。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-122">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="aaaa7-123">SQLitePCLRaw。 bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="aaaa7-123">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="aaaa7-124">使用 `SQLCipher` 來自 Zetetic 的官方組建（不包含）。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-124">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="aaaa7-125">例如，若要使用非官方的開放原始碼組建，請 `SQLCipher` 使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-125">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="aaaa7-126">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="aaaa7-126">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="aaaa7-127">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aaaa7-127">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="aaaa7-128">SQLitePCLRaw 可用的提供者</span><span class="sxs-lookup"><span data-stu-id="aaaa7-128">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="aaaa7-129">當不依賴配套時，您可以使用 SQLite 的可用提供者搭配核心元件。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-129">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="aaaa7-130">提供者</span><span class="sxs-lookup"><span data-stu-id="aaaa7-130">Provider</span></span> | <span data-ttu-id="aaaa7-131">說明</span><span class="sxs-lookup"><span data-stu-id="aaaa7-131">Description</span></span> |
|--|--|
| [<span data-ttu-id="aaaa7-132">SQLitePCLRaw。 dynamic</span><span class="sxs-lookup"><span data-stu-id="aaaa7-132">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="aaaa7-133">`dynamic`提供者會載入原生程式庫，而不是使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-133">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="aaaa7-134">如需使用此提供者的詳細資訊，請參閱[使用動態提供者](#use-the-dynamic-provider)。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-134">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="aaaa7-135">SQLitePCLRaw。 e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="aaaa7-135">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="aaaa7-136">`e_sqlite3`是預設提供者。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-136">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="aaaa7-137">SQLitePCLRaw。 e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="aaaa7-137">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="aaaa7-138">`e_sqlcipher`提供者是非官方和不支援的 `SQLCipher` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-138">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="aaaa7-139">SQLitePCLRaw. provider. db.sqlite3</span><span class="sxs-lookup"><span data-stu-id="aaaa7-139">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="aaaa7-140">`sqlite3`提供者是 `SQLite` 針對 IOS、MacOS 和 Linux 提供的系統。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-140">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="aaaa7-141">SQLitePCLRaw. provider. sqlcipher</span><span class="sxs-lookup"><span data-stu-id="aaaa7-141">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="aaaa7-142">`sqlcipher`提供者是來自的官方 `SQLCipher` 組建 `Zetetic` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-142">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="aaaa7-143">SQLitePCLRaw. provider. winsqlite3</span><span class="sxs-lookup"><span data-stu-id="aaaa7-143">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="aaaa7-144">`winsqlite3`提供者適用于 Windows 10 環境。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-144">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="aaaa7-145">若要使用 `sqlite3` 提供者，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="aaaa7-145">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="aaaa7-146">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="aaaa7-146">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="aaaa7-147">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aaaa7-147">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="aaaa7-148">安裝封裝之後，您就可以將提供者設定為 `sqlite3` 實例。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-148">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="aaaa7-149">使用動態提供者</span><span class="sxs-lookup"><span data-stu-id="aaaa7-149">Use the dynamic provider</span></span>

<span data-ttu-id="aaaa7-150">您可以利用套件來使用自己的 SQLite 組建 `SQLitePCLRaw.provider.dynamic_cdecl` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-150">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="aaaa7-151">在此情況下，您必須負責使用您的應用程式來部署原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-151">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="aaaa7-152">請注意，使用您的應用程式部署原生程式庫的詳細資料，會根據您所使用的 .NET 平臺和執行時間而有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-152">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="aaaa7-153">首先，您必須執行 `IGetFunctionPointer` 。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-153">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="aaaa7-154">.NET Core 上的實作為如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaaa7-154">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="aaaa7-155">接下來，設定 `SQLitePCLRaw` 提供者。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-155">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="aaaa7-156">請確定已 `Microsoft.Data.Sqlite` 在應用程式中使用之前完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-156">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="aaaa7-157">此外，請避免使用 `SQLitePCLRaw` 可能會覆寫您提供者的組合套件。</span><span class="sxs-lookup"><span data-stu-id="aaaa7-157">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
