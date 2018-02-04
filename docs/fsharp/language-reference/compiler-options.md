---
title: "編譯器選項 (F#)"
description: "使用 F # 編譯器命令列選項來控制 F # 應用程式和程式庫編譯。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c797cf0b-5953-4053-8626-0558e9eaf10f
ms.openlocfilehash: 23731832141bc2f74a04c5f4027fc210b5589537
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="compiler-options"></a>編譯器選項

本主題說明編譯器命令列選項的 F # 編譯器 fsc.exe。 編譯環境也可以藉由設定專案屬性來控制。


## <a name="compiler-options-listed-alphabetically"></a>依字母順序排列的編譯器選項
下表顯示依字母順序排列的編譯器選項。 有些類似於 C# 編譯器選項 F # 編譯器選項。 如果這種情況，請在提供 C# 編譯器選項主題的連結。



|編譯器選項|描述|
|---------------|-----------|
|**-a****&lt;output-filename&gt;**|產生的程式庫，並指定其檔案名稱。 這個選項是一種的簡短形式**-目標： 媒體櫃 *&lt;filename&gt;**。|
|**--baseaddress:&lt;string&gt;**|指定要建置程式庫的基底位址。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; baseaddress &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|**--codepage:&lt;int&gt;**|指定用來讀取原始程式檔的字碼頁。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; 字碼頁 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/w0kyekyh.aspx).|
|**--consolecolors**|指定的錯誤和警告使用色彩編碼的文字在主控台上。|
|**--crossoptimize**[**+**&#124;**-**]|啟用或停用跨模組最佳化。|
|**--delaysign**[**+**&#124;**-**]|延遲簽署組件使用強式名稱金鑰的公開部分。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; delaysign &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|**--checked**[**+**&#124;**-**]|啟用或停用產生溢位檢查。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[（& s) #47; 檢查 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|**--debug**[**+**&#124;**-**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**--debug**:[**full**&#124;**pdbonly**]<br /><br />**-g:** [**full**&#124;**pdbonly**]|啟用或停用偵錯資訊的產生，或指定產生的偵錯資訊類型。 預設值是完整的這允許附加至正在執行的程式。 選擇**pdbonly**取得限制儲存在 pdb （程式資料庫） 檔案中的偵錯資訊。<br /><br />相當於 C# 編譯器選項的名稱相同。 如需詳細資訊，請參閱<br /><br />[&#47; 偵錯 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx).|
|**--define:&lt;string&gt;**<br /><br />**-d:&lt;string&gt;**|定義條件式編譯符號，以供使用。|
|**--deterministic**[**+**&#124;**-**]|產生的具決定性的組件 （包括模組版本 GUID 與時間戳記）。  這不能使用萬用字元的版本號碼，並僅支援內嵌和可攜式的偵錯類型|
|**--doc:&lt;xmldoc-filename&gt;**|指示編譯器產生指定之檔案的 XML 文件註解。 如需詳細資訊，請參閱[XML 文件](xml-documentation.md)。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; 文件 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|**--fullpaths**|指示編譯器產生完整的路徑。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; fullpaths &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/d315xc66.aspx).|
|**--help**<br /><br />**-?**|顯示使用方式資訊，包括所有的編譯器選項的簡短描述。|
|**--highentropyva**[**+**&#124;**-**]|啟用或停用高熵位址空間配置隨機載入 (ASLR)、 增強式的安全性功能。 OS 隨機放置個基礎結構的應用程式 （例如堆疊和堆積中） 的載入位置的記憶體位置。 如果您啟用此選項時，作業系統就可以使用此隨機在 64 位元電腦上使用完整 64 位元位址空間。|
|**--keycontainer:&lt;string&gt;**|指定強式名稱金鑰容器。|
|**--keyfile:&lt;filename&gt;**|指定的公開金鑰來簽署產生的組件檔案名稱。|
|**--lib:&lt;folder-name&gt;**<br /><br />**-I:&lt;folder-name&gt;**|指定要在其中搜尋參考的組件的目錄。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; lib &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|**--linkresource**:**&lt;resource-info&gt;**|指定的資源連結至組件中。 資源資訊的格式是*filename*[，*名稱*[，*公用*&#124;*私用*]]<br /><br />連結到單一資源，使用此選項是內嵌整個資源檔的替代方式**-資源**選項。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; linkresource &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|**--mlcompatibility**|當您使用與其他 ML 版本相容性所設計的功能時所出現的警告，將會忽略。|
|**--noframework**|停用預設參考至.NET Framework 組件。|
|**--nointerfacedata**|指示編譯器忽略它通常會加入包含 F # 組件的資源-特定的中繼資料。|
|**--nologo**|當您啟動編譯器時，不會顯示的橫幅文字。|
|**--nooptimizationdata**|指示編譯器只包含實作內嵌的建構必要的最佳化。 禁止跨模組內嵌，但可改善二進位碼相容性。|
|**--nowin32manifest**|指示編譯器忽略預設的 Win32 資訊清單。|
|**--nowarn:&lt;int-list&gt;**|停用特定警告列出編號。 以逗號分隔每個警告編號。 您可以探索編譯輸出中的任何警告的警告編號。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; nowarn &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|**--optimize**[**+**&#124;**-**]**[&lt;string-list&gt;]**<br /><br />**-O[+&#124;-] [&lt;string-list&gt;]**|啟用或停用最佳化。 可以停用某些最佳化選項，或選擇性地啟用列出它們。 這些是： **nojitoptimize**， **nojittracking**， **nolocaloptimize**， **nocrossoptimize**， **notailcalls**.|
|**--out:&lt;output-filename&gt;**<br /><br />**-o:&lt;output-filename&gt;**|指定編譯的組件或模組的名稱。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; out &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|**--pdb:&lt;pdb-filename&gt;**|輸出偵錯 （程式資料庫） PDB 檔的名稱。 此選項僅適用於當**-偵錯**也會啟用。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; pdb &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/ms228625.aspx).|
|**--platform:&lt;platform-name&gt;**|指定產生的程式碼只會在指定的平台上執行 (**x86**， **Itanium**，或**x64**)，或者，如果平台名稱**anycpu**選擇時，會指定產生的程式碼可以在任何平台上執行。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; 平台 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|**--preferreduilang:&lt;lang&gt;**| 指定慣用的輸出語言文化特性名稱 （例如 ES-ES、 JA-JP）。 |
|**--quotations-debug**|指定的額外偵錯資訊應該發出對衍生自 F # 引號常值，而且反映定義的運算式。 偵錯資訊已加入至 F # 運算式樹狀結構節點的自訂屬性。 請參閱[程式碼引號](code-quotations.md)和[Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)。|
|**--reference:&lt;assembly-filename&gt;**<br /><br />**-r** &lt;**assembly-filename&gt;**|讓程式碼從 F # 或.NET Framework 組件可供已編譯的程式碼。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; 參考 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|**--resource:&lt;resource-filename&gt;**|Managed 的資源檔嵌入產生的組件。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; 資源 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|**--sig**:&lt;**signature-filename&gt;**|產生簽章檔案產生的組件為基礎。 如需簽章檔案的詳細資訊，請參閱[簽章](signatures.md)。|
|**--simpleresolution**|指定應該使用目錄型單聲道的規則，而不是 MSBuild 解析來解析組件參考。 預設為使用 MSBuild 解析 Mono 執行時除外。|
|**--standalone**|指定用來產生包含及其所有相依性，使其本身執行，而不需要額外的組件，例如 F # 程式庫的組件。|
|**--staticlink:&lt;assembly-name**&gt;|以靜態方式連結指定的組件和所有依存於這個組件的被參考的 Dll。 使用組件名稱，而不是 DLL 名稱。|
|**--subsystemversion**|指定要使用所產生的可執行檔的作業系統子系統版本。 使用 Windows 8.1、 windows 7、 Windows vista 6.00 6.01 6.02。 這個選項只適用於可執行檔，不是 Dll，並需要只能使用於您的應用程式依存於特定的安全性功能只能在特定的作業系統版本上使用。 如果使用此選項，而且使用者嘗試在較低版本的作業系統上執行您的應用程式，它將會失敗並出現錯誤訊息。|
|**--tailcalls**[**+**&#124;**-**]|啟用或停用造成可重複使用之結尾遞迴函式的堆疊框架結尾 IL 指令的使用。 這個選項預設為啟用。|
|**--target**:[**exe** &#124; **winexe** &#124; **library** &#124; **module** ] **&lt;output-filename&gt;**|指定產生已編譯的程式碼的類型和檔案名稱。<ul><li>**exe**表示主控台應用程式。<br /></li><li>**winexe**表示不同於主控台應用程式，因為它沒有標準輸出資料流 （stdin、 stdout、 與 stderr） 定義的 Windows 應用程式。<br /></li><li>**程式庫**是沒有進入點的組件。<br /></li><li>**模組**是.NET Framework 模組 (.netmodule)，稍後可合併與其他模組的組件。<br /></li><ul/>這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; 目標 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|**--times**|顯示已編譯的計時資訊。|
|**--utf8output**|啟用列印編譯器輸出中的 utf-8 編碼方式。|
|**--warn:&lt;warning-level&gt;**|設定警告層級 (0 到 5)。 預設值為 3。 每個警告是提供根據其嚴重性層級。 層級 5 提供多個，但較少的嚴重性，警告層級 1。<br /><br />警告層級 5: （遞迴使用在執行階段檢查） 21、 22 (**let rec**不按順序評估)，45 （完整摘要），到 52 （防禦複製）。 所有其他警告是層級 2。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[（& s) #47;，即發出警告 &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|**--warnon:&lt;int-list&gt;**|啟用特定的警告，可能會預設為關閉或停用另一個命令列選項。 在 F # 3.0 中，只有 1182 （未使用的變數） 警告預設為關閉。|
|**--warnaserror**[**+**&#124;**-**] [**&lt;int-list&gt;**]|啟用或停用報告警告視為錯誤的選項。 您可以提供特定的警告編號，停用或啟用。 稍後在命令列中的選項會覆寫稍早在命令列中的選項。 例如，若要指定您不想回報為錯誤的警告，請指定**-warnaserror +-warnaserror-:&lt;int 清單&gt;**。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; warnaserror &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|**--win32manifest:manifest-filename**|將 Win32 資訊清單檔案加入至編譯。 這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; win32manifest &#40;& #35。編譯器選項 &#41;](https://msdn.microsoft.com/library/bb545961.aspx).|
|**--win32res:resource-filename**|將 Win32 資源檔加入至編譯。<br /><br />這個編譯器選項相當於相同名稱的 C# 編譯器選項。 如需詳細資訊，請參閱[&#47; /win32res (&#40;& #35)。編譯器選項 &#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-topics"></a>相關主題


|標題|描述|
|-----|-----------|
|[F# Interactive 選項](fsharp-interactive-options.md)|描述 F # 解譯器，所支援的命令列選項 fsi.exe。|
|[專案屬性參考](/visualstudio/ide/reference/project-properties-reference)|描述專案，包括提供建置選項的專案屬性頁的 UI。|
