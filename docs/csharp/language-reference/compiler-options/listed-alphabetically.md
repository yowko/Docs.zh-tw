---
title: 依字母順序列出 C# 編譯器選項
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alphabetically
- C# language, compiler options listed alphabetically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: 37eedc6d41867a6d5e6a49b8df5040c657bb2689
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602760"
---
# <a name="c-compiler-options-listed-alphabetically"></a>依字母順序列出 C# 編譯器選項

下列編譯器選項會依字母順序排序。 如需分類清單，請參閱[依分類列出的 C# 編譯器選項](listed-by-category.md)。

|選項|用途|
|------------|-------------|
|[@](response-file-compiler-option.md)|讀取回應檔以取得更多選項。|
|[-?](help-compiler-option.md)|將使用方式訊息顯示到 stdout。|
|-additionalfile|命名不會直接影響程式碼產生，但可能被分析器用來產生錯誤或警告的其他檔案。|
|[-addmodule](addmodule-compiler-option.md)|將指定的模組連結至此組件|
|-analyzer|從這個組件執行分析器 (簡短形式：-a)|
|[-appconfig](appconfig-compiler-option.md)|指定組件繫結時的 app.config 位置。|
|.[-baseaddress](baseaddress-compiler-option.md)|指定要建置程式庫的基底位址。|
|[-bugreport](bugreport-compiler-option.md)|建立「錯誤報告」檔案。 如果這個檔案與 -errorreport:prompt 或 -errorreport:send 搭配使用，就會與任何損毀資訊一併傳送。|
|[-checked](checked-compiler-option.md)|會導致編譯器產生溢位檢查。|
|-checksumalgorithm:\<alg>|針對儲存在 PDB 中的來源檔案總和檢查碼，指定計算所用的演算法。  支援的值為：SHA1 (預設) 或 SHA256。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。 |
|[-codepage](codepage-compiler-option.md)|指定開啟原始程式檔時所要使用的字碼頁。|
|[-debug](debug-compiler-option.md)|發出偵錯資訊。|
|[-define](define-compiler-option.md)|定義條件式編譯符號。|
|[-delaysign](delaysign-compiler-option.md)|只使用強式名稱金鑰的公開部分來延遲簽署組件。|
|[-deterministic](deterministic-compiler-option.md)|可讓編譯器輸出在輸入相同時編譯之間二進位內容相同的組件。|
|[-doc](doc-compiler-option.md)|指定要產生的 XML 文件檔案。|
|-embed|在 PDB 中內嵌所有來源檔案。|
|-embed:\<檔案清單>|在 PDB 中內嵌特定檔案。|
|-errorendlocation|輸出每個錯誤結束位置的行與列。|
|-errorlog:\<檔案>|指定檔案，記錄所有編譯器和分析器的診斷資料。|
|[-errorreport](errorreport-compiler-option.md)|指定如何處理內部編譯器錯誤：prompt、send 或 none。 預設值是 [none]。|
|[-filealign](filealign-compiler-option.md)|指定用來輸出檔案區段的對齊。|
|[-fullpaths](fullpaths-compiler-option.md)|會導致編譯器產生完整的路徑。|
|[-help](help-compiler-option.md)|將使用方式訊息顯示到 stdout。|
|[-highentropyva](highentropyva-compiler-option.md)|指定支援高熵 ASLR。|
|-incremental|啟用累加編譯 [已過時]。|
|[-keycontainer](keycontainer-compiler-option.md)|指定強式名稱金鑰容器。|
|[-keyfile](keyfile-compiler-option.md)|指定強式名稱金鑰檔。|
|[-langversion:\<字串>](langversion-compiler-option.md)|指定語言版本：預設、ISO-1、ISO-2、3、4、5、6、7、7.1、7.2、7.3 或最新 |
|[-lib](lib-compiler-option.md)|指定要在其中搜尋參考的其他目錄。|
|[-link](link-compiler-option.md)|將指定組件中的 COM 類型資訊提供給專案使用。|
|[-linkresource](linkresource-compiler-option.md)|將指定的資源連結至此組件。|
|[-main](main-compiler-option.md)|指定包含進入點 (忽略所有其他可能進入點) 的類型。|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|指定 .netmodule 可以存取其非公用類型的組件。|
|-modulename:\<字串>|指定來源模組的名稱|
|[-noconfig](noconfig-compiler-option.md)|指示編譯器不要自動包含 CSC.RSP 檔案。|
|[-nologo](nologo-compiler-option.md)|隱藏編譯器著作權訊息。|
|[-nostdlib](nostdlib-compiler-option.md)|指示編譯器不要參考標準程式庫 (mscorlib.dll)。|
|[-nowarn](nowarn-compiler-option.md)|停用特定的警告訊息|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|指示編譯器不要將應用程式資訊清單內嵌在可執行檔中。|
|[-optimize](optimize-compiler-option.md)|啟用/停用最佳化。|
|[-out](out-compiler-option.md)|指定輸出檔案名稱 (預設：具有主要類別或第一個檔案的檔案基底名稱)。|
|-parallel[+&#124;-]|指定是否要使用並行組建 (+)。|
|[-pathmap](pathmap-compiler-option.md)|指定編譯器所輸出來源路徑名稱的對應。|
|[-pdb](pdb-compiler-option.md)|指定 .pdb 檔案的檔案名稱和位置。|
|[-platform](platform-compiler-option.md)|限制此程式碼可以在哪些平台執行︰x86、Itanium、x64、anycpu 或 anycpu32bitpreferred。 預設為 anycpu。|
|[-preferreduilang](preferreduilang-compiler-option.md)|指定編譯器輸出要使用的語言。|
|[-publicsign](publicsign-compiler-option.md)|套用公開金鑰而不簽署組件，但會在組件中設定此位元以表示該組件已經過簽署。|
|[-recurse](recurse-compiler-option.md)|根據萬用字元的指定來加入目前目錄和子目錄中所有檔案。|
|[-reference](reference-compiler-option.md)|從指定的組件檔案參考中繼資料。|
|[-refout](refout-compiler-option.md)|除了主要組件，再另外產生參考組件。|
|[-refonly](refonly-compiler-option.md)|產生參考組件，而非主要組件。|
|-reportanalyzer|回報其他分析器資訊，例如執行時間。|
|[-resource](resource-compiler-option.md)|嵌入指定的資源。|
|-ruleset:\<檔案>|指定停用特定診斷的規則集檔案。|
|[-subsystemversion](subsystemversion-compiler-option.md)|指定可執行檔能夠使用的最低子系統版本。|
|[-target](target-compiler-option.md)|使用下列四個選項之一來指定輸出檔案的格式：[-target:appcontainerexe](target-appcontainerexe-compiler-option.md)、[-target:exe](target-exe-compiler-option.md)、[-target:library](target-library-compiler-option.md)、[-target:module](target-module-compiler-option.md)、[-target:winexe](target-winexe-compiler-option.md)、[-target:winmdobj](target-winmdobj-compiler-option.md)。|
|[-unsafe](unsafe-compiler-option.md)|允許 [unsafe](../keywords/unsafe.md) 程式碼。|
|[-utf8output](utf8output-compiler-option.md)|在 UTF-8 編碼中輸出編譯器訊息。|
|-version|顯示編譯器版本號碼並結束。|
|[-warn](warn-compiler-option.md)|設定警告層級 (0-4)。|
|[-warnaserror](warnaserror-compiler-option.md)|將特定警告報告為錯誤。|
|[-win32icon](win32icon-compiler-option.md)|在輸出使用此圖示。|
|[-win32manifest](win32manifest-compiler-option.md)|指定自訂 win32 資訊清單檔。|
|[-win32res](win32res-compiler-option.md)|指定 win32 資源檔案 (.res)。|

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](index.md)
- [依分類列出的 C# 編譯器選項](listed-by-category.md)
- [如何：為 Visual Studio 命令列設定環境變數](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<編譯器> 項目](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
