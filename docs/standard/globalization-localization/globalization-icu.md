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
# <a name="net-globalization-and-icu"></a>.NET 全球化和 ICU

在過去，.NET 全球化 Api 在不同的平臺上使用不同的基礎程式庫。 在 Unix 上，Api 使用了 [Unicode (ICU) 的國際元件 ](http://site.icu-project.org/home)，而在 Windows 上則是使用 [國家語言支援 (NLS) ](/windows/win32/intl/national-language-support)。 這會導致在不同平臺上執行應用程式時，少數的全球化 Api 有一些行為差異。 這些方面的行為差異很明顯：

- 文化特性和文化特性資料
- 字串大小寫
- 字串排序和搜尋
- 排序索引鍵
- 字串正規化
-  (IDN) 支援的國際化功能變數名稱
- Linux 上的時區顯示名稱

從 .NET 5.0 開始，開發人員可以更充分掌控使用的基礎程式庫，讓應用程式得以避免不同平臺之間的差異。

## <a name="icu-on-windows"></a>Windows 上的 ICU

Windows 10 2019 年5月更新和更新版本包含 [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) 作為作業系統的一部分，而 .net 5.0 和更新版本預設會使用 ICU。 在 Windows 上執行時，.NET 5.0 和更新版本會嘗試載入，如果有的話，請 `icu.dll` 將它用於全球化執行。 如果找不到或無法載入 ICU 程式庫（例如在舊版 Windows 上執行時），則 .NET 5.0 和更新版本會切換回以 NLS 為基礎的實作為。

> [!NOTE]
> 即使使用 ICU， `CurrentCulture` 、 `CurrentUICulture` 和 `CurrentRegion` 成員仍會使用 Windows 作業系統 api 來接受使用者設定。

### <a name="use-nls-instead-of-icu"></a>使用 NLS 而非 ICU

使用 ICU 而非 NLS，可能會導致與一些全球化相關作業的行為有所差異。 若要還原回使用 NLS，開發人員可以退出宣告 ICU 的執行。 應用程式可以使用下列任何一種方式來啟用 NLS 模式：

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

- 將環境變數設定 `DOTNET_SYSTEM_GLOBALIZATION_USENLS` 為值 `true` 或 `1` 。

> [!NOTE]
> 在專案或檔案中設定的值 `runtimeconfig.json` 會優先于環境變數。

如需詳細資訊，請參閱 [執行時間配置設定](../../core/run-time-config/globalization.md#nls)。

## <a name="app-local-icu"></a>應用程式本機 ICU

每一版的 ICU 都可能帶來 it bug 修正，以及更新的一般地區設定資料存放庫 (CLDR 描述世界語言的) 資料。 在不同版本的 ICU 之間移動時，在與全球化相關的作業時，可能會對應用程式行為產生細微的影響 為了協助應用程式開發人員確保所有部署之間的一致性，.NET 5.0 和更新版本可讓 Windows 和 Unix 上的應用程式執行並使用自己的 ICU 複本。

應用程式可以使用下列任何一種方式，選擇進入應用程式本機的 ICU 真實模式：

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

- 將環境變數設定 `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` 為值 `<suffix>:<version>` 或 `<version>` 。

  `<suffix>`：選擇性尾碼的長度少於36個字元，請遵循 public ICU 封裝慣例。 當您建立自訂的 ICU 時，您可以自訂它來產生 lib 名稱和匯出的符號名稱，以包含尾碼，例如， `libicuucmyapp` 其中 `myapp` 是尾碼。

  `<version>`：有效的 ICU 版本，例如67.1。 此版本是用來載入二進位檔，並取得匯出的符號。

若要在設定應用程式本機參數時載入 ICU，.NET 會使用 <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> 探查多個路徑的方法。 方法會先嘗試在屬性中尋找程式庫 `NATIVE_DLL_SEARCH_DIRECTORIES` ，此屬性是由 dotnet 主機根據應用程式的檔案所建立 `deps.json` 。 如需詳細資訊，請參閱 [預設探查](../../core/dependency-loading/default-probing.md)。

針對獨立應用程式，使用者不需要採取任何特殊動作，除了確定 ICU 是在獨立應用程式的應用程式目錄 (中，工作目錄預設為 `NATIVE_DLL_SEARCH_DIRECTORIES`) 。

如果您是透過 NuGet 套件來取用 ICU，這會在與 framework 相依的應用程式中運作。 NuGet 會解析原生資產，並將它們包含在檔案中，並將其包含在 `deps.json` 目錄的應用程式的輸出目錄中 `runtimes` 。 .NET 會從該處載入它。

針對與 framework 相依的應用程式， (不是自主) 從本機組建取用 ICU 的情況下，您必須採取額外的步驟。 .NET SDK 尚未提供「鬆散」原生二進位檔的功能，可將其併入 `deps.json` (請參閱 [此 SDK 問題](https://github.com/dotnet/sdk/issues/11373)) 。 相反地，您可以藉由在應用程式的專案檔中新增其他資訊來啟用此專案。 例如︰

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

這必須針對支援執行時間的所有 ICU 二進位檔進行。 此外， `NuGetPackageId` 專案群組中的中繼資料 `RuntimeTargetsCopyLocalItems` 必須符合專案實際參考的 NuGet 套件。

### <a name="macos-behavior"></a>macOS 行為

`macOS` 有不同的行為，可從檔案中指定的載入命令（ `match-o` 而不是 Linux 載入器）解析相依的動態連結程式庫。 在 Linux 載入器中，.NET 可以 `libicudata` `libicuuc` `libicui18n` 依該順序嘗試、和 () 來滿足 ICU 相依性圖形。 不過，在 macOS 上，這無法運作。 在 macOS 上建立 ICU 時，根據預設，會在中使用這些載入命令來取得動態連結程式庫 `libicuuc` 。 下列程式碼片段顯示範例。

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

這些命令只會參考其他 ICU 元件的相依程式庫名稱。 載入器會依照慣例執行搜尋 `dlopen` ，其牽涉到將這些程式庫安裝在系統目錄中或設定 `LD_LIBRARY_PATH` env 變數，或在應用層級目錄中具有 ICU。 如果您無法設定 `LD_LIBRARY_PATH` 或確定 ICU 二進位檔是在應用層級目錄，您需要執行一些額外的工作。

載入器有一些指示詞，例如 `@loader_path` ，它會指示載入器使用該 load 命令，在與二進位檔相同的目錄中搜尋該相依性。 作法有二：

- `install_name_tool -change`

  執行下列命令：

  ```bash
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
  install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
  ```

- 修補 ICU 以產生安裝名稱 `@loader_path`

  在執行 autoconf (`./runConfigureICU`) 之前，請將 [下列幾行](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) 變更為：

  ```
  LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
  ```

## <a name="icu-on-webassembly"></a>WebAssembly 上的 ICU

您可以針對 WebAssembly 的工作負載取得 ICU 的版本。 此版本提供與桌面設定檔的全球化相容性。 若要將 ICU 資料檔案大小從 24 MB 減少為 1.4 MB (或 ~ 0.3 MB （如果使用 Brotli) 壓縮的話），此工作負載有少數的限制。

不支援下列 Api：

- <xref:System.Globalization.CultureInfo.EnglishName?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.NativeName?displayProperty=nameWithType>
- <xref:System.Globalization.DateTimeFormatInfo.NativeCalendarName?displayProperty=nameWithType>
- <xref:System.Globalization.RegionInfo.NativeName?displayProperty=nameWithType>

以下是支援的 Api，其限制如下：

- <xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> 而且 <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> 不支援很少使用 <xref:System.Text.NormalizationForm.FormKC> 和 <xref:System.Text.NormalizationForm.FormKD> 表單。
- <xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> 會傳回與 <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType> 相同的值。

此外，您可以在 [dotnet/icu](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54)存放庫中找到支援的地區設定清單。
