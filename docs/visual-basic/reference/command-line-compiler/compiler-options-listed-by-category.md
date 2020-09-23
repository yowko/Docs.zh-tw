---
title: 依分類排列的編譯器選項
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 77a130b684d26cf7e4b9df9382348a371a60bc5d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072037"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>依類別列出的 Visual Basic 編譯器選項

Visual Basic 的命令列編譯器可作為從 Visual Studio 整合式開發環境（ (IDE) ）編譯器的替代方案。 以下是依功能類別目錄排序 Visual Basic 命令列編譯器選項的清單。  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>編譯器輸出  
  
|選項|目的|  
|---|---|  
|[-nologo](nologo.md)|隱藏編譯器橫幅資訊。|  
|[-utf8output](utf8output.md)|使用 UTF-8 編碼顯示編譯器輸出。|  
|[-verbose](verbose.md)|在編譯期間輸出額外資訊。|  
|`-modulename:<string>`|指定來源模組的名稱|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|指定編譯器輸出的語言。|
  
## <a name="optimization"></a>Optimization  
  
|選項|目的|  
|---|---|  
|[-filealign](filealign.md)|指定要對齊輸出檔案區段的位置。|  
|[-優化](optimize.md)|啟用/停用最佳化。|  
  
## <a name="output-files"></a>輸出檔案  
  
|選項|目的|  
|---|---|  
|[-doc](doc.md)|將文件註解處理成 XML 檔案。|  
|[-具決定性](deterministic.md)|可讓編譯器輸出在輸入相同時編譯之間二進位內容相同的組件。|
|[-netcf](netcf.md)|將編譯器設定為以 .NET Compact Framework 為目標。|  
|[-out](out.md)|指定輸出檔。|  
|[-refonly](refonly-compiler-option.md)|只輸出參考元件。|
|[-refout](refout-compiler-option.md)|指定參考元件的輸出路徑。|
|[-目標](target.md)|指定輸出的格式。|  
  
## <a name="net-assemblies"></a>.NET 組件  
  
|選項|目的|  
|---|---|  
|[-addmodule](addmodule.md)|讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。|  
|[-delaysign](delaysign.md)|指定將要完整簽署還是部分簽署組件。|  
|[-imports](imports.md)|從指定的組件匯入命名空間。|  
|[-keycontainer](keycontainer.md)|指定金鑰組的金鑰容器名稱，為組件提供強式名稱。|  
|[-keyfile](keyfile.md)|指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。|  
|[-libpath](libpath.md)|指定 [參考](reference.md) 選項所參考之元件的位置。|  
|[-reference](reference.md)|從組匯入中繼資料。|  
|[-moduleassemblyname](moduleassemblyname.md)|指定將包含模組的組件名稱。|  
|`-analyzer`|從這個組件執行分析器 (簡短形式：-a)|  
|`-additionalfile`|命名不會直接影響程式碼產生，但可能被分析器用來產生錯誤或警告的其他檔案。|  
  
## <a name="debuggingerror-checking"></a>調試/錯誤檢查  
  
|選項|目的|  
|---|---|  
|[-bugreport](bugreport.md)|建立檔案，其中包含可簡化錯誤回報的資訊。|  
|[-debug](debug.md)|產生偵錯資訊。|  
|[-nowarn](nowarn.md)|抑制編譯器產生警告的功能。|  
|[-quiet](quiet.md)|防止編譯器顯示語法相關錯誤和警告的程式碼。|  
|[-removeintchecks](removeintchecks.md)|停用整數的溢位檢查。|  
|[-warnaserror](warnaserror.md)|將警告提升為錯誤。|  
|`-ruleset:<file>`|指定停用特定診斷的規則集檔案。|  
  
## <a name="help"></a>説明  
  
|選項|目的|  
|---|---|  
|[-?](help.md)|顯示編譯器選項。 此命令的效用等同於指定 `-help` 選項。 未執行編譯。|  
|[-help](help.md)|顯示編譯器選項。 此命令的效用等同於指定 `-?` 選項。 未執行編譯。|  
  
## <a name="language"></a>Language  
  
|選項|目的|  
|---|---|  
|[-langversion](langversion.md)|指定語言版本： 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0。|  
|[-optionexplicit](optionexplicit.md)|強制執行變數的明確宣告。|  
|[-optionstrict](optionstrict.md)|強制執行嚴格類型語意。|  
|[-optioncompare](optioncompare.md)|指定字串比較是否應為二進位，或是使用地區設定特定的文字語意。|  
|[-optioninfer](optioninfer.md)|可讓您在變數宣告中使用區域類型推斷。|  
  
## <a name="preprocessor"></a>前置處理器  
  
|選項|目的|  
|---|---|  
|[-define](define.md)|定義條件式編譯的符號。|  
  
## <a name="resources"></a>資源  
  
|選項|目的|  
|---|---|  
|[-linkresource](linkresource.md)|建立與 Managed 資源的連結。|  
|[-資源](resource.md)|將 Managed 資源內嵌至組件中。|  
|[-win32icon](win32icon.md)|將 .ico 檔插入輸出檔中。|  
|[-win32resource](win32resource.md)|將 Win32 資源插入輸出檔中。|  
  
## <a name="miscellaneous"></a>其他  
  
|選項|目的|  
|---|---|  
|[@ (指定回應檔)](specify-response-file.md)|指定回應檔。|  
|[-baseaddress](baseaddress.md)|指定 DLL 的基底位址。|  
|[-字碼頁](codepage.md)|指定編譯過程中所有原始程式碼檔使用的字碼頁。|  
|[-errorreport](errorreport.md)|指定 Visual Basic 編譯器應該如何報告內部編譯器錯誤。|  
|[-highentropyva](highentropyva.md)|指示 Windows 核心某一特定可執行檔是否支援高熵位址空間配置隨機載入 (ASLR)。|  
|[-main](main.md)|指定包含啟動時所要使用之程式的類別 `Sub Main` 。|  
|[-noconfig](noconfig.md)|不使用 Vbc.rsp 進行編譯|  
|[-nostdlib](nostdlib.md)|使編譯器不要參考標準程式庫。|  
|[-nowin32manifest](nowin32manifest.md)|指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。|  
|[-platform](platform.md)|指定編譯器為輸出檔設為目標的處理器平台。|  
|[-遞迴](recurse.md)|搜尋要編譯之原始程式檔的子目錄。|  
|[-rootnamespace](rootnamespace.md)|指定所有類型宣告的命名空間。|  
|[-sdkpath](sdkpath.md)|指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。|  
|[-vbruntime](vbruntime.md)|指定編譯器在編譯時不應使用 Visual Basic 執行階段程式庫的參考，或應使用特定執行階段程式庫的參考。|  
|[-win32manifest](win32manifest.md)|識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。|  
|`-parallel[+&#124;-]`|指定是否要使用並行組建 (+)。|  
|`-checksumalgorithm:<alg>`|指定用於計算儲存在 PDB 的來源檔案總和檢查碼的演算法。  支援的值為：SHA1 (預設值) 或 SHA256。 <br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256 或更好的方式。|  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic Compiler Options Listed Alphabetically](compiler-options-listed-alphabetically.md)
- [管理專案和解決方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
