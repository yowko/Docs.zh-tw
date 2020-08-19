---
title: 編譯器選項
description: '使用 F # 編譯器命令列選項來控制 F # 應用程式和程式庫的編譯。'
ms.date: 08/15/2020
ms.openlocfilehash: 7f7b7dac2060213cd7d783669cb4de2b96a88968
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557356"
---
# <a name="compiler-options"></a>編譯器選項

本主題說明 F # 編譯器 fsc.exe 的編譯器命令列選項。

您也可以藉由設定專案屬性來控制編譯環境。 針對以 .NET Core 為目標的專案，中的「其他旗標」屬性 `<OtherFlags>...</OtherFlags>` `.fsproj` 會用來指定額外的命令列選項。

## <a name="compiler-options-listed-alphabetically"></a>依字母順序排列的編譯器選項

下表顯示依字母順序列出的編譯器選項。 某些 F # 編譯器選項類似于 c # 編譯器選項。 如果是這種情況，則會提供 c # 編譯器選項主題的連結。

|編譯器選項|描述|
|---------------|-----------|
|`-a filename.fs`|從指定的檔案產生文件庫。 此選項是的簡短形式 `--target:library filename.fs` 。|
|`--baseaddress:address`|指定載入 DLL 時慣用的基底位址。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;baseaddress &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)。|
|`--codepage:id`|如果必要的頁面不是系統目前的預設字碼頁，請指定在編譯期間要使用的字碼頁。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;程式字碼頁 &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/codepage-compiler-option.md)。|
|`--consolecolors`|指定錯誤和警告在主控台上使用以色彩標示的文字。|
|`--crossoptimize[+|-]`|啟用或停用跨模組優化。|
|<code>--delaysign[+&#124;-]</code>|只使用強式名稱金鑰的公開部分來延遲簽署元件。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;delaysign &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)。|
|<code>--checked[+&#124;-]</code>|啟用或停用產生溢位檢查。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [ &#40;C&#35; 編譯器選項&#41;&#47;核 ](../../csharp/language-reference/compiler-options/checked-compiler-option.md)取。|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|啟用或停用產生的 debug 資訊，或指定要產生的 debug 資訊類型。 預設值為 `full` ，可讓您附加至執行中的程式。 選擇 `pdbonly` 取得儲存在 pdb (程式資料庫) 檔中的有限偵錯工具資訊。<br /><br />相當於相同名稱的 c # 編譯器選項。 如需相關資訊，請參閱<br /><br />[&#47;debug &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/debug-compiler-option.md)。|
|`--define:symbol`<br /><br />`-d:symbol`|定義條件式編譯中使用的符號。|
|<code>--deterministic[+&#124;-]</code>|產生具決定性的元件 (包括模組版本 GUID 和時間戳記) 。 此選項不能與萬用字元版本號碼搭配使用，而且只支援內嵌和可移植的調試型別|
|`--doc:xmldoc-filename`|指示編譯器針對指定的檔案產生 XML 檔批註。 如需詳細資訊，請參閱 [XML Documentation](xml-documentation.md)。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;doc &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/doc-compiler-option.md)。|
|`--fullpaths`|指示編譯器產生完整路徑。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;fullpaths &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)。|
|`--help`<br /><br />`-?`|顯示使用方式資訊，包括所有編譯器選項的簡短描述。|
|<code>--highentropyva[+&#124;-]</code>|啟用或停用高熵位址空間配置隨機載入 (ASLR) （增強的安全性功能）。 OS 會隨機化記憶體中的位置，其中會載入應用程式 (的基礎結構，例如堆疊和堆積) 。 如果您啟用此選項，作業系統可以使用此隨機載入，在64位電腦上使用完整的64位位址空間。|
|`--keycontainer:key-container-name`|指定強式名稱金鑰容器。|
|`--keyfile:filename`|指定用於簽署所產生元件的公開金鑰檔案名。|
|`--lib:folder-name`<br /><br />`-I:folder-name`|指定要搜尋參考之元件的目錄。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;lib &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/lib-compiler-option.md)。|
|`--linkresource:resource-info`|將指定的資源連結至元件。 資源資訊的格式為 <code>filename[name[public&#124;private]]</code><br /><br />使用這個選項連結單一資源，是使用選項內嵌整個資源檔的替代方案 `--resource` 。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;linkresource &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)。|
|`--mlcompatibility`|當您使用設計來與其他 ML 版本相容的功能時，會忽略出現的警告。|
|`--noframework`|停用 .NET Framework 元件的預設參考。|
|`--nointerfacedata`|指示編譯器省略它通常會加入至包含 F # 專屬中繼資料之元件的資源。|
|`--nologo`|啟動編譯器時，不會顯示橫幅文字。|
|`--nooptimizationdata`|指示編譯器只包含執行內嵌結構的優化。 禁止跨模組內嵌，但改善二進位檔相容性。|
|`--nowin32manifest`|指示編譯器省略預設的 Win32 資訊清單。|
|`--nowarn:warning-number-list`|停用依數位列出的特定警告。 以逗號分隔每個警告編號。 您可以從編譯輸出中探索任何警告的警告編號。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;nowarn &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)。|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|啟用或停用優化。 您可以藉由列出某些優化選項，以選擇性地加以停用或啟用。 這些是： `nojitoptimize` 、 `nojittracking` 、 `nolocaloptimize` 、 `nocrossoptimize` 、 `notailcalls` 。|
|`--out:output-filename`<br /><br />`-o:output-filename`|指定已編譯的元件或模組的名稱。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;&#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/out-compiler-option.md)。|
|`--pathmap:path=sourcePath,...`|指定如何將實體路徑對應到編譯器所輸出的來源路徑名稱。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;pathmap &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/pathmap-compiler-option.md)。|
|`--pdb:pdb-filename`|將輸出偵錯工具的 (命名為程式資料庫) 檔。 此選項只適用于 `--debug` 也啟用時。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;pdb &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/pdb-compiler-option.md)。|
|`--platform:platform-name`|指定產生的程式碼只會在指定的平臺上執行 (`x86` 、 `Itanium` 或 `x64`) ，或者，如果選擇了平臺名稱 `anycpu` ，則會指定產生的程式碼可以在任何平臺上執行。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;平臺 &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/platform-compiler-option.md)。|
|`--preferreduilang:lang`| 指定慣用的輸出語言文化特性名稱 (例如，  `es-ES` `ja-JP`) 。 |
|`--quotations-debug`|指定應針對衍生自 F # 引號常值和反映定義的運算式發出額外的偵錯工具資訊。 偵錯工具資訊會加入至 F # 運算式樹狀結構節點的自訂屬性。 請參閱程式 [代碼引號](code-quotations.md) 和 [CustomAttributes](https://msdn.microsoft.com/visualfsharpdocs/conceptual/expr.customattributes-property-%5bfsharp%5d)。|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|讓 F # 或 .NET Framework 元件中的程式碼可供所要編譯的程式碼使用。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;參考 &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/reference-compiler-option.md)。|
|`--resource:resource-filename`|將 managed 資源檔內嵌到產生的元件中。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;資源 &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/resource-compiler-option.md)。|
|`--sig:signature-filename`|根據產生的元件產生簽名檔。 如需有關簽名檔的詳細資訊， [請參閱簽](signature-files.md)章。|
|`--simpleresolution`|指定應該使用以目錄為基礎的 Mono 規則來解析元件參考，而不是使用 MSBuild 解析。 預設值是使用 MSBuild 解析（除了在 Mono 下執行時）。|
|`--standalone`|指定要產生包含其所有相依性的元件，使其本身執行，而不需要其他元件，例如 F # 程式庫。|
|`--staticlink:assembly-name`|以靜態方式連結指定的元件，以及相依于此元件的所有參考 Dll。 使用元件名稱，而不是 DLL 名稱。|
|`--subsystemversion`|指定所產生之可執行檔所要使用的 OS 子系統版本。 使用6.02 進行 Windows 8.1、適用于 Windows 7 的6.01、適用于 Windows Vista 的6.00。 此選項只適用于可執行檔，而不是 Dll，而且只有在您的應用程式相依于特定作業系統版本上可用的特定安全性功能時，才需要使用。 如果使用此選項，且使用者嘗試在較低版本的作業系統上執行您的應用程式，它將會失敗並出現錯誤訊息。|
|<code>--tailcalls[+&#124;-]</code>|啟用或停用 tail IL 指令，這會導致堆疊框架重複用於 tail 遞迴函式。 這個選項預設為啟用。|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|指定所產生之已編譯器代碼的類型和檔案名。<ul><li>`exe` 表示主控台應用程式。<br /></li><li>`winexe` 表示 Windows 應用程式與主控台應用程式不同，因為它沒有標準的輸入/輸出資料流程 (stdin、stdout 和 stderr) 已定義。<br /></li><li>`library` 是沒有進入點的元件。<br /></li><li>`module` 是 .NET Framework 模組 (. .netmodule) ，稍後可以與其他模組結合至元件。<br /></li><ul/>這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;目標 &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/target-compiler-option.md)。|
|`--times`|顯示編譯的計時資訊。|
|`--utf8output`|啟用 UTF-8 編碼的列印編譯器輸出。|
|`--warn:warning-level`|設定警告層級 (0 到 5) 。 預設層級為3。 每個警告都會根據其嚴重性獲得等級。 層級5可提供比層級1更多但較不嚴重的警告。<br /><br />層級5警告為： 21 (在執行時間檢查遞迴使用) 、22 (依 `let rec` 順序評估) 、45 (完整抽象) 和 52 (防禦性複製) 。 所有其他警告都是層級2。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;警告 &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/warn-compiler-option.md)。|
|`--warnon:warning-number-list`|啟用可能預設關閉或由另一個命令列選項停用的特定警告。 1182 (未使用的變數) 警告預設為關閉。|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|啟用或停用將警告報告為錯誤的選項。 您可以提供要停用或啟用的特定警告編號。 稍後在命令列中的選項會覆寫先前命令列中的選項。 例如，若要指定您不想回報為錯誤的警告，請指定 `--warnaserror+` `--warnaserror-:warning-number-list` 。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;warnaserror &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)。|
|`--win32manifest:manifest-filename`|將 Win32 資訊清單檔加入至編譯。 這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;win32manifest &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)。|
|`--win32res:resource-filename`|將 Win32 資源檔新增至編譯。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱 [&#47;win32res ( # B1 C&#35;) 編譯器選項&#41;](../../csharp/language-reference/compiler-options/win32res-compiler-option.md)。|

## <a name="related-articles"></a>相關文章

|Title|描述|
|-----|-----------|
|[F# Interactive 選項](fsharp-interactive-options.md)|描述 F # 解譯器支援的命令列選項 fsi.exe。|
|[專案屬性參考](/visualstudio/ide/reference/project-properties-reference)|描述專案的 UI，包括提供組建選項的專案屬性頁。|
