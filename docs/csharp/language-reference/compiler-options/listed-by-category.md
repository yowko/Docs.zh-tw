---
title: "依分類列出的 C# 編譯器選項"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 410cad333b023e59d8c093d70d0e248504625dd6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="c-compiler-options-listed-by-category"></a>依分類列出的 C# 編譯器選項
下列編譯器選項會依類別排序。 如需依字母順序排列的清單，請參閱[依字母順序列出的 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)。  
  
### <a name="optimization"></a>最佳化  
  
|選項|用途|  
|------------|-------------|  
|[-filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|指定輸出檔案中區段的大小。|  
|[-optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|啟用/停用最佳化。|  
  
### <a name="output-files"></a>輸出檔  
  
|選項|用途|  
|------------|-------------|  
|[-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|指定要寫入已處理文件註解的 XML 檔案。|  
|[-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|指定輸出檔。|  
|[-pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|指定 .pdb 檔案的檔案名稱和位置。|  
|[-platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|指定輸出平台。|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|指定編譯器輸出的語言。|  
|[-refout](refout-compiler-option.md)|除了主要組件，再另外產生參考組件。|  
|[-refonly](refonly-compiler-option.md)|產生參考組件，而非主要組件。|  
|[-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|使用下列五個選項之一來指定輸出檔案的格式：[-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)、[-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)、[-target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)、[-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)、[-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) 或 [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)。|  
|-modulename:\<字串>|指定來源模組的名稱|  
  
### <a name="net-framework-assemblies"></a>.NET Framework 組件  
  
|選項|用途|  
|------------|-------------|  
|[-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|指定要成為此組件一部分的一或多個模組。|  
|[-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|指示編譯器新增公開金鑰，但是讓組件不帶正負號。|  
|[-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|指定密碼編譯金鑰容器的名稱。|  
|[-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|指定包含密碼編譯金鑰的檔名。|  
|[-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|指定透過 [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 參考的組件位置。|  
|[-nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|指示編譯器不要匯入標準程式庫 (mscorlib.dll)。|  
|[-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|從包含組件的檔案匯入中繼資料。|  
|-analyzer|從這個組件執行分析器 (簡短形式：/a)|  
|-additionalfile|命名不會直接影響程式碼產生，但可能被分析器用來產生錯誤或警告的其他檔案。|  
  
### <a name="debuggingerror-checking"></a>偵錯/錯誤檢查  
  
|選項|用途|  
|------------|-------------|  
|[-bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|建立檔案，其中包含可簡化錯誤回報的資訊。|  
|[-checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|指定超出資料類型範圍的整數算術，是否會導致在執行階段發生例外狀況。|  
|[-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|指示編譯器發出偵錯資訊。|  
|[-errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|設定錯誤報告行為。|  
|[-fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|在編譯器輸出中指定檔案的絕對路徑。|  
|[-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|抑制編譯器產生指定的警告。|  
|[-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|設定警告層級。|  
|[-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|將警告提升為錯誤。|  
|-ruleset:\<檔案>|指定停用特定診斷的規則集檔案。|  
  
### <a name="preprocessor"></a>前置處理器  
  
|選項|用途|  
|------------|-------------|  
|[-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|定義前置處理器符號。|  
  
### <a name="resources"></a>資源  
  
|選項|用途|  
|------------|-------------|  
|[-link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|將指定組件中的 COM 類型資訊提供給專案使用。|  
|[-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|建立與 Managed 資源的連結。|  
|[-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|將 .NET Framework 資源內嵌到輸出檔中。|  
|[-win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|指定要插入輸出檔中的 .ico 檔案。|  
|[-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|指定要插入輸出檔中的 Win32 資源。|  
  
### <a name="miscellaneous"></a>其他  
  
|選項|用途|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|指定回應檔。|  
|[-?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|將編譯器選項列出至 stdout。|  
|.[-baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|指定載入 DLL 時慣用的基底位址。|  
|[-codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|指定編譯過程中所有原始程式碼檔使用的字碼頁。|  
|[-help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|將編譯器選項列出至 stdout。|  
|[-highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|指定可執行檔支援位址空間配置隨機載入 (ASLR)。|  
|[-langversion](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|指定語言版本模式：Default、ISO-1、ISO-2、3、4、5、6、7、7.1 或 Latest |  
|[-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|指定 **Main** 方法的位置。|  
|[-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|指示編譯器不要使用 csc.rsp 進行編譯。|  
|[-nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|隱藏編譯器橫幅資訊。|  
|[-recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|搜尋要編譯之原始程式檔的子目錄。|  
|[-subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|指定可執行檔能夠使用的最低子系統版本。|  
|[-unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|啟用使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字的程式碼編譯。|  
|[-utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|使用 UTF-8 編碼顯示編譯器輸出。|  
|-parallel[+&#124;-]|指定是否要使用並行組建 (+)。|  
|-checksumalgorithm:\<alg>|指定用於計算儲存在 PDB 的來源檔案總和檢查碼的演算法。  支援的值為：SHA1 (預設值) 或 SHA256。|  
  
## <a name="obsolete-options"></a>過時的選項  
  
|選項|用途|  
|---|---|  
|-incremental|啟用累加編譯。|  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [依字母順序列出 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [如何：為 Visual Studio 命令列設定環境變數](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
