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
# <a name="net-globalization-and-icu"></a>.NET 全球化和 ICU

在過去，.NET 全球化 Api 在不同平臺上使用不同的基礎程式庫。 在 Unix 上，Api 使用了[Unicode （ICU）的國際元件](http://site.icu-project.org/home)，而在 Windows 上則使用了[國家語言支援（NLS）](/windows/win32/intl/national-language-support)。 這會導致在不同平臺上執行應用程式時，少數全球化 Api 中有一些行為上的差異。 在這些區域中，行為差異很明顯：

- 文化特性和文化特性資料
- 字串大小寫
- 字串排序和搜尋
- 排序索引鍵
- 字串正規化
- 國際化功能變數名稱（IDN）支援
- Linux 上的時區顯示名稱

從 .NET 5.0 開始，開發人員可以更充分掌控使用的基礎程式庫，讓應用程式可以避免跨平臺的差異。

## <a name="icu-on-windows"></a>Windows 上的 ICU

Windows 10 2019 版的更新和更新版本包含[icu .dll](/windows/win32/intl/international-components-for-unicode--icu-)做為作業系統的一部分，而且 .net 5.0 和更新版本預設會使用 icu。 在 Windows 上執行時，.NET 5.0 和更新版本會嘗試載入， `icu.dll` 如果可用，則會將它用於全球化執行。  如果找不到或無法載入該程式庫（例如在舊版 Windows 上執行時），則 .NET 5.0 和更新版本會回到 NLS 型的實作為基礎。

> [!NOTE]
> 即使在使用 ICU 時， `CurrentCulture` 、 `CurrentUICulture` 和 `CurrentRegion` 成員仍然會使用 Windows 作業系統 api 來接受使用者設定。

### <a name="using-nls-instead-of-icu"></a>使用 NLS 而非 ICU

使用 ICU 而不是 NLS，可能會導致與一些全球化相關作業的行為差異。 若要還原回使用 NLS，開發人員可以退出宣告 ICU 的執行。 應用程式可以使用下列任何方式來啟用 NLS 模式：

- 在專案檔中：

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
</ItemGroup>
```

- 在 `runtimeconfig.json` 檔案中：

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.UseNls": true
      }
  }
}
```

- 藉由將環境變數設定 `DOTNET_SYSTEM_GLOBALIZATION_USENLS` 為 `true` 或值 `1` 。

> [!NOTE]
> 在專案或檔案中設定的值 `runtimeconfig.json` 優先于環境變數。

如需詳細資訊，請參閱[執行時間配置設定](../../core/run-time-config/globalization.md#nls)。

## <a name="app-local-icu"></a>應用程式-本機 ICU

每一版的 ICU 都可能引進 it 錯誤修正，並更新通用地區設定資料存放庫（CLDR）資料，以描述世界的語言。 在不同版本的 ICU 之間移動，可能會對全球化相關作業的應用程式行為有細微的影響。  為了協助應用程式開發人員確保所有部署的一致性，.NET 5.0 和更新版本可讓 Windows 和 Unix 上的應用程式攜帶和使用自己的 ICU 複本。

應用程式可以使用下列任何一種方式，加入宣告應用程式本機的 ICU 執行模式：

- 在專案檔中：

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
</ItemGroup>
```

- 在 `runtimeconfig.json` 檔案中：

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
      }
  }
}
```

- 藉由將環境變數設定 `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` 為 `<suffix>:<version>` 或值 `<version>` 。

`<suffix>`：長度小於36個字元的選擇性尾碼，遵循公用的 ICU 封裝慣例。 當您建立自訂的 ICU 時，您可以自訂它以產生 lib 名稱和匯出的符號名稱以包含尾碼，例如， `libicuucmyapp` ，其中 `myapp` 是尾碼。

`<version>`：有效的 ICU 版本，例如67.1。 這個版本是用來載入二進位檔，並取得匯出的符號。

若要在設定應用程式本機參數時載入 ICU，.NET 會使用 <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> 方法來探查多個路徑。 方法會先嘗試在屬性中尋找程式庫 `NATIVE_DLL_SEARCH_DIRECTORIES` ，這是由 dotnet 主機根據應用程式的檔案所建立 `deps.json` 。 如需詳細資訊，請參閱[預設探查](../../core/dependency-loading/default-probing.md)。

針對獨立應用程式，使用者不需要採取任何特殊動作，除了確定 ICU 是在應用程式目錄中（針對獨立式應用程式，工作目錄預設為 `NATIVE_DLL_SEARCH_DIRECTORIES` ）。

如果您是透過 NuGet 套件取用 ICU，這適用于架構相依的應用程式。 NuGet 會解析原生資產，並將它們包含在檔案 `deps.json` 和目錄下之應用程式的輸出目錄中 `runtimes` 。 .NET 會從該處載入它。

針對從本機組建取用 ICU 的 framework 相依應用程式（非獨立），您必須採取額外的步驟。 .NET SDK 尚未有「鬆散」的原生二進位檔要併入的功能 `deps.json` （請參閱[此 SDK 問題](https://github.com/dotnet/sdk/issues/11373)）。 相反地，您可以藉由在應用程式的專案檔中新增其他資訊來啟用此項。 例如：

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

這必須針對支援的執行時間的所有 ICU 二進位檔來完成。 此外， `NuGetPackageId` 專案群組中的中繼資料 `RuntimeTargetsCopyLocalItems` 必須符合專案實際所參考的 NuGet 套件。

### <a name="macos-behavior"></a>macOS 行為

`macOS`具有不同的行為，可從檔案中指定的載入命令（ `match-o` 而非 Linux 載入器）解析相依的動態連結程式庫。 在 Linux 載入器中，.NET 可以嘗試 `libicudata` 、 `libicuuc` 和 `libicui18n` （依此順序）來滿足 ICU 相依性圖形。 不過，在 macOS 上，這不會有作用。 在 macOS 上建立 ICU 時，根據預設，您會在中使用這些載入命令來取得動態連結程式庫 `libicuuc` 。 例如：

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

這些命令只會參考 ICU 其他元件的相依程式庫名稱。 載入器會依照慣例執行搜尋 `dlopen` ，這牽涉到在系統目錄中擁有這些程式庫或設定 `LD_LIBRARY_PATH` env 變數，或在應用層級目錄中擁有 ICU。 如果您無法設定 `LD_LIBRARY_PATH` 或確定 ICU 二進位檔位於應用層級目錄，您將需要執行一些額外的工作。

載入器有一些指示詞，例如 `@loader_path` ，它會告知載入器使用該載入命令，在與二進位檔相同的目錄中搜尋該相依性。 作法有二：

- `install_name_tool -change`

  執行下列命令：

```bash
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
```

- 修補 ICU 以產生安裝名稱`@loader_path`

  執行 autoconf （ `./runConfigureICU` ）之前，請將[下列幾行](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37)變更為：

```
LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
```
