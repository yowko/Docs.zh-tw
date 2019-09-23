---
title: 依分類列出 Visual Basic 編譯器選項
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 8f09566585c06531a346b0143a6002c2854a0b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182562"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>依分類列出的 Visual Basic 編譯器選項
提供 Visual Basic 的命令列編譯器, 做為從 Visual Studio 整合式開發環境 (IDE) 中編譯器的替代方案。 以下是依功能類別排序的 Visual Basic 命令列編譯器選項清單。  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>編譯器輸出  
  
|選項|用途|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|隱藏編譯器橫幅資訊。|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|使用 UTF-8 編碼顯示編譯器輸出。|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|在編譯期間輸出額外資訊。|  
|`-modulename:<string>`|指定來源模組的名稱|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|指定編譯器輸出的語言。|
  
## <a name="optimization"></a>最佳化  
  
|選項|用途|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|指定要對齊輸出檔案區段的位置。|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|啟用/停用最佳化。|  
  
## <a name="output-files"></a>輸出檔案  
  
|選項|用途|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|將文件註解處理成 XML 檔案。|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|可讓編譯器輸出在輸入相同時編譯之間二進位內容相同的組件。|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|設定編譯器以 .NET Compact Framework 為目標。|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|指定輸出檔。|  
|[-refonly](refonly-compiler-option.md)|只輸出參考元件。|
|[-refout](refout-compiler-option.md)|指定參考元件的輸出路徑。|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|指定輸出的格式。|  
  
## <a name="net-assemblies"></a>.NET 元件  
  
|選項|用途|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|指定將要完整簽署還是部分簽署組件。|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|從指定的組件匯入命名空間。|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|指定金鑰組的金鑰容器名稱，為組件提供強式名稱。|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|指定[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)選項所參考之元件的位置。|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|從組匯入中繼資料。|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|指定將包含模組的組件名稱。|  
|`-analyzer`|從這個組件執行分析器 (簡短形式：-a)|  
|`-additionalfile`|命名不會直接影響程式碼產生，但可能被分析器用來產生錯誤或警告的其他檔案。|  
  
## <a name="debuggingerror-checking"></a>調試/錯誤檢查  
  
|選項|用途|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|建立檔案，其中包含可簡化錯誤回報的資訊。|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|產生偵錯資訊。|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|抑制編譯器產生警告的功能。|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|防止編譯器顯示語法相關錯誤和警告的程式碼。|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|停用整數的溢位檢查。|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|將警告提升為錯誤。|  
|`-ruleset:<file>`|指定停用特定診斷的規則集檔案。|  
  
## <a name="help"></a>說明  
  
|選項|用途|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|顯示編譯器選項。 此命令的效用等同於指定 `-help` 選項。 未執行編譯。|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|顯示編譯器選項。 此命令的效用等同於指定 `-?` 選項。 未執行編譯。|  
  
## <a name="language"></a>語言  
  
|選項|用途|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|指定語言版本：9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|強制執行變數的明確宣告。|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|強制執行嚴格類型語意。|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|指定字串比較是否應為二進位，或是使用地區設定特定的文字語意。|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|可讓您在變數宣告中使用區域類型推斷。|  
  
## <a name="preprocessor"></a>前置處理器  
  
|選項|用途|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|定義條件式編譯的符號。|  
  
## <a name="resources"></a>資源  
  
|選項|用途|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|建立與 Managed 資源的連結。|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|將 Managed 資源內嵌至組件中。|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|將 .ico 檔插入輸出檔中。|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|將 Win32 資源插入輸出檔中。|  
  
## <a name="miscellaneous"></a>其他  
  
|選項|用途|  
|---|---|  
|[@ (指定回應檔)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|指定回應檔。|  
|.[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|指定 DLL 的基底位址。|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|指定編譯過程中所有原始程式碼檔使用的字碼頁。|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|指定 Visual Basic 編譯器應該如何報告內部編譯器錯誤。|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|指示 Windows 核心某一特定可執行檔是否支援高熵位址空間配置隨機載入 (ASLR)。|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|指定類別, 其中包含要`Sub Main`在啟動時使用的程式。|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|不使用 Vbc.rsp 進行編譯|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|使編譯器不要參考標準程式庫。|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|指定編譯器為輸出檔設為目標的處理器平台。|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|搜尋要編譯之原始程式檔的子目錄。|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|指定所有類型宣告的命名空間。|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|指定編譯器在編譯時不應使用 Visual Basic 執行階段程式庫的參考，或應使用特定執行階段程式庫的參考。|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。|  
|`-parallel[+&#124;-]`|指定是否要使用並行組建 (+)。|  
|`-checksumalgorithm:<alg>`|指定用於計算儲存在 PDB 的來源檔案總和檢查碼的演算法。  支援的值為：SHA1 (預設) 或 SHA256。 <br>由於 SHA1 的衝突問題, Microsoft 建議使用 SHA256 或更好的方式。|  
  
## <a name="see-also"></a>另請參閱

- [依字母順序列出 Visual Basic 編譯器選項](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [管理專案及解決方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
