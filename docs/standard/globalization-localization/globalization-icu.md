---
title: 全球化與 ICU
ms.date: 05/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- globalization [.NET], about globalization
- global applications, globalization
- international applications [.NET], globalization
- world-ready applications, globalization
- application development [.NET], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: e0ca78871d1ddf851148096c8c6cfd10076763ab
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400875"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="027a8-102">.NET 全球化和 ICU</span><span class="sxs-lookup"><span data-stu-id="027a8-102">.NET globalization and ICU</span></span>

<span data-ttu-id="027a8-103">在過去，.NET 全球化 Api 在不同的平臺上使用不同的基礎程式庫。</span><span class="sxs-lookup"><span data-stu-id="027a8-103">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="027a8-104">在 Unix 上，Api 使用了 [Unicode (ICU) 的國際元件 ](http://site.icu-project.org/home)，而在 Windows 上則是使用 [國家語言支援 (NLS) ](/windows/win32/intl/national-language-support)。</span><span class="sxs-lookup"><span data-stu-id="027a8-104">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="027a8-105">這會導致在不同平臺上執行應用程式時，少數的全球化 Api 有一些行為差異。</span><span class="sxs-lookup"><span data-stu-id="027a8-105">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="027a8-106">這些方面的行為差異很明顯：</span><span class="sxs-lookup"><span data-stu-id="027a8-106">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="027a8-107">文化特性和文化特性資料</span><span class="sxs-lookup"><span data-stu-id="027a8-107">Cultures and culture data</span></span>
- <span data-ttu-id="027a8-108">字串大小寫</span><span class="sxs-lookup"><span data-stu-id="027a8-108">String casing</span></span>
- <span data-ttu-id="027a8-109">字串排序和搜尋</span><span class="sxs-lookup"><span data-stu-id="027a8-109">String sorting and searching</span></span>
- <span data-ttu-id="027a8-110">排序索引鍵</span><span class="sxs-lookup"><span data-stu-id="027a8-110">Sort keys</span></span>
- <span data-ttu-id="027a8-111">字串正規化</span><span class="sxs-lookup"><span data-stu-id="027a8-111">String normalization</span></span>
- <span data-ttu-id="027a8-112"> (IDN) 支援的國際化功能變數名稱</span><span class="sxs-lookup"><span data-stu-id="027a8-112">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="027a8-113">Linux 上的時區顯示名稱</span><span class="sxs-lookup"><span data-stu-id="027a8-113">Time zone display name on Linux</span></span>

<span data-ttu-id="027a8-114">從 .NET 5.0 開始，開發人員可以更充分掌控使用的基礎程式庫，讓應用程式得以避免不同平臺之間的差異。</span><span class="sxs-lookup"><span data-stu-id="027a8-114">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="027a8-115">Windows 上的 ICU</span><span class="sxs-lookup"><span data-stu-id="027a8-115">ICU on Windows</span></span>

<span data-ttu-id="027a8-116">Windows 10 2019 年5月更新和更新版本包含 [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) 作為作業系統的一部分，而 .net 5.0 和更新版本預設會使用 ICU。</span><span class="sxs-lookup"><span data-stu-id="027a8-116">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="027a8-117">在 Windows 上執行時，.NET 5.0 和更新版本會嘗試載入，如果有的話，請 `icu.dll` 將它用於全球化執行。</span><span class="sxs-lookup"><span data-stu-id="027a8-117">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and, if it's available, use it for the globalization implementation.</span></span> <span data-ttu-id="027a8-118">如果找不到或無法載入 ICU 程式庫（例如在舊版 Windows 上執行時），則 .NET 5.0 和更新版本會切換回以 NLS 為基礎的實作為。</span><span class="sxs-lookup"><span data-stu-id="027a8-118">If the ICU library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="027a8-119">即使使用 ICU， `CurrentCulture` 、 `CurrentUICulture` 和 `CurrentRegion` 成員仍會使用 Windows 作業系統 api 來接受使用者設定。</span><span class="sxs-lookup"><span data-stu-id="027a8-119">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="use-nls-instead-of-icu"></a><span data-ttu-id="027a8-120">使用 NLS 而非 ICU</span><span class="sxs-lookup"><span data-stu-id="027a8-120">Use NLS instead of ICU</span></span>

<span data-ttu-id="027a8-121">使用 ICU 而非 NLS，可能會導致與一些全球化相關作業的行為有所差異。</span><span class="sxs-lookup"><span data-stu-id="027a8-121">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="027a8-122">若要還原回使用 NLS，開發人員可以退出宣告 ICU 的執行。</span><span class="sxs-lookup"><span data-stu-id="027a8-122">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="027a8-123">應用程式可以使用下列任何一種方式來啟用 NLS 模式：</span><span class="sxs-lookup"><span data-stu-id="027a8-123">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="027a8-124">在專案檔中：</span><span class="sxs-lookup"><span data-stu-id="027a8-124">In the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="027a8-125">在 `runtimeconfig.json` 檔案中：</span><span class="sxs-lookup"><span data-stu-id="027a8-125">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.UseNls": true
        }
    }
  }
  ```

- <span data-ttu-id="027a8-126">將環境變數設定 `DOTNET_SYSTEM_GLOBALIZATION_USENLS` 為值 `true` 或 `1` 。</span><span class="sxs-lookup"><span data-stu-id="027a8-126">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="027a8-127">在專案或檔案中設定的值 `runtimeconfig.json` 會優先于環境變數。</span><span class="sxs-lookup"><span data-stu-id="027a8-127">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="027a8-128">如需詳細資訊，請參閱 [執行時間配置設定](../../core/run-time-config/globalization.md#nls)。</span><span class="sxs-lookup"><span data-stu-id="027a8-128">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="027a8-129">應用程式本機 ICU</span><span class="sxs-lookup"><span data-stu-id="027a8-129">App-local ICU</span></span>

<span data-ttu-id="027a8-130">每一版的 ICU 都可能帶來 it bug 修正，以及更新的一般地區設定資料存放庫 (CLDR 描述世界語言的) 資料。</span><span class="sxs-lookup"><span data-stu-id="027a8-130">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="027a8-131">在不同版本的 ICU 之間移動時，在與全球化相關的作業時，可能會對應用程式行為產生細微的影響</span><span class="sxs-lookup"><span data-stu-id="027a8-131">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span> <span data-ttu-id="027a8-132">為了協助應用程式開發人員確保所有部署之間的一致性，.NET 5.0 和更新版本可讓 Windows 和 Unix 上的應用程式執行並使用自己的 ICU 複本。</span><span class="sxs-lookup"><span data-stu-id="027a8-132">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="027a8-133">應用程式可以使用下列任何一種方式，選擇進入應用程式本機的 ICU 真實模式：</span><span class="sxs-lookup"><span data-stu-id="027a8-133">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="027a8-134">在專案檔中：</span><span class="sxs-lookup"><span data-stu-id="027a8-134">In  the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
  </ItemGroup>
  ```

- <span data-ttu-id="027a8-135">在 `runtimeconfig.json` 檔案中：</span><span class="sxs-lookup"><span data-stu-id="027a8-135">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
       }
    }
  }
  ```

- <span data-ttu-id="027a8-136">將環境變數設定 `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` 為值 `<suffix>:<version>` 或 `<version>` 。</span><span class="sxs-lookup"><span data-stu-id="027a8-136">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

  <span data-ttu-id="027a8-137">`<suffix>`：選擇性尾碼的長度少於36個字元，請遵循 public ICU 封裝慣例。</span><span class="sxs-lookup"><span data-stu-id="027a8-137">`<suffix>`: Optional suffix of fewer than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="027a8-138">當您建立自訂的 ICU 時，您可以自訂它來產生 lib 名稱和匯出的符號名稱，以包含尾碼，例如， `libicuucmyapp` 其中 `myapp` 是尾碼。</span><span class="sxs-lookup"><span data-stu-id="027a8-138">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

  <span data-ttu-id="027a8-139">`<version>`：有效的 ICU 版本，例如67.1。</span><span class="sxs-lookup"><span data-stu-id="027a8-139">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="027a8-140">此版本是用來載入二進位檔，並取得匯出的符號。</span><span class="sxs-lookup"><span data-stu-id="027a8-140">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="027a8-141">若要在設定應用程式本機參數時載入 ICU，.NET 會使用 <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> 探查多個路徑的方法。</span><span class="sxs-lookup"><span data-stu-id="027a8-141">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="027a8-142">方法會先嘗試在屬性中尋找程式庫 `NATIVE_DLL_SEARCH_DIRECTORIES` ，此屬性是由 dotnet 主機根據應用程式的檔案所建立 `deps.json` 。</span><span class="sxs-lookup"><span data-stu-id="027a8-142">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="027a8-143">如需詳細資訊，請參閱 [預設探查](../../core/dependency-loading/default-probing.md)。</span><span class="sxs-lookup"><span data-stu-id="027a8-143">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="027a8-144">針對獨立應用程式，使用者不需要採取任何特殊動作，除了確定 ICU 是在獨立應用程式的應用程式目錄 (中，工作目錄預設為 `NATIVE_DLL_SEARCH_DIRECTORIES`) 。</span><span class="sxs-lookup"><span data-stu-id="027a8-144">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="027a8-145">如果您是透過 NuGet 套件來取用 ICU，這會在與 framework 相依的應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="027a8-145">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="027a8-146">NuGet 會解析原生資產，並將它們包含在檔案中，並將其包含在 `deps.json` 目錄的應用程式的輸出目錄中 `runtimes` 。</span><span class="sxs-lookup"><span data-stu-id="027a8-146">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="027a8-147">.NET 會從該處載入它。</span><span class="sxs-lookup"><span data-stu-id="027a8-147">.NET loads it from there.</span></span>

<span data-ttu-id="027a8-148">針對與 framework 相依的應用程式， (不是自主) 從本機組建取用 ICU 的情況下，您必須採取額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="027a8-148">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="027a8-149">.NET SDK 尚未提供「鬆散」原生二進位檔的功能，可將其併入 `deps.json` (請參閱 [此 SDK 問題](https://github.com/dotnet/sdk/issues/11373)) 。</span><span class="sxs-lookup"><span data-stu-id="027a8-149">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="027a8-150">相反地，您可以藉由在應用程式的專案檔中新增其他資訊來啟用此專案。</span><span class="sxs-lookup"><span data-stu-id="027a8-150">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="027a8-151">例如︰</span><span class="sxs-lookup"><span data-stu-id="027a8-151">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="027a8-152">這必須針對支援執行時間的所有 ICU 二進位檔進行。</span><span class="sxs-lookup"><span data-stu-id="027a8-152">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="027a8-153">此外， `NuGetPackageId` 專案群組中的中繼資料 `RuntimeTargetsCopyLocalItems` 必須符合專案實際參考的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="027a8-153">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="027a8-154">macOS 行為</span><span class="sxs-lookup"><span data-stu-id="027a8-154">macOS behavior</span></span>

<span data-ttu-id="027a8-155">`macOS` 有不同的行為，可從檔案中指定的載入命令（ `match-o` 而不是 Linux 載入器）解析相依的動態連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="027a8-155">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="027a8-156">在 Linux 載入器中，.NET 可以 `libicudata` `libicuuc` `libicui18n` 依該順序嘗試、和 () 來滿足 ICU 相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="027a8-156">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="027a8-157">不過，在 macOS 上，這無法運作。</span><span class="sxs-lookup"><span data-stu-id="027a8-157">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="027a8-158">在 macOS 上建立 ICU 時，根據預設，會在中使用這些載入命令來取得動態連結程式庫 `libicuuc` 。</span><span class="sxs-lookup"><span data-stu-id="027a8-158">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="027a8-159">下列程式碼片段顯示範例。</span><span class="sxs-lookup"><span data-stu-id="027a8-159">The following snippet shows an example.</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="027a8-160">這些命令只會參考其他 ICU 元件的相依程式庫名稱。</span><span class="sxs-lookup"><span data-stu-id="027a8-160">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="027a8-161">載入器會依照慣例執行搜尋 `dlopen` ，其牽涉到將這些程式庫安裝在系統目錄中或設定 `LD_LIBRARY_PATH` env 變數，或在應用層級目錄中具有 ICU。</span><span class="sxs-lookup"><span data-stu-id="027a8-161">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="027a8-162">如果您無法設定 `LD_LIBRARY_PATH` 或確定 ICU 二進位檔是在應用層級目錄，您需要執行一些額外的工作。</span><span class="sxs-lookup"><span data-stu-id="027a8-162">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="027a8-163">載入器有一些指示詞，例如 `@loader_path` ，它會指示載入器使用該 load 命令，在與二進位檔相同的目錄中搜尋該相依性。</span><span class="sxs-lookup"><span data-stu-id="027a8-163">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="027a8-164">作法有二：</span><span class="sxs-lookup"><span data-stu-id="027a8-164">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="027a8-165">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="027a8-165">Run the following commands:</span></span>

  ```bash
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
  install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
  ```

- <span data-ttu-id="027a8-166">修補 ICU 以產生安裝名稱 `@loader_path`</span><span class="sxs-lookup"><span data-stu-id="027a8-166">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="027a8-167">在執行 autoconf (`./runConfigureICU`) 之前，請將 [下列幾行](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) 變更為：</span><span class="sxs-lookup"><span data-stu-id="027a8-167">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

  ```
  LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
  ```

## <a name="icu-on-webassembly"></a><span data-ttu-id="027a8-168">WebAssembly 上的 ICU</span><span class="sxs-lookup"><span data-stu-id="027a8-168">ICU on WebAssembly</span></span>

<span data-ttu-id="027a8-169">您可以針對 WebAssembly 的工作負載取得 ICU 的版本。</span><span class="sxs-lookup"><span data-stu-id="027a8-169">A version of ICU is available that's specifically for WebAssembly workloads.</span></span> <span data-ttu-id="027a8-170">此版本提供與桌面設定檔的全球化相容性。</span><span class="sxs-lookup"><span data-stu-id="027a8-170">This version provides globalization compatibility with desktop profiles.</span></span> <span data-ttu-id="027a8-171">若要將 ICU 資料檔案大小從 24 MB 減少為 1.4 MB (或 ~ 0.3 MB （如果使用 Brotli) 壓縮的話），此工作負載有少數的限制。</span><span class="sxs-lookup"><span data-stu-id="027a8-171">To reduce the ICU data file size from 24 MB to 1.4 MB (or ~0.3 MB if compressed with Brotli), this workload has a handful of limitations.</span></span>

<span data-ttu-id="027a8-172">不支援下列 Api：</span><span class="sxs-lookup"><span data-stu-id="027a8-172">The following APIs are not supported:</span></span>

- <xref:System.Globalization.CultureInfo.EnglishName?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.NativeName?displayProperty=nameWithType>
- <xref:System.Globalization.DateTimeFormatInfo.NativeCalendarName?displayProperty=nameWithType>
- <xref:System.Globalization.RegionInfo.NativeName?displayProperty=nameWithType>

<span data-ttu-id="027a8-173">以下是支援的 Api，其限制如下：</span><span class="sxs-lookup"><span data-stu-id="027a8-173">The following APIs are supported with limitations:</span></span>

- <span data-ttu-id="027a8-174"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> 而且 <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> 不支援很少使用 <xref:System.Text.NormalizationForm.FormKC> 和 <xref:System.Text.NormalizationForm.FormKD> 表單。</span><span class="sxs-lookup"><span data-stu-id="027a8-174"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> and <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> don't support the rarely used <xref:System.Text.NormalizationForm.FormKC> and <xref:System.Text.NormalizationForm.FormKD> forms.</span></span>
- <span data-ttu-id="027a8-175"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> 會傳回與 <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType> 相同的值。</span><span class="sxs-lookup"><span data-stu-id="027a8-175"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> returns the same value as <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="027a8-176">此外，您可以在 [dotnet/icu](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54)存放庫中找到支援的地區設定清單。</span><span class="sxs-lookup"><span data-stu-id="027a8-176">In addition, a list of supported locales can be found on the [dotnet/icu repo](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span></span>
