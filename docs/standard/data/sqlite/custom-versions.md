---
title: 自訂 SQLite 版本
ms.date: 09/04/2020
description: 瞭解如何使用原生 SQLite 程式庫的自訂版本。
ms.openlocfilehash: fbf4b4cd33e6e890ce0c0cfe0b7688487b94b4a3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516134"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="aaef7-103">自訂 SQLite 版本</span><span class="sxs-lookup"><span data-stu-id="aaef7-103">Custom SQLite versions</span></span>

<span data-ttu-id="aaef7-104">`Microsoft.Data.Sqlite` 建置於之上 `SQLitePCLRaw` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="aaef7-105">您可以使用套件組合或設定提供者，來使用原生 SQLite 程式庫的自訂版本 `SQLitePCLRaw` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="aaef7-106">束</span><span class="sxs-lookup"><span data-stu-id="aaef7-106">Bundles</span></span>

<span data-ttu-id="aaef7-107">`SQLitePCLRaw` 提供便利的套件組合套件，可讓您輕鬆地在不同平臺上帶入正確的相依性。</span><span class="sxs-lookup"><span data-stu-id="aaef7-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="aaef7-108">`Microsoft.Data.Sqlite`依預設，主要套件會帶入 `SQLitePCLRaw.bundle_e_sqlite3` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="aaef7-109">若要使用不同的配套，請 `Microsoft.Data.Sqlite.Core` 改為安裝套件，以及您想要使用的套件組合套件。</span><span class="sxs-lookup"><span data-stu-id="aaef7-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="aaef7-110">組合會由自動初始化 `Microsoft.Data.Sqlite` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="aaef7-111">套件組合</span><span class="sxs-lookup"><span data-stu-id="aaef7-111">Bundle</span></span> | <span data-ttu-id="aaef7-112">描述</span><span class="sxs-lookup"><span data-stu-id="aaef7-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="aaef7-113">SQLitePCLRaw。 bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="aaef7-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="aaef7-114">在所有平臺上都提供一致版本的 SQLite。</span><span class="sxs-lookup"><span data-stu-id="aaef7-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="aaef7-115">包含 FTS4、FTS5、JSON1 和 R \* 樹狀結構擴充。</span><span class="sxs-lookup"><span data-stu-id="aaef7-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="aaef7-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="aaef7-116">This is the default.</span></span> |
| [<span data-ttu-id="aaef7-117">SQLitePCLRaw。 bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="aaef7-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="aaef7-118">提供的非官方、開放原始碼組建 `SQLCipher` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="aaef7-119">SQLitePCLRaw。 bundle_green</span><span class="sxs-lookup"><span data-stu-id="aaef7-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="aaef7-120">與相同 `bundle_e_sqlite3` ，但使用系統 SQLite 程式庫的 iOS 除外。</span><span class="sxs-lookup"><span data-stu-id="aaef7-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="aaef7-121">SQLitePCLRaw。 bundle_sqlite3</span><span class="sxs-lookup"><span data-stu-id="aaef7-121">SQLitePCLRaw.bundle_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_sqlite3) | <span data-ttu-id="aaef7-122">使用系統 SQLite 程式庫。</span><span class="sxs-lookup"><span data-stu-id="aaef7-122">Uses the system SQLite library.</span></span> |
| [<span data-ttu-id="aaef7-123">SQLitePCLRaw。 bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="aaef7-123">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="aaef7-124">使用 `winsqlite3.dll` Windows 10 上的系統 SQLite 程式庫。</span><span class="sxs-lookup"><span data-stu-id="aaef7-124">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="aaef7-125">SQLitePCLRaw。 bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="aaef7-125">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="aaef7-126">使用 `SQLCipher` Zetetic 中的官方組建 (不包含) 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-126">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="aaef7-127">例如，若要使用非官方的開放原始碼組建，請 `SQLCipher` 使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="aaef7-127">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="aaef7-128">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="aaef7-128">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="aaef7-129">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aaef7-129">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="aaef7-130">SQLitePCLRaw 可用提供者</span><span class="sxs-lookup"><span data-stu-id="aaef7-130">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="aaef7-131">如果不依賴套件組合，您可以使用 SQLite 的可用提供者搭配核心元件。</span><span class="sxs-lookup"><span data-stu-id="aaef7-131">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="aaef7-132">提供者</span><span class="sxs-lookup"><span data-stu-id="aaef7-132">Provider</span></span> | <span data-ttu-id="aaef7-133">描述</span><span class="sxs-lookup"><span data-stu-id="aaef7-133">Description</span></span> |
|--|--|
| [<span data-ttu-id="aaef7-134">SQLitePCLRaw： dynamic</span><span class="sxs-lookup"><span data-stu-id="aaef7-134">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="aaef7-135">`dynamic`提供者會載入原生程式庫，而不是使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="aaef7-135">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="aaef7-136">如需使用此提供者的詳細資訊，請參閱 [使用動態提供者](#use-the-dynamic-provider)。</span><span class="sxs-lookup"><span data-stu-id="aaef7-136">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="aaef7-137">SQLitePCLRaw。 e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="aaef7-137">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="aaef7-138">`e_sqlite3`是預設的提供者。</span><span class="sxs-lookup"><span data-stu-id="aaef7-138">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="aaef7-139">SQLitePCLRaw。 e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="aaef7-139">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="aaef7-140">`e_sqlcipher`提供者是非官方且不受支援 `SQLCipher` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-140">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="aaef7-141">SQLitePCLRaw。 >db.sqlite3</span><span class="sxs-lookup"><span data-stu-id="aaef7-141">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="aaef7-142">`sqlite3`提供者是 `SQLite` 適用于 IOS、MacOS 和 Linux 的系統提供的提供者。</span><span class="sxs-lookup"><span data-stu-id="aaef7-142">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="aaef7-143">SQLitePCLRaw。 sqlcipher</span><span class="sxs-lookup"><span data-stu-id="aaef7-143">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="aaef7-144">`sqlcipher`提供者適用于的官方 `SQLCipher` 組建 `Zetetic` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-144">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="aaef7-145">SQLitePCLRaw。 winsqlite3</span><span class="sxs-lookup"><span data-stu-id="aaef7-145">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="aaef7-146">`winsqlite3`提供者適用于 Windows 10 環境。</span><span class="sxs-lookup"><span data-stu-id="aaef7-146">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="aaef7-147">若要使用 `sqlite3` 提供者，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="aaef7-147">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="aaef7-148">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="aaef7-148">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="aaef7-149">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aaef7-149">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="aaef7-150">安裝封裝之後，您就可以將提供者設定為 `sqlite3` 實例。</span><span class="sxs-lookup"><span data-stu-id="aaef7-150">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="aaef7-151">使用動態提供者</span><span class="sxs-lookup"><span data-stu-id="aaef7-151">Use the dynamic provider</span></span>

<span data-ttu-id="aaef7-152">您可以利用封裝，使用自己的 SQLite 組建 `SQLitePCLRaw.provider.dynamic_cdecl` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-152">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="aaef7-153">在此情況下，您必須負責使用您的應用程式部署原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="aaef7-153">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="aaef7-154">請注意，使用您的應用程式部署原生程式庫的詳細資料，會根據您所使用的 .NET 平臺和執行時間而有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="aaef7-154">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="aaef7-155">首先，您必須實行 `IGetFunctionPointer` 。</span><span class="sxs-lookup"><span data-stu-id="aaef7-155">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="aaef7-156">.NET Core 上的實作為如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaef7-156">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="aaef7-157">接下來，設定 `SQLitePCLRaw` 提供者。</span><span class="sxs-lookup"><span data-stu-id="aaef7-157">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="aaef7-158">請確定這是在 `Microsoft.Data.Sqlite` 應用程式中使用之前完成的。</span><span class="sxs-lookup"><span data-stu-id="aaef7-158">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="aaef7-159">此外，請避免使用 `SQLitePCLRaw` 可能會覆寫您的提供者的套件組合套件。</span><span class="sxs-lookup"><span data-stu-id="aaef7-159">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
