---
title: "依字母順序列出 C# 編譯器選項"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f4d7f1b122d3481dc8c3c5256ee361965846a830
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="c-compiler-options-listed-alphabetically"></a>依字母順序列出 C# 編譯器選項
下列編譯器選項會依字母順序排序。 如需分類清單，請參閱[依分類列出的 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-by-category.md)。  
  
|選項|用途|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|讀取回應檔以取得更多選項。|  
|[-?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|將使用方式訊息顯示到 stdout。|  
|-additionalfile|命名不會直接影響程式碼產生，但可能被分析器用來產生錯誤或警告的其他檔案。|  
|[-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|將指定的模組連結至此組件|  
|-analyzer|從這個組件執行分析器 (簡短形式：-a)|  
|[-appconfig](../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)|指定組件繫結時的 app.config 位置。|  
|.[-baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|指定要建置程式庫的基底位址。|  
|[-bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|建立「錯誤報告」檔案。 如果這個檔案與 -errorreport:prompt 或 -errorreport:send 搭配使用，就會與任何損毀資訊一併傳送。|  
|[-checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|會導致編譯器產生溢位檢查。|  
|-checksumalgorithm:\<alg>|指定用於計算儲存在 PDB 的來源檔案總和檢查碼的演算法。  支援的值為：SHA1 (預設值) 或 SHA256。|  
|[-codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|指定開啟原始程式檔時所要使用的字碼頁。|  
|[-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|發出偵錯資訊。|  
|[-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|定義條件式編譯符號。|  
|[-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|只使用強式名稱金鑰的公開部分來延遲簽署組件。|  
|[-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|指定要產生的 XML 文件檔案。|  
|[-errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|指定如何處理內部編譯器錯誤：prompt、send 或 none。 預設值是 [none]。|  
|[-filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|指定用來輸出檔案區段的對齊。|  
|[-fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|會導致編譯器產生完整的路徑。|  
|[-help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|將使用方式訊息顯示到 stdout。|  
|[-highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|指定支援高熵 ASLR。|  
|-incremental|啟用累加編譯 [已過時]。|  
|[-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|指定強式名稱金鑰容器。|  
|[-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|指定強式名稱金鑰檔。|  
|[-langversion:\<字串>](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|指定語言版本模式：Default、ISO-1、ISO-2、3、4、5、6、7、7.1 或 Latest |  
|[-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|指定要在其中搜尋參考的其他目錄。|  
|[-link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|將指定組件中的 COM 類型資訊提供給專案使用。|  
|[-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|將指定的資源連結至此組件。|  
|[-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|指定包含進入點 (忽略所有其他可能進入點) 的類型。|  
|[-moduleassemblyname](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)|指定 .netmodule 可以存取其非公用類型的組件。|  
|-modulename:\<字串>|指定來源模組的名稱|  
|[-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|指示編譯器不要自動包含 CSC.RSP 檔案。|  
|[-nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|隱藏編譯器著作權訊息。|  
|[-nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|指示編譯器不要參考標準程式庫 (mscorlib.dll)。|  
|[-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|停用特定的警告訊息|  
|[-nowin32manifest](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)|指示編譯器不要將應用程式資訊清單內嵌在可執行檔中。|  
|[-optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|啟用/停用最佳化。|  
|[-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|指定輸出檔案名稱 (預設：具有主要類別或第一個檔案的檔案基底名稱)。|  
|-parallel[+&#124;-]|指定是否要使用並行組建 (+)。|  
|[-pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|指定 .pdb 檔案的檔案名稱和位置。|  
|[-platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|限制此程式碼可以在哪些平台執行︰x86、Itanium、x64、anycpu 或 anycpu32bitpreferred。 預設為 anycpu。|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|指定編譯器輸出要使用的語言。|  
|[-recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|根據萬用字元的指定來加入目前目錄和子目錄中所有檔案。|  
|[-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|從指定的組件檔案參考中繼資料。|  
|[-refout](refout-compiler-option.md)|除了主要組件，再另外產生參考組件。|  
|[-refonly](refonly-compiler-option.md)|產生參考組件，而非主要組件。|  
|[-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|嵌入指定的資源。|  
|-ruleset:\<檔案>|指定停用特定診斷的規則集檔案。|  
|[-subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|指定可執行檔能夠使用的最低子系統版本。|  
|[-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|使用下列四個選項之一來指定輸出檔案的格式：[-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)、[-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)、[-target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)、[-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)、[-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)、[-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)。|  
|[-unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|允許 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 程式碼。|  
|[-utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|在 UTF-8 編碼中輸出編譯器訊息。|  
|[-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|設定警告層級 (0-4)。|  
|[-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|將特定警告報告為錯誤。|  
|[-win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|在輸出使用此圖示。|  
|[-win32manifest](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)|指定自訂 win32 資訊清單檔。|  
|[-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|指定 win32 資源檔案 (.res)。|  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [依分類列出的 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [如何：為 Visual Studio 命令列設定環境變數](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [\<編譯器> 項目](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
