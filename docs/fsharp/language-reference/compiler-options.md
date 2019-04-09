---
title: 編譯器選項
description: 使用F#編譯器的命令列選項，以控制編譯您F#應用程式和程式庫。
ms.date: 12/10/2018
ms.openlocfilehash: fa639fe37ed336ad9f990e01bf2645c5a86498e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089753"
---
# <a name="compiler-options"></a>編譯器選項

本主題描述編譯器命令列選項F#編譯器、 fsc.exe。 此編譯環境也可以藉由設定專案屬性來控制。

## <a name="compiler-options-listed-alphabetically"></a>依字母順序排列的編譯器選項
下表顯示依字母順序排列的編譯器選項。 某些F#編譯器選項會類似於C#編譯器選項。 如果這種情況下，將C#編譯器選項主題會提供。

|編譯器選項|描述|
|---------------|-----------|
|`-a filename.fs`|從指定的檔案中產生程式庫。 此功能的簡短形式`--target:library filename.fs`。|
|`--baseaddress:address`|指定載入 DLL 時慣用的基底位址。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;a &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx)。|
|`--codepage:id`|指定如果必要的頁面不是系統目前的預設字碼頁，在編譯時使用的字碼頁。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [&#47;字碼頁&#40;C&#35;編譯器選項&#41;](../../csharp/language-reference/compiler-options/codepage-compiler-option.md)。|
|`--consolecolors`|指定的錯誤和警告以色彩標示的文字的主控台上使用。|
|`--crossoptimize[+|-]`|啟用或停用跨模組最佳化。|
|<code>--delaysign[+&#124;-]</code>|延遲簽署組件使用強式名稱金鑰的公開部分。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;delaysign &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx)。|
|<code>--checked[+&#124;-]</code>|啟用或停用產生溢位檢查。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [&#47;核取&#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx)。|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|啟用或停用產生偵錯的詳細資訊，或指定要產生的偵錯資訊類型。 預設值為 full，以便附加至執行中的程式。 選擇**pdbonly**取得儲存在 pdb （程式資料庫） 檔中的有限偵錯資訊。<br /><br />相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱<br /><br />[&#47;偵錯&#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx)。|
|`--define:symbol`<br /><br />`-d:symbol`|定義條件式編譯符號，以供使用。|
|<code>--deterministic[+&#124;-]</code>|產生的具決定性的組件 （包括模組版本 GUID 與時間戳記）。 此選項不能使用萬用字元的版本號碼，並僅支援內嵌和可攜式偵錯類型|
|`--doc:xmldoc-filename`|會指示編譯器產生指定之檔案的 XML 文件註解。 如需詳細資訊，請參閱 [XML Documentation](xml-documentation.md)。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [&#47;文件&#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/3260k4x7.aspx)。|
|`--fullpaths`|會指示編譯器產生完整的路徑。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;fullpaths &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/d315xc66.aspx)。|
|`--help`<br /><br />`-?`|顯示用法資訊，包括所有的編譯器選項的簡短描述。|
|<code>--highentropyva[+&#124;-]</code>|啟用或停用高熵位址空間配置隨機載入 (ASLR)，增強的安全性功能。 OS 隨機化的位置，在記憶體中載入應用程式 （例如堆疊和堆積） 的基礎結構的位置。 如果您啟用此選項時，作業系統就可以使用這項隨機化 64 位元電腦上使用完整 64 位元位址空間。|
|`--keycontainer:key-container-name`|指定強式名稱金鑰容器。|
|`--keyfile:filename`|指定公開金鑰檔案來簽署產生的組件名稱。|
|`--lib:folder-name`<br /><br />`-I:folder-name`|指定要搜尋參考的組件的目錄。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;lib &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx)。|
|`--linkresource:resource-info`|指定的資源連結至組件。 資源資訊的格式 <code>filename[name[public&#124;private]]</code><br /><br />連結單一資源並使用此選項是內嵌的整個資源檔案的替代方式`--resource`選項。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;/linkresource &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/xawyf94k.aspx)。|
|`--mlcompatibility`|會忽略顯示當您使用所設計的功能與其他 ML 版本相容的警告。|
|`--noframework`|停用.NET Framework 組件的預設參考。|
|`--nointerfacedata`|指示編輯器省略通常會加入至組件，其中包含的資源F#-指定的中繼資料。|
|`--nologo`|啟動編譯器時，不會顯示橫幅文字。|
|`--nooptimizationdata`|指示編輯器只納入實作內嵌的建構不可或缺的最佳化。 禁止跨模組內嵌，但改進了二進位相容性。|
|`--nowin32manifest`|會指示編譯器略過預設 Win32 資訊清單。|
|`--nowarn:warning-number-list`|停用依編號列出的特定警告。 以逗號分隔每個警告編號。 您可以探索從編譯輸出的任何警告的警告編號。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;nowarn &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx)。|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|啟用或停用最佳化。 某些最佳化選項可停用或啟用選擇性地列出它們。 這些是： `nojitoptimize`， `nojittracking`， `nolocaloptimize`， `nocrossoptimize`， `notailcalls`。|
|`--out:output-filename`<br /><br />`-o:output-filename`|指定已編譯組件或模組的名稱。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;out &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx)。|
|`--pdb:pdb-filename`|命名輸出偵錯 PDB （程式資料庫） 檔。 此選項時，才適用`--debug`也會啟用。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;pdb &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/ms228625.aspx)。|
|`--platform:platform-name`|指定產生的程式碼只會在指定的平台上執行 (`x86`， `Itanium`，或`x64`)，或者，如果平台名稱`anycpu`選擇時，會指定產生的程式碼可以在任何平台上執行。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [&#47;平台&#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx)。|
|`--preferreduilang:lang`| 指定慣用的輸出語言文化特性名稱 (例如`es-ES`， `ja-JP`)。 |
|`--quotations-debug`|指定的額外的偵錯資訊應該發出衍生自運算式的F#引號常值及反映的定義。 偵錯資訊加入自訂屬性的F#運算式樹狀節點。 請參閱[程式碼引號](code-quotations.md)並[Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)。|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|可讓程式碼，從F#或.NET Framework 組件提供給要編譯程式碼。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [&#47;參考&#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx)。|
|`--resource:resource-filename`|將 managed 的資源檔內嵌到產生的組件中。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [&#47;資源&#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/c0tyye07.aspx)。|
|`--sig:signature-filename`|產生簽章檔案產生的組件為基礎。 如需簽章檔案的詳細資訊，請參閱[簽章](signatures.md)。|
|`--simpleresolution`|指定應該使用目錄型 Mono 規則，而非 MSBuild 解析來解析組件參考。 預設為使用 MSBuild 解析，除了在 Mono 下執行時。|
|`--standalone`|指定要產生組件，其中包含其所有相依性，使其獨立執行，而不需要其他組件，例如F#程式庫。|
|`--staticlink:assembly-name`|以靜態方式連結指定的組件和所有參考的 Dll 相依於這個組件。 使用組件名稱，而不是 DLL 名稱。|
|`--subsystemversion`|指定產生的可執行檔所使用之作業系統子系統的版本。 適用於 Windows 8.1，Windows 7，Windows vista 6.00 的 6.01 6.02。 這個選項只適用於可執行檔，不是 Dll，並需要時才使用應用程式相依於特定的安全性功能僅適用於特定版本的作業系統。 如果使用此選項，而且使用者嘗試在較低版本的作業系統上執行您的應用程式，它將會失敗並出現錯誤訊息。|
|<code>--tailcalls[+&#124;-]</code>|啟用或停用結尾的 IL 指令，這會導致尾端遞迴函式重複使用的堆疊框架的使用。 這個選項預設為啟用。|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|指定產生的已編譯程式碼類型和檔案名稱。<ul><li>`exe` 表示主控台應用程式。<br /></li><li>`winexe` 表示不同於主控台應用程式，因為它並沒有標準輸入/輸出資料流 （stdin、 stdout 和 stderr） 定義的 Windows 應用程式。<br /></li><li>`library` 是沒有進入點的組件。<br /></li><li>`module` 是.NET Framework 模組 (.netmodule)，稍後可合併與其他模組的組件。<br /></li><ul/>這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [&#47;目標&#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/6h25dztx.aspx)。|
|`--times`|顯示編譯的時間資訊。|
|`--utf8output`|啟用列印編譯器輸出中的 utf-8 編碼方式。|
|`--warn:warning-level`|設定警告層級 (0 到 5)。 預設層級是 3。 每個警告可以根據其嚴重性層級。 等級 5 會提供比層級 1 多，但較不嚴重的警告。<br /><br />層級 5 警告如下：（在執行階段檢查到遞迴使用） 21、 22 (`let rec`未依順序評估)、 45 （完整抽象） 和 52 （防禦性複製）。 所有其他警告是層級 2。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [&#47;警告&#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/13b90fz7.aspx)。|
|`--warnon:warning-number-list`|啟用可能預設為關閉，或另一個命令列選項停用特定警告。 在F#3.0 中，只有 1182 （未使用的變數） 警告預設為關閉。|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|啟用或停用警告報告為錯誤的選項。 您可以提供特定的警告編號，以停用或啟用。 稍後的命令列選項覆寫稍早在命令列中的選項。 例如，若要指定您不想回報為錯誤的警告，指定`--warnaserror+` `--warnaserror-:warning-number-list`。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;/warnaserror &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/406xhdz3.aspx)。|
|`--win32manifest:manifest-filename`|將 Win32 資訊清單檔加入至編譯。 這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;win32manifest &#40;C&#35;編譯器選項&#41;](https://msdn.microsoft.com/library/bb545961.aspx)。|
|`--win32res:resource-filename`|將 Win32 資源檔加入至編譯。<br /><br />這個編譯器選項相當於C#編譯器選項相同的名稱。 如需詳細資訊，請參閱 < [ &#47;win32res (&#40;C&#35;) 編譯器選項&#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx)。|

## <a name="related-articles"></a>相關文章

|標題|描述|
|-----|-----------|
|[F# Interactive 選項](fsharp-interactive-options.md)|描述支援的命令列選項F#解譯器、 fsi.exe。|
|[專案屬性參考](/visualstudio/ide/reference/project-properties-reference)|描述專案，包括提供建置選項的專案屬性頁的 UI。|