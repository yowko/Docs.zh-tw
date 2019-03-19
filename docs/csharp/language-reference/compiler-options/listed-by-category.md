---
title: 依分類列出的 C# 編譯器選項
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: bceb6283e202dfa699115edd6e0a1a040095783d
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "58028698"
---
# <a name="c-compiler-options-listed-by-category"></a>依分類列出的 C# 編譯器選項

下列編譯器選項會依類別排序。 如需依字母順序排列的清單，請參閱[依字母順序列出的 C# 編譯器選項](listed-alphabetically.md)。

## <a name="optimization"></a>最佳化

|選項|用途|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|指定輸出檔案中區段的大小。|
|[-optimize](optimize-compiler-option.md)|啟用/停用最佳化。|

## <a name="output-files"></a>輸出檔

|選項|用途|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|可讓編譯器輸出在輸入相同時編譯之間二進位內容相同的組件。|
|[-doc](doc-compiler-option.md)|指定要寫入已處理文件註解的 XML 檔案。|
|[-out](out-compiler-option.md)|指定輸出檔。|
|[-pathmap](pathmap-compiler-option.md)|指定編譯器所輸出來源路徑名稱的對應。|
|[-pdb](pdb-compiler-option.md)|指定 .pdb 檔案的檔案名稱和位置。|
|[-platform](platform-compiler-option.md)|指定輸出平台。|
|[-preferreduilang](preferreduilang-compiler-option.md)|指定編譯器輸出的語言。|
|[-refout](refout-compiler-option.md)|除了主要組件，再另外產生參考組件。|
|[-refonly](refonly-compiler-option.md)|產生參考組件，而非主要組件。|
|[-target](target-compiler-option.md)|使用下列五個選項之一來指定輸出檔案的格式：[-target:appcontainerexe](target-appcontainerexe-compiler-option.md)、[-target:exe](target-exe-compiler-option.md)、[-target:library](target-library-compiler-option.md)、[-target:module](target-module-compiler-option.md)、[-target:winexe](target-winexe-compiler-option.md) 或 [-target:winmdobj](target-winmdobj-compiler-option.md)。|
|-modulename:\<字串>|指定來源模組的名稱|

## <a name="net-framework-assemblies"></a>.NET Framework 組件

|選項|用途|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|指定要成為此組件一部分的一或多個模組。|
|[-delaysign](delaysign-compiler-option.md)|指示編譯器新增公開金鑰，但是讓組件不帶正負號。|
|[-keycontainer](keycontainer-compiler-option.md)|指定密碼編譯金鑰容器的名稱。|
|[-keyfile](keyfile-compiler-option.md)|指定包含密碼編譯金鑰的檔名。|
|[-lib](lib-compiler-option.md)|指定透過 [-reference](reference-compiler-option.md) 參考的組件位置。|
|[-nostdlib](nostdlib-compiler-option.md)|指示編譯器不要匯入標準程式庫 (mscorlib.dll)。|
|[-publicsign](publicsign-compiler-option.md)|套用公開金鑰而不簽署組件，但會在組件中設定此位元以表示該組件已經過簽署。|
|[-reference](reference-compiler-option.md)|從包含組件的檔案匯入中繼資料。|
|-analyzer|從這個組件執行分析器 (簡短形式：/a)|
|-additionalfile|命名不會直接影響程式碼產生，但可能被分析器用來產生錯誤或警告的其他檔案。|
|-embed|在 PDB 中內嵌所有來源檔案。|
|-embed:\<檔案清單>|在 PDB 中內嵌特定檔案。|
## <a name="debuggingerror-checking"></a>偵錯/錯誤檢查

|選項|用途|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|建立檔案，其中包含可簡化錯誤回報的資訊。|
|[-checked](checked-compiler-option.md)|指定超出資料類型範圍的整數算術，是否會導致在執行階段發生例外狀況。|
|[-debug](debug-compiler-option.md)|指示編譯器發出偵錯資訊。|
|[-errorreport](errorreport-compiler-option.md)|設定錯誤報告行為。|
|[-fullpaths](fullpaths-compiler-option.md)|在編譯器輸出中指定檔案的絕對路徑。|
|[-nowarn](nowarn-compiler-option.md)|抑制編譯器產生指定的警告。|
|[-warn](warn-compiler-option.md)|設定警告層級。|
|[-warnaserror](warnaserror-compiler-option.md)|將警告提升為錯誤。|
|-ruleset:\<檔案>|指定停用特定診斷的規則集檔案。|

## <a name="preprocessor"></a>前置處理器

|選項|用途|
|------------|-------------|
|[-define](define-compiler-option.md)|定義前置處理器符號。|

## <a name="resources"></a>資源

|選項|用途|
|------------|-------------|
|[-link](link-compiler-option.md)|將指定組件中的 COM 類型資訊提供給專案使用。|
|[-linkresource](linkresource-compiler-option.md)|建立與 Managed 資源的連結。|
|[-resource](resource-compiler-option.md)|將 .NET Framework 資源內嵌到輸出檔中。|
|[-win32icon](win32icon-compiler-option.md)|指定要插入輸出檔中的 .ico 檔案。|
|[-win32res](win32res-compiler-option.md)|指定要插入輸出檔中的 Win32 資源。|

## <a name="miscellaneous"></a>其他

|選項|用途|
|------------|-------------|
|[@](response-file-compiler-option.md)|指定回應檔。|
|[-?](help-compiler-option.md)|將編譯器選項列出至 stdout。|
|.[-baseaddress](baseaddress-compiler-option.md)|指定載入 DLL 時慣用的基底位址。|
|[-codepage](codepage-compiler-option.md)|指定編譯過程中所有原始程式碼檔使用的字碼頁。|
|[-help](help-compiler-option.md)|將編譯器選項列出至 stdout。|
|[-highentropyva](highentropyva-compiler-option.md)|指定可執行檔支援位址空間配置隨機載入 (ASLR)。|
|[-langversion](langversion-compiler-option.md)|指定語言版本：預設、ISO-1、ISO-2、3、4、5、6、7、7.1、7.2、7.3 或最新 |
|[-main](main-compiler-option.md)|指定 **Main** 方法的位置。|
|[-noconfig](noconfig-compiler-option.md)|指示編譯器不要使用 csc.rsp 進行編譯。|
|[-nologo](nologo-compiler-option.md)|隱藏編譯器橫幅資訊。|
|[-recurse](recurse-compiler-option.md)|搜尋要編譯之原始程式檔的子目錄。|
|[-subsystemversion](subsystemversion-compiler-option.md)|指定可執行檔能夠使用的最低子系統版本。|
|[-unsafe](unsafe-compiler-option.md)|啟用使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字的程式碼編譯。|
|[-utf8output](utf8output-compiler-option.md)|使用 UTF-8 編碼顯示編譯器輸出。|
|-parallel[+&#124;-]|指定是否要使用並行組建 (+)。|
|-checksumalgorithm:\<alg>|指定用於計算儲存在 PDB 的來源檔案總和檢查碼的演算法。  支援的值為：SHA1 (預設) 或 SHA256。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。|

## <a name="obsolete-options"></a>過時的選項

|選項|用途|
|---|---|
|-incremental|啟用累加編譯。|

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](index.md)
- [依字母順序列出 C# 編譯器選項](listed-alphabetically.md)
- [如何：為 Visual Studio 命令列設定環境變數](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
