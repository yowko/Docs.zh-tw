---
title: Gacutil.exe (全域組件快取工具)
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- global assembly cache, manipulating contents
- GAC (global assembly cache), Gacutil.exe
- Gacutil.exe
- GAC (global assembly cache), viewing contents
- installing assemblies into global assembly cache
- removing assemblies from global assembly cache
- list of assemblies in global assembly cache
- cache [.NET Framework], global assembly cache
- GAC (global assembly cache), manipulating contents
- global assembly cache, Gacutil.exe
- Global Assembly Cache tool
ms.assetid: 4c7be9c8-72ae-481f-a01c-1a4716806e99
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 367bf566d63a81336daed8a4c1bfea3a184bcdf7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081771"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (全域組件快取工具)
全域組件快取工具可以讓您檢視和操作全域組件快取和下載快取的內容。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]  
```  
  
## <a name="parameters"></a>參數  
  
|引數|說明|  
|--------------|-----------------|  
|*assemblyName*|組件的名稱。 您可以提供如 `myAssembly` 的部分指定組件名稱，或如 `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5` 的完整指定組件名稱。|  
|*assemblyPath*|含有組件資訊清單 (Assembly Manifest) 的檔案名稱。|  
|*assemblyListFile*|列出要安裝或解除安裝之組件的 ANSI 文字檔路徑。 若要使用文字檔安裝組件，請在檔案的個別行上指定每個組件的路徑。 這個工具會解譯相對路徑 (相對於 *assemblyListFile* 的位置)。 若要使用文字檔來解除安裝組件，請在檔案的個別行上為每個組件指定完整的組件名稱。 請參閱本主題稍後的 *assemblyListFile* 內容範例。|  
  
|選項|說明|  
|------------|-----------------|  
|**/cdl**|刪除下載快取的內容。|  
|**/f**|請使用 **/** 或 **/il** 選項指定這個選項，以強制進行組件的重新安裝。 如果具有相同名稱的組件已存在於全域組件快取中，則這個工具會覆寫它。|  
|**/h**[**elp**]|顯示工具的命令語法和選項。|  
|**/i** *assemblyPath*|在全域組件快取中安裝單一組件。|  
|**/if**  *assemblyPath*|在全域組件快取中安裝單一組件。 如果具有相同名稱的組件已存在於全域組件快取中，則這個工具會覆寫它。<br /><br /> 指定這個選項相當於同時指定 **/i** 和 **/f** 選項。|  
|**/il** *assemblyListFile*|將 *assemblyListFile* 中指定的一或多個組件安裝到全域組件快取中。|  
|**/ir**  *assemblyPath*<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *描述*|將組件安裝到全域組件快取中，並新增參考以計數組件。 您必須使用這個選項指定 *assemblyPath*、*scheme*、*id* 和 *description* 參數。 如需可以為這些參數指定之有效值的描述，請參閱 **/r** 選項。<br /><br /> 指定這個選項相當於同時指定 **/i** 和 **/r** 選項。|  
|**/l** [*assemblyName*]|列出全域組件快取的內容。 如果您指定 *assemblyName*參數，這個工具只會列出符合該名稱的組件。|  
|**/ldl**|列出已下載之檔案快取的內容。|  
|**/lr** [*assemblyName*]|列出所有組件及其對應的參考計數。 如果您指定 *assemblyName* 參數，這個工具只會列出符合該名稱的組件及其對應的參考計數。|  
|**/nologo**|隱藏 Microsoft 程式啟始資訊顯示。|  
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *描述*|指定要安裝或解除安裝之組件的追蹤參考。 請使用 **/i**、**/il**、**/u** 或 **/ul** 選項指定這個選項。<br /><br /> 若要安裝組件，請使用這個選項指定 *assemblyPath*、*scheme*、*id* 及 *description* 參數。 若要解除安裝組件，請指定 *assemblyName*、*scheme*、*id* 和 *description* 參數。<br /><br /> 若要移除組件的參考，您必須在指定安裝組件時使用與 */i* 和 */r* (或 */ir*) 選項指定的相同 **scheme**、**id** 和 **description** 參數。 如果您正在解除安裝組件，並且這個組件是最後要移除的參考，且 Windows Installer 沒有這個組件的未解決參考，這個工具也會從全域組件快取中移除這個組件。<br /><br /> *scheme* 參數指定安裝配置的類型。 您可以指定下列其中一個值：<br /><br /> -   UNINSTALL_KEY：如果安裝程式將應用程式新增至 Microsoft Windows 中的 [新增/移除程式]，則指定這個值。 應用程式會將一個登錄機碼加入 HKLM\Software\Microsoft\Windows\CurrentVersion，以將其本身加入至 [新增或移除程式] 中。<br />-   FILEPATH：如果安裝程式沒有將應用程式新增至 [新增/移除程式] 中，則指定這個值。<br />-   OPAQUE：如果提供之登錄機碼或檔案路徑不適用於您的安裝情節，則指定這個值。 這個值允許您對 *id* 參數指定自訂資訊。<br /><br /> 要對 *id* 參數指定的值取決於對 *scheme* 參數指定的值：<br /><br /> 如果您對 *scheme* 參數指定 UNINSTALL_KEY，請在 HKLM\Software\Microsoft\Windows\CurrentVersion 登錄機碼中指定應用程式集的名稱。 例如，如果登錄機碼是 HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp，請對 *id* 參數指定 MyApp。<br />-   如果您對 *scheme* 參數指定 FILEPATH，請將安裝組件之可執行檔的完整路徑指定為 *id* 參數。<br />-   如果您對 *scheme* 參數指定 OPAQUE，則可以提供任何資料片段做為 *id* 參數。 您所指定的資料必須包含在引號 ("") 中。<br /><br /> *description* 參數允許您指定與要安裝之應用程式有關的描述文字。 這項資訊會在列舉參考時顯示。|  
|**/silent**|隱藏所有輸出的顯示。|  
|**/u**  *assemblyName*|解除安裝全域組件快取中的單一組件。|  
|**/uf**  *assemblyName*|移除組件的所有參考，強制解除安裝指定的組件。<br /><br /> 指定這個選項相當於同時指定 **/u** 和 **/f** 選項。 **注意：** 您無法使用這個選項移除使用 Microsoft Windows Installer 所安裝的組件。 如果您嘗試這項作業，工具就會顯示錯誤訊息。|  
|**/ul** *assemblyListFile*|從全域組件快取中解除安裝 *assemblyListFile* 中指定的一或多個組件。|  
|**/u**[**ngen**] *assemblyName*|從全域組件快取解除安裝指定的組件。 如果指定的組件具有現存的參考計數，工具就會顯示參考計數，並且不會從全域組件快取中移除組件。 **注意：** 在 .NET Framework 2.0 版中不支援 `/ungen`。 請改用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 的 `uninstall` 命令。 <br /><br /> 在 .NET Framework 1.0 和 1.1 版中，指定 **/ungen** 會使 Gacutil.exe 移除原生映像快取中的組件。 這個快取儲存了使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 建立之組件的原生映像。|  
|**/ur**  *assemblyName*<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *描述*|從全域組件快取解除安裝指定之組件的參考。 若要移除組件的參考，您必須在指定安裝組件時使用與 */i* 和 */r* (或 */ir*) 選項指定的相同 **scheme**、**id** 和 **description** 參數。 如需可以為這些參數指定之有效值的描述，請參閱 **/r** 選項。<br /><br /> 指定這個選項相當於同時指定 **/u** 和 **/r** 選項。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  您必須擁有系統管理員權限才能使用 Gacutil.exe。  
  
 具體來說，Gacutil.exe 可以讓您將組件安裝到快取、從快取中將它們移除，以及列出快取的內容。  
  
 Gacutil.exe 提供支援參考計數的選項，與 Windows Installer 所支援的參考計數配置相似。 您可以使用 Gacutil.exe 安裝兩個安裝相同組件的應用程式﹔這個工具會追蹤組件的參考數量。 因此，組件會保留在電腦上，直到兩個應用程式都解除安裝為止。 如果您使用 Gacutil.exe 進行實際的產品安裝，請使用支援參考計數的選項。 請同時使用 **/i** 和 **/r** 選項安裝組件，並加入要對組件計數的參考。 請同時使用 **/u** 和 **/r** 選項移除組件的參考計數。 請注意，單獨使用 **/i** 和 **/u** 選項並不支援參考計數。 這些選項適用於產品開發期間，但不適用於實際產品安裝。  
  
 請使用 **/il** 或 **/ul** 選項，安裝或解除安裝存放在 ANSI 文字檔中的組件清單。 文字檔的內容必須被正確格式化。 若要使用文字檔安裝組件，請在檔案的個別行上指定每個組件的路徑。 下列範例說明包含要安裝之組件的檔案內容。  
  
```  
myAssembly1.dll  
myAssembly2.dll  
myAssembly3.dll  
```  
  
 若要使用文字檔來解除安裝組件，請在檔案的個別行上為每個組件指定完整的組件名稱。 下列範例說明包含要解除安裝之組件的檔案內容。  
  
```  
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
```  

> [!NOTE]
>  嘗試安裝檔案名稱超過 79 到 91 個字元 (不含副檔名) 的組件，可能導致下列錯誤：
> ```
> Failure adding assembly to the cache:   The file name is too long.
> ```
> 這是因為 Gacutil.exe 在內部建構的路徑超過 MAX_PATH 個字元，其中包含下列元素：
> - GAC 根目錄 - 34 個字元 (即 `C:\Windows\Microsoft.NET\assembly\`)
> - 架構 - 7 或 9 個字元 (即 `GAC_32\`、`GAC_64\`、`GAC_MSIL`)
> - AssemblyName - 最多 91 個字元，根據其他元素的大小而定 (例如 `System.Xml.Linq\`)
> - AssemblyInfo - 31 到 48 個字元或以上，其中包含下列元素：
>   - Framework - 5 個字元 (例如 `v4.0_`)
>   - AssemblyVersion - 8 到 24 個字元 (例如 `9.0.1000.0_`)
>   - AssemblyLanguage - 1 到 8 個字元 (例如 `de_`、`sr-Cyrl_`)
>   - PublicKey - 17 個字元 (例如 `31bf3856ad364e35\`)
> - DllFileName - 最多 91 + 4 個字元 (即 `<AssemblyName>.dll`)

## <a name="examples"></a>範例  
 下列命令會將 `mydll.dll` 組件安裝到全域組件快取中。  
  
```  
gacutil /i mydll.dll  
```  
  
 只要組件的參考計數不存在，下列命令便會從全域組件快取中移除 `hello` 組件。  
  
```  
gacutil /u hello  
```  
  
 請注意，上述命令可能會從組件快取中移除一個以上的組件，因為沒有完整地指定組件名稱。 例如，如果快取中同時安裝了 `hello` 的 1.0.0.0 和 3.2.2.1 版本，`gacutil /u hello` 命令會將這兩個組件同時移除。  
  
 為避免移除一個以上的組件，請使用下列範例。 這個命令只會移除符合完整指定版本號碼、文化特性 (Culture) 和公開金鑰的 `hello` 組件。  
  
```  
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca  
```  
  
 下列命令會將 `assemblyList.txt` 檔案中所指定的組件安裝到全域組件快取中。  
  
 `gacutil /il assemblyList.txt`  
  
 下列命令會從全域組件快取中移除 `assemblyList.txt` 檔案中指定的組件。  
  
 `gacutil /ul assemblyList.txt`  
  
 下列命令會將 `myDll.dll` 安裝到全域組件快取中，並加入要計數的參考。 `myDll.dll` 組件是由 `MyApp` 應用程式使用。 `UNINSTALL_KEY MyApp` 參數指定將 `MyApp` 加入至 Windows 中 [新增或移除程式] 的登錄機碼。 說明參數指定為 `My Application Description`。  
  
```  
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"  
```  
  
 下列命令會將 `myDll.dll` 安裝到全域組件快取中，並加入要計數的參考。 配置參數 `FILEPATH` 和 id 參數 `c:\applications\myApp\myApp.exe`，指定安裝 `myDll.dll.` 之應用程式的路徑。說明參數指定為 `MyApp`。  
  
 `gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 下列命令會將 `myDll.dll` 安裝到全域組件快取中，並加入要計數的參考。 配置參數 `OPAQUE` 允許您自訂 id 和 description 參數。  
  
```  
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"  
```  
  
 下列命令會使用 `myDll.dll` 應用程式移除 `myApp` 的參考。 如果這是組件的最後一個參考，它也會從全域組件快取中移除這個組件。  
  
 `gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 下列命令會列出全域組件快取的內容。  
  
```  
gacutil /l  
```  
  
## <a name="see-also"></a>另請參閱

- [工具](../../../docs/framework/tools/index.md)
- [全域組件快取](../../../docs/framework/app-domains/gac.md)
- [Regasm.exe (組件登錄工具)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)
- [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
