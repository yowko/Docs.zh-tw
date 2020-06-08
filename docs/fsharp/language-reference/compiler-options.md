---
title: 編譯器選項
description: '使用 F # 編譯器命令列選項來控制 F # 應用程式和程式庫的編譯。'
ms.date: 12/10/2018
ms.openlocfilehash: 36db70102c641d8e447cd62faf69e921b0cba677
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493717"
---
# <a name="compiler-options"></a>編譯器選項

本主題描述 F # 編譯器 fsc 的編譯器命令列選項。

您也可以藉由設定專案屬性來控制編譯環境。 針對以 .NET Core 為目標的專案，中的「其他旗標」屬性 `<OtherFlags>...</OtherFlags>` `.fsproj` 會用來指定額外的命令列選項。

## <a name="compiler-options-listed-alphabetically"></a>依字母順序排列的編譯器選項

下表顯示依字母順序列出的編譯器選項。 某些 F # 編譯器選項類似 c # 編譯器選項。 如果是這種情況，則會提供 c # 編譯器選項主題的連結。

|編譯器選項|說明|
|---------------|-----------|
|`-a filename.fs`|從指定的檔案產生程式庫。 此選項是的簡短形式 `--target:library filename.fs` 。|
|`--baseaddress:address`|指定載入 DLL 時慣用的基底位址。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;baseaddress &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx)。|
|`--codepage:id`|如果必要的頁面不是系統目前的預設字碼頁，則指定要在編譯期間使用的字碼頁。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;字碼頁 &#40;C&#35; 編譯器選項&#41;](../../csharp/language-reference/compiler-options/codepage-compiler-option.md)。|
|`--consolecolors`|指定錯誤和警告在主控台上使用以色彩標示的文字。|
|`--crossoptimize[+|-]`|啟用或停用跨模組優化。|
|<code>--delaysign[+&#124;-]</code>|只使用強式名稱金鑰的公用部分來延遲簽署元件。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;delaysign &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx)。|
|<code>--checked[+&#124;-]</code>|啟用或停用產生溢位檢查。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;核取 &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx)。|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|啟用或停用產生的調試資訊，或指定要產生的調試資訊類型。 預設值為 full，允許附加至執行中的程式。 選擇 [ **pdbonly** ] 以取得儲存在 pdb （程式資料庫）檔案中的有限偵錯工具資訊。<br /><br />相當於相同名稱的 c # 編譯器選項。 如需相關資訊，請參閱<br /><br />[&#47;debug &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx)。|
|`--define:symbol`<br /><br />`-d:symbol`|定義要在條件式編譯中使用的符號。|
|<code>--deterministic[+&#124;-]</code>|產生具決定性的元件（包括模組版本 GUID 和時間戳記）。 此選項不能搭配萬用字元版本號碼使用，而且只支援內嵌和可移植的調試類型|
|`--doc:xmldoc-filename`|指示編譯器產生 XML 檔批註給指定的檔案。 如需詳細資訊，請參閱 [XML Documentation](xml-documentation.md)。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;doc &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/3260k4x7.aspx)。|
|`--fullpaths`|指示編譯器產生完整的路徑。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;fullpaths &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/d315xc66.aspx)。|
|`--help`<br /><br />`-?`|顯示使用方式資訊，包括所有編譯器選項的簡短描述。|
|<code>--highentropyva[+&#124;-]</code>|啟用或停用高熵位址空間配置隨機載入（ASLR），這是增強的安全性功能。 作業系統會隨機化在記憶體中的位置，其中會載入應用程式的基礎結構（例如堆疊和堆積）。 如果您啟用此選項，作業系統可以使用此隨機載入，在64位的電腦上使用完整的64位位址空間。|
|`--keycontainer:key-container-name`|指定強式名稱金鑰容器。|
|`--keyfile:filename`|指定用來簽署所產生元件的公開金鑰檔案名。|
|`--lib:folder-name`<br /><br />`-I:folder-name`|指定要搜尋參考之元件的目錄。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;lib &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx)。|
|`--linkresource:resource-info`|將指定的資源連結至元件。 資源資訊的格式為<code>filename[name[public&#124;private]]</code><br /><br />使用此選項連結單一資源，是使用選項內嵌整個資源檔的替代方法 `--resource` 。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;linkresource &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/xawyf94k.aspx)。|
|`--mlcompatibility`|當您使用設計來與其他 ML 版本相容的功能時，會忽略出現的警告。|
|`--noframework`|停用 .NET Framework 元件的預設參考。|
|`--nointerfacedata`|指示編譯器省略它通常會新增至包含 F # 特定中繼資料之元件的資源。|
|`--nologo`|啟動編譯器時，不會顯示橫幅文字。|
|`--nooptimizationdata`|指示編譯器只包含用於執行內嵌結構的優化。 禁止跨模組內嵌，但改善二進位相容性。|
|`--nowin32manifest`|指示編譯器省略預設的 Win32 資訊清單。|
|`--nowarn:warning-number-list`|停用依數位列出的特定警告。 以逗號分隔每個警告編號。 您可以從編譯輸出中探索任何警告的警告編號。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;nowarn &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx)。|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|啟用或停用優化。 某些優化選項可以藉由列出，以選擇性地停用或啟用。 這些是： `nojitoptimize` 、 `nojittracking` 、 `nolocaloptimize` 、 `nocrossoptimize` 、 `notailcalls` 。|
|`--out:output-filename`<br /><br />`-o:output-filename`|指定已編譯元件或模組的名稱。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;out &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx)。|
|`--pathmap:path=sourcePath,...`|指定如何將實體路徑對應到編譯器所輸出的來源路徑名稱。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;pathmap &#40;C&#35; 編譯器選項&#41;](/csharp/language-reference/compiler-options/pathmap-compiler-option)。|
|`--pdb:pdb-filename`|命名輸出偵錯工具 PDB （程式資料庫）檔案。 此選項只適用于 `--debug` 同時啟用時。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;pdb &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/ms228625.aspx)。|
|`--platform:platform-name`|指定產生的程式碼只會在指定的平臺上執行（ `x86` 、 `Itanium` 或 `x64` ），或者，如果選擇平臺名稱，則會 `anycpu` 指定產生的程式碼可以在任何平臺上執行。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;平臺 &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx)。|
|`--preferreduilang:lang`| 指定慣用的輸出語言文化特性名稱（例如， `es-ES` `ja-JP` ）。 |
|`--quotations-debug`|指定針對衍生自 F # 引號常值和反映定義的運算式，應發出額外的偵錯工具資訊。 偵錯工具資訊會加入至 F # 運算式樹狀結構節點的自訂屬性。 請參閱程式[代碼引號](code-quotations.md)和[Expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)。|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|讓 F # 或 .NET Framework 元件中的程式碼可供編譯的程式碼使用。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;參考 &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx)。|
|`--resource:resource-filename`|將 managed 資源檔內嵌至產生的元件。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;資源 &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/c0tyye07.aspx)。|
|`--sig:signature-filename`|根據產生的元件產生簽名檔案。 如需有關簽章檔案的詳細資訊，[請參閱簽](signature-files.md)章。|
|`--simpleresolution`|指定應該使用以目錄為基礎的 Mono 規則（而非 MSBuild 解析）來解析元件參考。 預設值是使用 MSBuild 解析，但在 Mono 底下執行時除外。|
|`--standalone`|指定產生包含所有相依性的元件，使其本身執行，而不需要額外的元件，例如 F # 程式庫。|
|`--staticlink:assembly-name`|以靜態方式連結指定的元件，以及相依于這個元件的所有參考 Dll。 使用元件名稱，而不是 DLL 名稱。|
|`--subsystemversion`|指定所產生的可執行檔所要使用的 OS 子系統版本。 針對 Windows 8.1 使用6.02，適用于 Windows 7 的6.01，6.00 適用于 Windows Vista。 此選項僅適用于可執行檔，而非 Dll，而且只有在您的應用程式相依于特定版本的作業系統時，才需要使用。 如果使用此選項，且使用者嘗試在較低版本的 OS 上執行您的應用程式，則會失敗並出現錯誤訊息。|
|<code>--tailcalls[+&#124;-]</code>|啟用或停用 tail IL 指令的使用，這會導致堆疊框架重複用於尾遞迴函式。 這個選項預設為啟用。|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|指定所產生之已編譯器代碼的類型和檔案名。<ul><li>`exe`表示主控台應用程式。<br /></li><li>`winexe`表示 Windows 應用程式，與主控台應用程式不同之處在于，它不會定義標準輸入/輸出資料流程（stdin、stdout 和 stderr）。<br /></li><li>`library`是沒有進入點的元件。<br /></li><li>`module`是 .NET Framework 模組（. .netmodule），稍後可以與其他模組結合成元件。<br /></li><ul/>這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;目標 &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/6h25dztx.aspx)。|
|`--times`|顯示編譯的計時資訊。|
|`--utf8output`|啟用以 UTF-8 編碼方式列印編譯器輸出。|
|`--warn:warning-level`|設定警告層級（0到5）。 預設層級為3。 每個警告都會根據其嚴重性提供一個層級。 層級5會提供比層級1更多但較不嚴重的警告。<br /><br />層級5警告為：21（遞迴使用於執行時間時檢查）、22（依 `let rec` 序評估）、45（完整抽象）和52（防禦性複本）。 所有其他警告都是層級2。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;警告 &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/13b90fz7.aspx)。|
|`--warnon:warning-number-list`|啟用可能預設為關閉或由另一個命令列選項停用的特定警告。 在 F # 3.0 中，只有1182（未使用的變數）警告預設為關閉。|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|啟用或停用將警告報告為錯誤的選項。 您可以提供要停用或啟用的特定警告編號。 稍後在命令列中的選項會覆寫命令列中先前的選項。 例如，若要指定您不想要回報為錯誤的警告，請指定 `--warnaserror+` `--warnaserror-:warning-number-list` 。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;warnaserror &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/406xhdz3.aspx)。|
|`--win32manifest:manifest-filename`|將 Win32 資訊清單檔案加入至編譯。 這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;win32manifest &#40;C&#35; 編譯器選項&#41;](https://msdn.microsoft.com/library/bb545961.aspx)。|
|`--win32res:resource-filename`|將 Win32 資源檔加入至編譯。<br /><br />這個編譯器選項相當於相同名稱的 c # 編譯器選項。 如需詳細資訊，請參閱[&#47;win32res （&#40;C&#35;）編譯器選項&#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx)。|

## <a name="related-articles"></a>相關文章

|Title|描述|
|-----|-----------|
|[F# Interactive 選項](fsharp-interactive-options.md)|描述 F # 解譯器（fsi.exe）所支援的命令列選項。|
|[專案屬性參考](/visualstudio/ide/reference/project-properties-reference)|描述專案的 UI，包括提供組建選項的專案屬性頁。|
