---
title: 全球化和 ICU
ms.date: 05/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: 6ea848d4a60069e6702b9d60fd90a55f572fb043
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842524"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="169e7-102">.NET 全球化和 ICU</span><span class="sxs-lookup"><span data-stu-id="169e7-102">.NET globalization and ICU</span></span>

<span data-ttu-id="169e7-103">在過去，.NET 全球化 Api 在不同平臺上使用不同的基礎程式庫。</span><span class="sxs-lookup"><span data-stu-id="169e7-103">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="169e7-104">在 Unix 上，Api 使用了[Unicode （ICU）的國際元件](http://site.icu-project.org/home)，而在 Windows 上則使用了[國家語言支援（NLS）](/windows/win32/intl/national-language-support)。</span><span class="sxs-lookup"><span data-stu-id="169e7-104">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="169e7-105">這會導致在不同平臺上執行應用程式時，少數全球化 Api 中有一些行為上的差異。</span><span class="sxs-lookup"><span data-stu-id="169e7-105">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="169e7-106">在這些區域中，行為差異很明顯：</span><span class="sxs-lookup"><span data-stu-id="169e7-106">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="169e7-107">文化特性和文化特性資料</span><span class="sxs-lookup"><span data-stu-id="169e7-107">Cultures and culture data</span></span>
- <span data-ttu-id="169e7-108">字串大小寫</span><span class="sxs-lookup"><span data-stu-id="169e7-108">String casing</span></span>
- <span data-ttu-id="169e7-109">字串排序和搜尋</span><span class="sxs-lookup"><span data-stu-id="169e7-109">String sorting and searching</span></span>
- <span data-ttu-id="169e7-110">排序索引鍵</span><span class="sxs-lookup"><span data-stu-id="169e7-110">Sort keys</span></span>
- <span data-ttu-id="169e7-111">字串正規化</span><span class="sxs-lookup"><span data-stu-id="169e7-111">String normalization</span></span>
- <span data-ttu-id="169e7-112">國際化功能變數名稱（IDN）支援</span><span class="sxs-lookup"><span data-stu-id="169e7-112">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="169e7-113">Linux 上的時區顯示名稱</span><span class="sxs-lookup"><span data-stu-id="169e7-113">Time zone display name on Linux</span></span>

<span data-ttu-id="169e7-114">從 .NET 5.0 開始，開發人員可以更充分掌控使用的基礎程式庫，讓應用程式可以避免跨平臺的差異。</span><span class="sxs-lookup"><span data-stu-id="169e7-114">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="169e7-115">Windows 上的 ICU</span><span class="sxs-lookup"><span data-stu-id="169e7-115">ICU on Windows</span></span>

<span data-ttu-id="169e7-116">Windows 10 2019 版的更新和更新版本包含[icu .dll](/windows/win32/intl/international-components-for-unicode--icu-)做為作業系統的一部分，而且 .net 5.0 和更新版本預設會使用 icu。</span><span class="sxs-lookup"><span data-stu-id="169e7-116">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="169e7-117">在 Windows 上執行時，.NET 5.0 和更新版本會嘗試載入， `icu.dll` 如果可用，則會將它用於全球化執行。</span><span class="sxs-lookup"><span data-stu-id="169e7-117">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and if it's available, uses it for the globalization implementation.</span></span>  <span data-ttu-id="169e7-118">如果找不到或無法載入該程式庫（例如在舊版 Windows 上執行時），則 .NET 5.0 和更新版本會回到 NLS 型的實作為基礎。</span><span class="sxs-lookup"><span data-stu-id="169e7-118">If that library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="169e7-119">即使在使用 ICU 時， `CurrentCulture` 、 `CurrentUICulture` 和 `CurrentRegion` 成員仍然會使用 Windows 作業系統 api 來接受使用者設定。</span><span class="sxs-lookup"><span data-stu-id="169e7-119">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="using-nls-instead-of-icu"></a><span data-ttu-id="169e7-120">使用 NLS 而非 ICU</span><span class="sxs-lookup"><span data-stu-id="169e7-120">Using NLS instead of ICU</span></span>

<span data-ttu-id="169e7-121">使用 ICU 而不是 NLS，可能會導致與一些全球化相關作業的行為差異。</span><span class="sxs-lookup"><span data-stu-id="169e7-121">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="169e7-122">若要還原回使用 NLS，開發人員可以退出宣告 ICU 的執行。</span><span class="sxs-lookup"><span data-stu-id="169e7-122">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="169e7-123">應用程式可以使用下列任何方式來啟用 NLS 模式：</span><span class="sxs-lookup"><span data-stu-id="169e7-123">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="169e7-124">在專案檔中：</span><span class="sxs-lookup"><span data-stu-id="169e7-124">In the project file:</span></span>

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
</ItemGroup>
```

- <span data-ttu-id="169e7-125">在 `runtimeconfig.json` 檔案中：</span><span class="sxs-lookup"><span data-stu-id="169e7-125">In the `runtimeconfig.json` file:</span></span>

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.UseNls": true
      }
  }
}
```

- <span data-ttu-id="169e7-126">藉由將環境變數設定 `DOTNET_SYSTEM_GLOBALIZATION_USENLS` 為 `true` 或值 `1` 。</span><span class="sxs-lookup"><span data-stu-id="169e7-126">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="169e7-127">在專案或檔案中設定的值 `runtimeconfig.json` 優先于環境變數。</span><span class="sxs-lookup"><span data-stu-id="169e7-127">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="169e7-128">如需詳細資訊，請參閱[執行時間配置設定](../../core/run-time-config/globalization.md#nls)。</span><span class="sxs-lookup"><span data-stu-id="169e7-128">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="169e7-129">應用程式-本機 ICU</span><span class="sxs-lookup"><span data-stu-id="169e7-129">App-local ICU</span></span>

<span data-ttu-id="169e7-130">每一版的 ICU 都可能引進 it 錯誤修正，並更新通用地區設定資料存放庫（CLDR）資料，以描述世界的語言。</span><span class="sxs-lookup"><span data-stu-id="169e7-130">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="169e7-131">在不同版本的 ICU 之間移動，可能會對全球化相關作業的應用程式行為有細微的影響。</span><span class="sxs-lookup"><span data-stu-id="169e7-131">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span>  <span data-ttu-id="169e7-132">為了協助應用程式開發人員確保所有部署的一致性，.NET 5.0 和更新版本可讓 Windows 和 Unix 上的應用程式攜帶和使用自己的 ICU 複本。</span><span class="sxs-lookup"><span data-stu-id="169e7-132">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="169e7-133">應用程式可以使用下列任何一種方式，加入宣告應用程式本機的 ICU 執行模式：</span><span class="sxs-lookup"><span data-stu-id="169e7-133">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="169e7-134">在專案檔中：</span><span class="sxs-lookup"><span data-stu-id="169e7-134">In  the project file:</span></span>

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
</ItemGroup>
```

- <span data-ttu-id="169e7-135">在 `runtimeconfig.json` 檔案中：</span><span class="sxs-lookup"><span data-stu-id="169e7-135">In the `runtimeconfig.json` file:</span></span>

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
      }
  }
}
```

- <span data-ttu-id="169e7-136">藉由將環境變數設定 `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` 為 `<suffix>:<version>` 或值 `<version>` 。</span><span class="sxs-lookup"><span data-stu-id="169e7-136">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

<span data-ttu-id="169e7-137">`<suffix>`：長度小於36個字元的選擇性尾碼，遵循公用的 ICU 封裝慣例。</span><span class="sxs-lookup"><span data-stu-id="169e7-137">`<suffix>`: Optional suffix of less than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="169e7-138">當您建立自訂的 ICU 時，您可以自訂它以產生 lib 名稱和匯出的符號名稱以包含尾碼，例如， `libicuucmyapp` ，其中 `myapp` 是尾碼。</span><span class="sxs-lookup"><span data-stu-id="169e7-138">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

<span data-ttu-id="169e7-139">`<version>`：有效的 ICU 版本，例如67.1。</span><span class="sxs-lookup"><span data-stu-id="169e7-139">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="169e7-140">這個版本是用來載入二進位檔，並取得匯出的符號。</span><span class="sxs-lookup"><span data-stu-id="169e7-140">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="169e7-141">若要在設定應用程式本機參數時載入 ICU，.NET 會使用 <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> 方法來探查多個路徑。</span><span class="sxs-lookup"><span data-stu-id="169e7-141">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="169e7-142">方法會先嘗試在屬性中尋找程式庫 `NATIVE_DLL_SEARCH_DIRECTORIES` ，這是由 dotnet 主機根據應用程式的檔案所建立 `deps.json` 。</span><span class="sxs-lookup"><span data-stu-id="169e7-142">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="169e7-143">如需詳細資訊，請參閱[預設探查](../../core/dependency-loading/default-probing.md)。</span><span class="sxs-lookup"><span data-stu-id="169e7-143">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="169e7-144">針對獨立應用程式，使用者不需要採取任何特殊動作，除了確定 ICU 是在應用程式目錄中（針對獨立式應用程式，工作目錄預設為 `NATIVE_DLL_SEARCH_DIRECTORIES` ）。</span><span class="sxs-lookup"><span data-stu-id="169e7-144">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="169e7-145">如果您是透過 NuGet 套件取用 ICU，這適用于架構相依的應用程式。</span><span class="sxs-lookup"><span data-stu-id="169e7-145">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="169e7-146">NuGet 會解析原生資產，並將它們包含在檔案 `deps.json` 和目錄下之應用程式的輸出目錄中 `runtimes` 。</span><span class="sxs-lookup"><span data-stu-id="169e7-146">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="169e7-147">.NET 會從該處載入它。</span><span class="sxs-lookup"><span data-stu-id="169e7-147">.NET loads it from there.</span></span>

<span data-ttu-id="169e7-148">針對從本機組建取用 ICU 的 framework 相依應用程式（非獨立），您必須採取額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="169e7-148">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="169e7-149">.NET SDK 尚未有「鬆散」的原生二進位檔要併入的功能 `deps.json` （請參閱[此 SDK 問題](https://github.com/dotnet/sdk/issues/11373)）。</span><span class="sxs-lookup"><span data-stu-id="169e7-149">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="169e7-150">相反地，您可以藉由在應用程式的專案檔中新增其他資訊來啟用此項。</span><span class="sxs-lookup"><span data-stu-id="169e7-150">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="169e7-151">例如：</span><span class="sxs-lookup"><span data-stu-id="169e7-151">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="169e7-152">這必須針對支援的執行時間的所有 ICU 二進位檔來完成。</span><span class="sxs-lookup"><span data-stu-id="169e7-152">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="169e7-153">此外， `NuGetPackageId` 專案群組中的中繼資料 `RuntimeTargetsCopyLocalItems` 必須符合專案實際所參考的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="169e7-153">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="169e7-154">macOS 行為</span><span class="sxs-lookup"><span data-stu-id="169e7-154">macOS behavior</span></span>

<span data-ttu-id="169e7-155">`macOS`具有不同的行為，可從檔案中指定的載入命令（ `match-o` 而非 Linux 載入器）解析相依的動態連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="169e7-155">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="169e7-156">在 Linux 載入器中，.NET 可以嘗試 `libicudata` 、 `libicuuc` 和 `libicui18n` （依此順序）來滿足 ICU 相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="169e7-156">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="169e7-157">不過，在 macOS 上，這不會有作用。</span><span class="sxs-lookup"><span data-stu-id="169e7-157">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="169e7-158">在 macOS 上建立 ICU 時，根據預設，您會在中使用這些載入命令來取得動態連結程式庫 `libicuuc` 。</span><span class="sxs-lookup"><span data-stu-id="169e7-158">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="169e7-159">例如：</span><span class="sxs-lookup"><span data-stu-id="169e7-159">For example.:</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="169e7-160">這些命令只會參考 ICU 其他元件的相依程式庫名稱。</span><span class="sxs-lookup"><span data-stu-id="169e7-160">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="169e7-161">載入器會依照慣例執行搜尋 `dlopen` ，這牽涉到在系統目錄中擁有這些程式庫或設定 `LD_LIBRARY_PATH` env 變數，或在應用層級目錄中擁有 ICU。</span><span class="sxs-lookup"><span data-stu-id="169e7-161">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="169e7-162">如果您無法設定 `LD_LIBRARY_PATH` 或確定 ICU 二進位檔位於應用層級目錄，您將需要執行一些額外的工作。</span><span class="sxs-lookup"><span data-stu-id="169e7-162">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="169e7-163">載入器有一些指示詞，例如 `@loader_path` ，它會告知載入器使用該載入命令，在與二進位檔相同的目錄中搜尋該相依性。</span><span class="sxs-lookup"><span data-stu-id="169e7-163">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="169e7-164">作法有二：</span><span class="sxs-lookup"><span data-stu-id="169e7-164">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="169e7-165">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="169e7-165">Run the following commands:</span></span>

```bash
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
```

- <span data-ttu-id="169e7-166">修補 ICU 以產生安裝名稱`@loader_path`</span><span class="sxs-lookup"><span data-stu-id="169e7-166">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="169e7-167">執行 autoconf （ `./runConfigureICU` ）之前，請將[下列幾行](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37)變更為：</span><span class="sxs-lookup"><span data-stu-id="169e7-167">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

```
LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
```
