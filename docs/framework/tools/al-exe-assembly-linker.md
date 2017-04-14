---
title: "Al.exe (組件連結器) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Al.exe"
  - "組件連結器"
  - "模組, 組件連結器"
  - "組件資訊清單, 組件連結器"
ms.assetid: b5382965-0053-47cf-b92f-862860275a01
caps.latest.revision: 37
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 37
---
# Al.exe (組件連結器)
組件連結器 (Assembly Linker) 會從一個或多個模組或資源檔中產生一個包含組件資訊清單的檔案。 模組是不包含組件資訊清單的中繼語言 (IL) 檔案。  
  
> [!NOTE]
>  為避免受 Windows Vista 電腦上的虛擬化所限制，您的組件必須包含 Win32 資訊清單 (其指定所要求的執行層級)。 當您直接從命令列使用 al.exe 時，可以將資訊清單嵌入 Win32 資源檔，或者使用 mt.exe 在後續建置程序中附加資訊清單。 從 [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)] 開始，C# 和 Visual Basic 編譯器都會自動將 Win32 資訊清單嵌入組件中。 如需詳細資訊，請參閱[/win32manifest （C# 編譯器選項）](../Topic/-win32manifest%20\(C%23%20Compiler%20Options\).md)。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
al sources options  
```  
  
#### <a name="parameters"></a>參數  
 您可以指定一個或多個下列 `sources`。  
  
|來源|描述|  
|------------|-----------------|  
|`file`[,`target`]|將 `file` (模組) 的內容複製到 `target` 所指定的檔案名稱中。 複製完成後，Al.exe 會將 `target` 編譯成組件。|  
|**/embed**[`resource`]`:``file`[,`name`[,`private`]]|將 `file` 所指定的資源嵌入包含組件資訊清單的映像中，Al.exe 會將 `file` 的內容複製到可攜式執行檔 (PE) 映像中。<br /><br /> `name` 參數是資源的內部識別項。 根據預設，組件中的資源為公用 (其他組件也可看見)。 指定 `private` 會使其他組件無法看見資源。<br /><br /> 如果`file`是.NET Framework 建立的資源檔，例如，由[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)或在開發環境中，它可以存取與其中成員保持<xref:System.Resources>。 如需詳細資訊，請參閱<xref:System.Resources.ResourceManager>。 如需其他資源，使用`GetManifestResource`* 方法在<xref:System.Reflection.Assembly>在執行階段存取資源。<br /><br /> 如果只將資源檔傳遞至 Al.exe，則輸出檔會是附屬資源組件。|  
|**/link**[`resource`]:`file`[,`name`[,`target`[,`private`]]]|將資源檔連結至組件。 `file` 所指定的資源會變成組件的一部分，但是不會複製檔案。 `file` 參數可以是任何檔案格式。 例如，您可以指定原生 DLL 做為 `file` 參數。 這樣就會產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。 您也可以執行此使用**/linkresource**編譯器選項。 如需詳細資訊，請參閱[/linkresource （C# 編譯器選項）](../Topic/-linkresource%20\(C%23%20Compiler%20Options\).md)。<br /><br /> `name`參數是資源的內部識別項。 `target`參數會指定 Al.exe 複製路徑和檔案名稱`file` *。* 複製完成後，Al.exe 會將 `target` 編譯成組件。 根據預設，組件中的資源為公用 (其他組件也可看見)。 指定 `private` 會使其他組件無法看見資源。<br /><br /> 如果`file`是.NET Framework 資源檔建立，例如，由資源檔產生器 (Resgen.exe) 或是在開發環境中，可存取之成員<xref:System.Resources>命名空間。 如需詳細資訊，請參閱<xref:System.Resources.ResourceManager>。 如需其他資源，使用`GetManifestResource`* 方法中的<xref:System.Reflection.Assembly>類別，以在執行階段存取資源。<br /><br /> 如果只將資源檔傳遞至 Al.exe，則輸出檔會是附屬資源組件。|  
  
 您可以指定下列`options`; 您必須指定**/out**。  
  
|選項|說明|  
|------------|-----------------|  
|**/ algid**:`id`|指定雜湊多檔案組件中所有檔案的演算法，但包含組件資訊清單的檔案除外。 預設演算法為 CALG_SHA1。 如需其他演算法，請參閱 Platform SDK 文件中的 ALG_ID。 對於第一版 .NET Framework，只有 CALG_SHA1 和 CALG_MD5 有效。<br /><br /> 雜湊值儲存在組件資訊清單的檔案表中。 在安裝和載入期間，系統會根據雜湊來檢查組件的檔案。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyAlgorithmIdAttribute>) 中的任何模組的原始程式碼。|  
|**/base**[`address`]:`addr`|指定在執行期間將 DLL 載入使用者電腦上的目標位址。 如果您指定 DLL 的基底位址，而不是讓作業系統重新找出處理序空間中的 DLL，應用程式載入的速度會更快。|  
|**/bugreport**:`filename`|建立包含回報 Bug 所需資訊的檔案 (`filename`)。|  
|**/comp**[`any`]:`text`|為組件中的 [公司] 欄位指定字串。 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果您未指定**/win32res**，`text`會出現在檔案總管中，成為`Company`之檔案屬性。 如果您指定**/win32res**，在指定的資源檔中的公司資訊會顯示為`Company`檔案總管 中的屬性。<br /><br /> 如果文字為空字串 ("")，Win32 `Company` 資源會顯示為單一空格。<br /><br /> 如果您指定**/win32res**， **/公司**將不會影響 Win32 資源資訊。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyCompanyAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/config**[`uration`]:`text`|為組件中的 [組態] 欄位指定字串。 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果文字為空字串，Win32 Configuration 資源會顯示為單一空格。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyConfigurationAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/copy**[`right`]:`text`|為組件中的 [著作權] 欄位指定字串。 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果您未指定**/win32res**， **/著作權**為著作權 Win32 資源檔案總管 中會出現。<br /><br /> 如果文字為空字串，Win32 Copyright 資源會顯示為單一空格。<br /><br /> 如果您指定**/win32res**， **/著作權**將不會影響 Win32 資源資訊。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyCopyrightAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/c**[**ulture**]:`text`|指定與組件相關聯的文化特性字串。 文化特性的有效值為標題＜Tags for the Identification of Languages＞的＜Internet Requests for Comments (RFC) 1766＞文件中定義的值。<br /><br /> 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 沒有預設的文化特性字串。 這個字串可使用反映進行檢視。<br /><br /> 如需有效`text`字串，請參閱<xref:System.Globalization.CultureInfo>。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyCultureAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/delay**[`sign`][`+&#124;-`]|指定將要完整簽署還是部分簽署組件。 使用**/delaysign-**如果要完整簽署組件。 使用**/delaysign+**如果您只想要包含組件中的公開金鑰。<br /><br /> 當您要求完整簽署的組件時，Al.exe 會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署雜湊。 所產生的數位簽章會儲存在包含資訊清單的檔案中。 當組件延遲簽署時，Al.exe 不會計算和儲存該簽章，只會在檔案中保留空間，以便稍後再加入該簽章。<br /><br /> 預設值是**/delaysign-**。<br /><br /> **/Delaysign**選項沒有任何作用，除非搭配**/keyfile**或**/keyname**。<br /><br /> 例如，使用**/delaysign+**可讓測試人員將組件置於全域快取中。 測試過後，您就可以將私密金鑰包含在組件內，藉此完整簽署組件。<br /><br /> 注意︰ 使用之前[Gacutil.exe （全域組件快取工具）](../../../docs/framework/tools/gacutil-exe-gac-tool.md)將延遲簽署組件放入全域快取中，使用[Sn.exe （強式名稱工具）](../../../docs/framework/tools/sn-exe-strong-name-tool.md)註冊組件，以略過驗證。 例如，`Sn.exe –Vr delaySignedAssembly`。 這種方式僅適用於開發工作。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyDelaySignAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/descr**[**iption**]**:**`text`|指定的字串<xref:System.Reflection.AssemblyDescriptionAttribute.Description%2A>組件中的欄位。 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果您未指定**/win32res**， **myapplication /description**會出現在檔案總管 中為 Win32**註解**資源。<br /><br /> 如果文字為空字串，Win32**註解**資源會顯示為單一空格。<br /><br /> 如果您指定**/win32res**， **myapplication /description**將不會影響 Win32 資源資訊。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyDescriptionAttribute.Description%2A>) 在任何 MSIL 模組的原始程式碼。|  
|**/e [vidence]:**`file`|使用 Security.Evidence 的資源名稱將 `file` 嵌入組件中。<br /><br /> Security.Evidence 無法用於一般資源。|  
|**/fileversion:**`version`|指定的字串**檔案版本**組件中的欄位。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果您未指定**/win32res**， **/fileversion**做為 Win32**檔案版本**資源。 如果您未指定**/fileversion**，Win32**檔案版本**資源中將填入 win32**組件版本**資源。<br /><br /> 如果**/win32res**指定，則**/fileversion**並不會影響 Win32 資源。<br /><br /> 您也可以在任何 MSIL 模組的原始程式碼中指定這個選項做為自訂屬性 (AssemblyFileVersionAttribute)。|  
|**/ 加上旗標︰**`flags`|為組件中的 [`Flags`] 欄位指定值。 `flags` 的可能值如下：<br /><br /> 0x0000<br /> 組件可並存相容。<br /><br /> 0x0010<br /> 如果組件在相同的應用程式定義域中執行時，就無法與其他版本一起執行。<br /><br /> 0x0020<br /> 如果組件在相同的處理序中執行，就無法與其他版本一起執行。<br /><br /> 0x0030<br /> 如果組件與其他版本位於同一部電腦上，就無法與其他版本一起執行。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyFlagsAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/fullpaths**|讓 Al.exe 使用錯誤訊息中所報告任何檔案的絕對路徑。|  
|**/help**|顯示工具的命令語法和選項。|  
|**/keyf [ile]:**`filename`|指定包含金鑰組或只有公開金鑰的檔案 (`filename`)，用以簽署組件。 編譯器會將公開金鑰插入組件資訊清單中，然後使用私密金鑰簽署最終組件。 請參閱[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)如需產生金鑰檔，以及將金鑰組安裝在金鑰容器。<br /><br /> 如果您使用延遲簽署，這個檔案通常會包含公開金鑰，但不會包含私密金鑰。<br /><br /> (金鑰組的) 公開金鑰資訊會出現在組件的 [.publickey] 欄位中。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) 在任何 MSIL 模組的原始程式碼。<br /><br /> 如果兩個**/keyfile**和**/keyname**指定 （命令列選項或是自訂屬性） 在相同編譯中，Al.exe 會先嘗試使用指定的容器**/keyname**。 如果這個動作成功，那麼組件就會使用金鑰容器中的資訊進行簽署。 如果 Al.exe 找不到金鑰容器，將會嘗試使用指定的檔案**/keyfile**。 如果成功，組件已簽署的金鑰檔中的資訊和金鑰資訊會安裝在金鑰容器中 (類似於-i 選項[Sn.exe](../../../docs/framework/tools/sn-exe-strong-name-tool.md)) 以便在下次編譯時， **/keyname**選項才有效。|  
|**/keyn \ [名稱]:**`text`|指定保留金鑰組的容器。 這樣會藉由將公開金鑰插入組件資訊清單中的方式簽署組件 (為它指定強式名稱)。 然後 Al.exe 將會使用私密金鑰簽署最終組件。<br /><br /> 請使用 Sn.exe 產生金鑰組。<br /><br /> 金鑰資訊會出現在組件的 [.publickey] 欄位中。<br /><br /> 如果有內嵌空格，請將 `text` 置於雙引號 (" ") 內。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/main:**`method`|指定將模組轉換成可執行檔時，用來做為進入點之方法的完整名稱 (`class`.`method`)。|  
|**/nologo**|隱藏叫用 Al.exe 時命令列中顯示的橫幅或標誌。|  
|**/out:**`filename`|指定 Al.exe 所產生檔案的名稱。 這是必要選項。|  
|**/platform**:`text`|限制可以執行這個程式碼的平台，這個平台必須下列其中之一：x86、Itanium、x64、anycpu (預設值) 或 anycpu32bitpreferred。|  
|**/ 生產環境 [utc]:**`text`|指定的字串**產品**組件中的欄位。 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果您未指定**/win32res**， **/product**會出現在檔案總管 中為 Win32**產品名稱**資源。<br /><br /> 如果文字為空字串，Win32**產品名稱**資源會顯示為單一空格。<br /><br /> 如果您指定**/win32res**， **/product**將不會影響 Win32 資源資訊。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyProductAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/productv [版本]:**`text`|指定的字串**產品版本**組件中的欄位。 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果您未指定**/win32res**， **/productversion**做為 Win32**產品版本**資源。 如果您未指定**/productversion**，Win32**產品版本**資源中將填入 win32**檔案版本**資源。<br /><br /> 如果您指定**/win32res**， **/productversion**將不會影響 Win32 資源資訊。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyInformationalVersionAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**[arget] /t: lib [rary] |exe |win [exe]**|指定輸出檔的檔案格式：lib[rary] (程式碼程式庫)、exe (主控台應用程式) 或 win[exe] (Windows 應用程式)。 預設值為 lib[rary]。|  
|**/template:**`filename`|指定要從其中繼承所有組件中繼資料的組件 `filename`，但不包括 [文化特性] 欄位。<br /><br /> 使用您建立的組件**/template**將會是附屬組件。|  
|**/ t:**`text`|指定的字串**標題**組件中的欄位。 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果您未指定**/win32res**， **/t**會出現在檔案總管 中為 Win32**描述**資源，可做為殼層應用程式的易記名稱。 它也會顯示在**開啟**子功能表中的檔案類型，針對有多個支援的應用程式的捷徑功能表。<br /><br /> 如果文字為空字串，Win32**描述**資源會顯示為單一空格。<br /><br /> 如果您指定**/win32res**， **/t**將不會影響 Win32 資源資訊。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyTitleAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/ 交換 [標記]:**`text`|指定的字串**商標**組件中的欄位。 如果 `text` 包含空格，請將字串置於雙引號內 (" ")。 這個字串是組件的自訂屬性，可使用反映進行檢視。<br /><br /> 如果您未指定**/win32res**， **/商標**會出現在檔案總管 中為 Win32**商標**資源。<br /><br /> 如果文字為空字串，Win32**商標**資源會顯示為單一空格。<br /><br /> 如果您指定**/win32res**， **/商標**將不會影響 Win32 資源資訊。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyTrademarkAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**[版本] /v:**`version`|指定這個組件的版本資訊。 版本字串的格式為 `major`.`minor`.`build`.`revision`。 預設值為 0。<br /><br /> 如果您指定**/version**，您必須指定`major`。 如果您指定`major`和`minor`，您可以指定星號 (\*) 的`build`。 這樣一來，`build` 就相當於自當地時間 2000 年 1 月 1 日起算的天數，而 `revision` 則等於自當地時間當天午夜起算的秒數除以 2。<br /><br /> 如果您指定 `major`、`minor` 和 `build`，則可以指定星號代表 `revision`。 這樣一來，`revision` 就等於自當地時間當天午夜起算的秒數除以 2。<br /><br /> 簡單來說，有效的版本字串如下：<br /><br /> X<br /><br /> X.X<br /><br /> X.X.\*<br /><br /> X.X.X<br /><br /> X.X.X.\*<br /><br /> X.X.X.X<br /><br /> 其中 X 是指任何不帶正負號的簡短常數，但 65535 除外 (0-65534)。<br /><br /> 如果您未指定**/win32res**， **/version**做為 Win32**組件版本**資源。<br /><br /> 如果您未指定**/win32res**， **/productversion**，和**/fileversion**， **/version**將用於**組件版本**，檔案版本和**產品版本**Win32 資源。<br /><br /> 如果您指定**/win32res**， **/version**將不會影響 Win32 資源資訊。<br /><br /> 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyVersionAttribute>) 在任何 MSIL 模組的原始程式碼。|  
|**/win32icon:**`filename`|將 .ico 檔案插入組件中。 .ico 檔案會讓輸出檔在檔案總管中以所要的外觀顯示。|  
|**/win32res:**`filename`|將 Win32 資源 (.res 檔案) 插入輸出檔中。 您可以使用資源編譯器建立 Win32 資源檔。 資源編譯器是在編譯 Visual C++ 程式時叫用，而 .res 檔案則是從 .rc 檔案建立。|  
|`@filename`|指定包含 Al.exe 命令的回應檔。<br /><br /> 回應檔中的命令可顯示為一行一個，也可以全部顯示在同一行，並以一個或多個空格加以分隔。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 所有 Visual Studio 編譯器都會產生組件。 但是，如果您有一個或多個模組 (不含資訊清單的中繼資料)，就可以使用 Al.exe 在另一個檔案中建立包含資料清單的組件。  
  
 若要安裝的組件快取中，從快取中移除組件或清單的快取的內容，請使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)。  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 下表列出 Al.exe 所產生的錯誤。  
  
|錯誤|描述|  
|-----------|-----------------|  
|al1001|內部編譯器錯誤<br /><br /> 請嘗試判斷 Al.exe 失敗的原因是否為無法剖析未預期的語法。 然後，請連絡 Microsoft 產品支援服務。|  
|al1002|記憶體不足<br /><br /> Al.exe 因記憶體不足而停止。 請增加可用記憶體的數量。|  
|al1003|編譯器選項 'option' 後面必須使用引數<br /><br /> Al.exe 必須有傳遞至命令列選項的引數。 例如，如果您指定**/ algid:**，您必須傳遞演算法識別項。|  
|al1004|未預期的 Common Language Runtime 初始化錯誤 — 'reason'<br /><br /> Al.exe 報告因指定原因而造成 Visual Studio 或 Common Language Runtime 安裝錯誤。|  
|al1005|檔案 'file' 太大，無法開啟<br /><br /> Al.exe 開啟的所有檔案必須小於 4 GB。|  
|al1006|已經包含回應檔 'file'<br /><br /> 相同的回應檔 (`@file`) 在命令列中指定多次。 回應檔只能包含一次。|  
|al1007|開啟回應檔 'file' 時發生錯誤 — 'reason'<br /><br /> Al.exe 因指定原因而無法開啟指定的回應檔。|  
|al1008|遺漏 'option' 命令列選項的檔案規格<br /><br /> Al.exe 必須有傳遞至命令列選項的檔案。 例如，如果您指定**/out**選項時，您必須指定一個檔案。|  
|al1009|無法開啟 'file' 進行寫入<br /><br /> Al.exe 無法寫入檔案，例如輸出組件檔。 可能是磁碟已滿、檔案為唯讀，或沒有檔案的權限。|  
|al1010|命令列語法錯誤: 遺漏 'option' 選項的 ':text'<br /><br /> Al.exe 必須有傳遞至命令列選項的引數。 例如，如果您指定**/t**選項時，您必須傳遞字串。|  
|al1011|檔案 'file' 是可執行檔，無法當做文字檔開啟<br /><br /> 必須是文字檔，但卻指定了二進位檔。 例如，如果在命令列上將二進位檔當做回應檔傳遞，便會發生這個錯誤。|  
|al1012|'value' 不是選項 'option' 的有效設定<br /><br /> 傳遞至命令列選項的值是未預期的值。 例如，如果您指定無效值而發生此錯誤**/目標**選項。|  
|al1013|無法辨認的命令列選項: 'option'<br /><br /> 指定的命令列選項無效。|  
|al1014|未預期的初始化錯誤 — 'reason'<br /><br /> Al.exe 偵測到 COM 初始化失敗。 可能是由於記憶體不足所造成，更可能的原因是系統的 DLL 檔案。 如果執行任何自動化感知或 COM 感知程式 (例如 Microsoft Visual Studio)，可能會看見類似的錯誤。<br /><br /> 請重新安裝作業系統。|  
|al1015|找不到訊息檔案 'alinkui.dll'<br /><br /> Al.exe 需要 Alinkui.dll。 請確定這個檔案在路徑中。 如有必要，請從產品光碟複製這個檔案。|  
|al1016|未指定有效的輸入檔<br /><br /> Al.exe 需要一或多個不含組件資訊的輸入檔。|  
|al1017|未指定目標檔名<br /><br /> 必要**/out**遺漏指定目標檔名的選項。|  
|al1018|無法載入必要的檔案 'file'<br /><br /> 無法載入特定 DLL 檔。 請重新安裝 Visual Studio 或 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]。|  
|al1019|建立組件期間發生中繼資料錯誤 — 原因<br /><br /> 產生組件時因指定原因而中斷。 例如，如果您使用指定的檔案而發生此錯誤**/win32res**找不到選項。|  
|al1020|忽略包含的組件 'file'<br /><br /> 指定的輸入檔包含組件。 Al.exe 輸入檔不能包含組件。|  
|al1021|'setting' : 正在覆寫先前的設定<br /><br /> 模組具有可能透過自訂屬性指派的特定設定值，但已遭到使用 Al.exe 命令列選項傳遞的值覆寫。|  
|al1022|讀取內嵌的資源 'file' 時發生錯誤 — 原因<br /><br /> Al.exe 無法讀取檔案傳遞至**/embedresource**選項因指定原因。|  
|al1023|嵌入資源 'file' 時發生錯誤 — 原因<br /><br /> 作業系統因指定原因而無法將資源檔嵌入組件中。|  
|al1025|ComType 記錄 'record' 指向無效的檔案記錄 'record'<br /><br /> 輸入模組中的中繼資料無效。 產生模組的工具必須固定。|  
|al1026|指定的版本 'version' 無效<br /><br /> 顯示相關資訊， **/version**有效格式的選項。|  
|al1028|金鑰檔 'file' 遺漏簽署所需的私密金鑰<br /><br /> 只包含公開金鑰的金鑰檔案傳遞給**/keyfile**選項。 使用[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)來產生檔案具有這兩個公用和私人金鑰，如下列命令中所示。<br /><br /> `sn -k keypair.snk.`|  
|al1029|金鑰容器名稱 'container' 不存在<br /><br /> 若要傳遞的值**/keyname**選項不是有效的容器。 使用[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)建立容器。|  
|al1030|未妥善安裝密碼編譯服務或缺乏適當的金鑰提供者<br /><br /> 您可能必須重新安裝作業系統，或安裝用來建立金鑰的特定密碼編譯公用程式。|  
|al1031|讀取圖示 'file' 時發生錯誤 — 原因<br /><br /> Al.exe 無法讀取檔案傳遞給**/win32icon**選項因指定原因|  
|al1032|產生 'file' 的資源時發生錯誤 — 原因<br /><br /> Al.exe 因磁碟空間不足或其他一些錯誤而無法建立檔案。 當您指定時，會發生此錯誤**/win32icon**選項 （產生.ico 檔），或不指定**/win32res**選項 （產生包含資源資訊的檔案）。<br /><br /> 如果您無法解決檔案產生問題，請使用**/win32res**，指定的檔案可以包含版本或點陣圖 （圖示） 資訊。|  
|al1033|已經多次以不同的值指定組件自訂屬性 'attribute'<br /><br /> 在指定為 Al.exe 輸入的來源模組中，將不同的值傳遞給相同自訂屬性的兩個項目。|  
|al1034|組件 'file' 無法被複製或重新命名<br /><br /> 雖然使用 Al.exe 語法可讓您指定和複製輸入檔，但是會發生名稱衝突，使編譯器停止。 例如，如果您指定 `input.dll,somename.dll /out:somename.dll`，便會發生這個錯誤。|  
|al1035|程式庫無法有進入點<br /><br /> 您無法同時指定**/target:lib**選項 （預設值） 和**/main**選項。|  
|al1036|可執行應用程式必須有進入點<br /><br /> 當使用**/target: exe**或**/target:win**選項時，您也必須指定**/main**選項。|  
|al1037|找不到進入點方法 'main'<br /><br /> 找不到 Al.exe`Main`方法所指定的位置處**/main**選項。|  
|al1039|全域組件快取管理員初始化失敗 — 原因<br /><br /> 請重新安裝 Visual Studio 或 [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]。|  
|al1040|無法將組件安裝至快取 — 原因<br /><br /> 只有簽署的組件才能安裝至快取。 請參閱[全域組件快取](../../../docs/framework/app-domains/gac.md)如需詳細資訊。|  
|al1041|'method': 因為簽章或可見度不正確，或者其為泛型，所以無法成為進入點<br /><br /> 一種方法所指定的**/main**選項，但該方法不是靜態，不會傳回`int`或`void`、 為泛型，或包含無效的引數。|  
|al1042|'exe': 無法將 EXE 加入模組<br /><br /> 已將不含組件的 .exe 檔指定為 Al.exe 的輸入檔。 Al.exe 只能將不含組件的 .dll 檔當做輸入檔。|  
|al1043|資訊清單檔名 'name' 不可與任何模組相同<br /><br /> 指定的名稱與**/out**選項不能是任何一個指定為 al.exe 輸入的檔案名稱相同。|  
|al1044|讀取金鑰檔 'file' 時發生錯誤 — 原因<br /><br /> 開啟或從指定的檔案讀取時發生錯誤**/keyfile**或<xref:System.Reflection.AssemblyKeyFileAttribute>。|  
|al1045|檔名 'file' 太長或無效<br /><br /> 傳遞至 Al.exe 的檔名超過 260 個字元。 請選擇字元較少或路徑較短的檔名，或重新命名檔案。|  
|al1046|在這個組件中已經使用過資源識別項 'ID'<br /><br /> 兩個內嵌或連結的資源具有相同的識別項或名稱 (第二個引數)。 請將其中一個衝突的資源移除或重新命名。|  
|al1047|匯入檔案 'file' 時發生錯誤 — 原因<br /><br /> 模組檔案因指定原因而無法開啟。|  
|al1048|匯入模組 'module' (屬於組件 'assembly') 時發生錯誤 — 原因<br /><br /> 開啟多檔案組件的非資訊清單檔時發生錯誤。 這個錯誤並不是由 Al.exe 直接發出，但是可以利用程式設計方式傳遞至使用 Al.exe 的處理序。|  
|al1049|無法自動產生日期早於 2000 年 1 月 1 日的組建與修訂版本號碼<br /><br /> 電腦上所設定的系統時間日期早於 2000 年 1 月 1 日。|  
|al1050|不再支援您正使用的 'old feature' 功能; 請改用 'new feature'<br /><br /> Al.exe 先前支援的功能已經過時。 請改用建議的功能。|  
|al1051|發出 'attribute' 屬性時發生錯誤 — '原因'<br /><br /> Al.exe 因指定原因而未處理組件自訂屬性。|  
|al1052|檔案 'filename' 不是組件<br /><br /> 使用指定的檔案**/template**必須包含組件中繼資料。 此錯誤表示所指定的檔案**/template**未包含組件。|  
|al1053|版本 'version' (指定給 'option') 不是使用一般的 'major.minor.build.revision' 格式<br /><br /> Al.exe 偵測到與指定的格式不正確的版本資訊**/fileversion**或**/productversion**選項。|  
|al1054|版本 'version' (指定給 'option') 不是使用一般的 'major.minor.build.revision' 格式<br /><br /> Al.exe 偵測到與指定的格式不正確的版本資訊<xref:System.Resources.SatelliteContractVersionAttribute>。|  
|al1055|參考的組件 'filename' 沒有強式名稱<br /><br /> 當您建置包含強式名稱的組件，但是卻參考不含強式名稱的組件時，便會發生這個錯誤。 若要修正此問題，您必須重新產生組件具有強式名稱，或附加至組件的強式名稱使用 sn.exe (請參閱文件[sn.exe](../../../docs/framework/tools/sn-exe-strong-name-tool.md))。<br /><br /> 透過包裝函式組件使用 COM 物件時，通常會發生這個錯誤，例如透過 Visual Studio IDE 在 C# 專案的 COM 模組中加入參考時。 若要避免發生這個錯誤，您可以在 [包裝函式組件金鑰檔/名稱] 專案屬性中指定 COM 包裝函式組件的強式名稱金鑰檔。<br /><br /> 如果您要建立透過 tlbimp 的包裝函式組件，請參閱[tlbimp](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)文件，如需有關如何將強式名稱指派給包裝函式組件資訊。<br /><br /> 如果組件有強式名稱，便可將它安裝在全域組件快取中。 因此，參考的組件也需要進入全域組件快取中。 只有包含強式名稱的組件才能進入全域組件快取中。|  
|al1056|參考的組件 'filename' 是當地語系化的附屬組件<br /><br /> 使用建立的組件<xref:System.Reflection.AssemblyCultureAttribute>屬性中建立新的組件參考。 <xref:System.Reflection.AssemblyCultureAttribute>屬性表示檔案是當地語系化的附屬組件，不適合參考附屬組件。 您可能應該改為參考主要父組件。|  
|al1057|可執行檔無法被當地語系化，文化特性需保持空白<br /><br /> 正在建立組件使用**/target: exe**但**/文化特性**所指定。 .exe 中的組件在 [文化特性] 欄位中不能包含資訊。|  
|al1058|'file' 是組件，而且無法加入為模組<br /><br /> 在 c + + 編譯， **/assemblymodule** （連結器選項） 傳遞包含組件的檔案。|  
|al1059|未知的錯誤 (code)<br /><br /> Al.exe 收到未知的錯誤碼 (`code`)。<br /><br /> 可能的解決方法包括：<br /><br /> 請重新安裝 Visual Studio。<br /><br /> 重新安裝 [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]。<br /><br /> 檢查是否有遺漏的檔案。<br /><br /> 檢查是否有足夠的磁碟空間。<br /><br /> 檢查是否有足夠的記憶體。<br /><br /> 停止其他可能會存取檔案的處理序。<br /><br /> 重新啟動電腦。|  
|al1060|建立雜湊時密碼編譯失敗 — 原因<br /><br /> 為多檔案組件建立檔案雜湊時發生錯誤。|  
|al1061|無法設定選項 'option'，因為 'reason'<br /><br /> 為這個選項指定的值因指定原因無效。|  
|al1062|模組 'module' 已經被指定多次; 它只能被包括一次<br /><br /> 這個警告會在相同的來源、輸入或模組檔案於命令列上多次指定時產生。 請確定您只指定一次檔案名稱。|  
|al1063|在這個組件中公用類型 'type' 已於多個位置定義: 'file1' 和 'file2'<br /><br /> 在組件的多個模組中找到同一個類型。 組件中每個類型只能有一個版本。|  
|al1064|無法指定多個 /bugreport 選項。<br /><br /> 只有一個**/bugreport**允許選項。|  
|al1065|檔名 'File Name' 太長或無效<br /><br /> 指定的檔名超過允許的上限。|  
|al1066|不能在命令列或回應檔中使用字元 'character'<br /><br /> 在命令列或檔案中找到無效的字元。|  
|al1067|'filename' 是二進位檔，不是文字檔<br /><br /> 這個檔案是二進位格式，不是文字格式。|  
|al1068|在這個組件中已經定義模組 'ModuleName'。 每個連結資源和模組必須具有唯一的檔名。<br /><br /> 該模組在這個組件中出現一次以上。|  
|al1069|無法建立短檔名 'filename'，因為已經有個長檔名具有相同的短檔名<br /><br /> 目前檔案的名稱是另一個已存在檔名的簡短版本。 例如，編譯 LongFileName.cs 後再以 LongFi~1.cs 名稱重新編譯，便會造成類似的編譯器錯誤。 如果已刪除具有長名稱的編譯器輸出檔，但類比連結器檔案還存在，便會發生這個錯誤。|  
|al1070|無從驗證的組件不能有處理器特定模組 'Module Name'<br /><br /> 如果您要建置使用**/platform:agnostic** (或您沒有指定**/platform**)，將會產生錯誤，如果您嘗試新增的模組 (使用**/addmodule**) 不是無從驗證。 這類似嘗試將 i386 obj 檔連結至 ia64 obj。<br /><br /> 非無從驗證模組的主要來源為 C++。 如果您使用**/addmodule**與 c + + 模組，您可能必須修改建置指令碼，以指定適當**/platform**設定。|  
|al1072|組件和模組 'Module Name' 的目標處理器不能不同<br /><br /> 您無法將目標為不同處理器的組件和模組連結在一起，因為結果必須在單一處理器上執行。|  
|al1073|參考的組件 'assembly' 以不同的處理器為目標<br /><br /> 您無法將目標為不同處理器的組件連結在一起，因為結果必須在單一處理器上執行。|  
|al1074|儲存於 'File Name' 的模組名稱 'Module Name' 必須符合其檔名<br /><br /> 這是連結器的必要條件。 若要解決這個問題，請讓這兩個名稱相符。|  
|al1075|要求延遲簽署，但未提供金鑰<br /><br /> 當延遲簽署組件時，編譯器不會去計算和儲存簽章，但會保留檔案中的空間，以便稍後再加入簽章。<br /><br /> 例如，使用**/delaysign+**可讓測試人員將組件置於全域快取中。 測試之後，您可以使用 Assembly Linker 公用程式將私密金鑰加入組件，以完整簽署組件。|  
|al1076|類型 'type' 會轉送至多個組件: 'assembly' 和 'assembly'。<br /><br /> 類型只能轉送至一個組件。|  
|al1077|公用類型 'type' 定義於 'assembly' 中並轉送至 'assembly'。<br /><br /> 所產生的組件中有重複的公用類型。 其中一個是有效的類型定義，另一個是類型轉送子。|  
  
## <a name="example"></a>範例  
 下列命令會使用 `t2a.exe` 模組中的組件建立可執行檔 `t2.netmodule`。 進入點是 `Main` 中的 `MyClass` 方法。  
  
```  
al t2.netmodule /target:exe /out:t2a.exe /main:MyClass.Main  
```  
  
## <a name="see-also"></a>另請參閱  
 [工具](../../../docs/framework/tools/index.md)   
 [Sn.exe （強式名稱工具）](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [Gacutil.exe （全域組件快取工具）](../../../docs/framework/tools/gacutil-exe-gac-tool.md)   
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)