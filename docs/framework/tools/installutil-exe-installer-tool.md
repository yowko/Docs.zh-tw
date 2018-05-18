---
title: Installutil.exe (安裝程式工具)
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec7e498e0f0634d4f0e104247b430fb591f702ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (安裝程式工具)
安裝程式工具是一種命令列公用程式，可讓您透過執行指定之組件中的安裝程式元件，來安裝和解除安裝伺服器資源。 這個工具可以與 <xref:System.Configuration.Install> 命名空間中的類別一起使用。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] \(或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a>參數  
  
|引數|描述|  
|--------------|-----------------|  
|`assembly`|要執行安裝程式元件之組件的檔案名稱。 如果您要使用 `/AssemblyName` 選項指定組件的強式名稱，請略過此參數。|  
  
<a name="options"></a>   
## <a name="options"></a>選項  
  
|選項|描述|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> -或-<br /><br /> `/?`|顯示工具的命令語法和選項。|  
|`/help` *assembly*<br /><br /> -或-<br /><br /> `/?` *assembly*|顯示指定之組件中的個別安裝程式所辨識的其他選項，以及 InstallUtil.exe 的指令語法和選項。 這個選項會將每個安裝程式元件之 <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> 屬性所傳回的文字加入至 InstallUtil.exe 的説明文字。|  
|`/AssemblyName` "*assemblyName*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> ,Culture=*locale*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|指定組件的強式名稱，必須在全域組件快取中登錄此名稱。 您必須利用組件的版本、文化特性 (Culture) 和公開金鑰語彙基元 (Token) 以完整限定組件名稱。 必須以引號括住完整名稱。<br /><br /> 例如，"myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" 就是完整的組件名稱。|  
|`/InstallStateDir=[` *directoryName* `]`|指定 .InstallState 檔案的目錄，其中包含用於解除安裝組件的資料。 預設是包含組件的目錄。|  
|`/LogFile=`[*filename*]|指定記錄安裝進度的記錄檔名稱。 預設情況下，如果省略 `/LogFile` 選項，則會建立名為 *assemblyname*.InstallLog 的記錄檔。 如果省略 *filename*，則不會產生任何記錄檔。|  
|`/LogToConsole`={`true`&#124;`false`}|如果為 `true`，則會在主控台顯示輸出。 如果為 `false` (預設值)，則隱藏對主控台的輸出。|  
|`/ShowCallStack`|如果在安裝期間的任何時間點上發生例外狀況，則將呼叫堆疊輸出到記錄檔。|  
|`/u`[`ninstall`]|解除安裝指定的組件。 不同於其他選項，`/u` 會套用至所有組件 (與選項出現在命令列上的位置無關)。|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a>其他安裝程式選項  
 組件中使用的個別安裝程式可能會辨識列在[選項](#options)區段以外的選項。 若要了解這些選項，請在命令列上使用組件路徑搭配 `/?` 或 `/help` 選項以執行 InstallUtil.exe。 若要指定這些選項，請在命令列上將這些選項與 InstallUtil.exe 辨識的選項包含在一起。  
  
> [!NOTE]
>  個別安裝程式元件所支援之選項上的說明文字由 <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> 屬性傳回。 已經在命令列上輸入的個別選項可透過程式設計方式從 <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> 屬性中存取。  
  
 所有選項和命令列參數皆會寫入安裝記錄檔。 但是，如果您使用某些安裝程式元件可識別的 `/Password` 參數，則會以八個星號 (*) 取代密碼資訊，因此密碼不會出現在記錄檔中。  
  
> [!IMPORTANT]
>  在某些情況下，傳遞給安裝程式的參數可能包含機密或可識別個人身分的資訊，這些資訊預設是寫入到純文字的記錄檔。 若要防止這個行為，您可以在命令列上的 Installutil.exe 後面指定 `/LogFile=` (不含 *filename* 引數) 以隱藏記錄檔。  
  
## <a name="remarks"></a>備註  
 .NET Framework 應用程式由傳統的程式檔和關聯的資源組成，例如訊息佇列、事件記錄檔，以及部署應用程式時所必須建立的效能計數器。 安裝應用程式時，您可以使用組件的安裝元件來建立這些資源，並在解除安裝應用程式時移除它們。 Installutil.exe 會偵測並執行這些安裝程式元件。  
  
 您可以在相同命令列上指定多個組件。 任何出現在組件名稱之前的選項都會套用到該組件的安裝。 除了 `/u` 和 `/AssemblyName` 之外，選項可以累積但不可覆寫。 也就是說，除非以新的值指定選項，否則為一個組件指定的選項會套用到所有後續的組件。  
  
 如果對組件執行 Installutil.exe 而沒有指定任何選項的話，它會將下列三個檔案放置到組件的目錄中：  
  
-   InstallUtil.InstallLog：包含安裝進度的一般說明。  
  
-   *assemblyname*.InstallLog - 包含安裝程序認可階段的特定資訊。 如需關於認可階段的詳細資訊，請參閱 <xref:System.Configuration.Install.Installer.Commit%2A> 方法。  
  
-   *assemblyname*.InstallState - 包含用來解除安裝組件的資料。  
  
 Installutil.exe 使用反射來檢查指定的組件並找到所有 <xref:System.Configuration.Install.Installer> 類型，這些類型的 <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> 屬性設定為 `true`。 然後工具會在 <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> 類型的每個執行個體上執行 <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> 或 <xref:System.Configuration.Install.Installer> 方法。 Installutil.exe 會以交易方式執行安裝；也就是說，如果其中一個組件安裝失敗，便會復原所有其他組件的安裝。 解除安裝不是可異動的。  
  
 Installutil.exe 無法安裝或解除安裝延遲簽署的組件，但是可以安裝或解除安裝強式命名的組件。  
  
 從 .NET Framework 2.0 版開始，32 位元版本的通用語言執行平台 (CLR) 僅會隨附於 32 位元版本的安裝程式工具，但是 64 位元版本的 CLR 則會隨附於 32 位元和 64 位元版本的安裝程式工具。 當您使用 64 位元的 CLR 時，請使用 32 位元的安裝程式工具來安裝 32 位元的組件，並使用 64 位元的安裝程式工具來安裝 64 位元和 Microsoft Intermediate Language (MSIL) 的組件。 這兩種版本的安裝程式工具會有相同的行為方式。  
  
 您不能使用 Installutil.exe 部署使用 C++ 建立的 Windows 服務，因為 Installutil.exe 無法辨識由 C++ 編譯器產生的內嵌機器碼。 如果您嘗試使用 Installutil.exe 部署 C++ Windows 服務，就會擲回類似 <xref:System.BadImageFormatException> 的例外狀況。 若要處理這種案例，請將服務程式碼移至 C++ 模組，然後以 C# 或 Visual Basic 撰寫安裝程式物件。  
  
## <a name="examples"></a>範例  
 下列命令會顯示 InstallUtil.exe 命令語法及選項的描述。  
  
```  
installutil /?  
```  
  
 下列命令會顯示 InstallUtil.exe 命令語法及選項的描述。 如果已將說明文字指派給安裝程式的 <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> 屬性，還會顯示 `myAssembly.exe` 中的安裝程式元件所支援的選項描述和清單。  
  
```  
installutil /? myAssembly.exe  
```  
  
 下列命令會執行 `myAssembly.exe` 組件中的安裝程式元件。  
  
```  
installutil myAssembly.exe  
```  
  
 下列命令會使用 `/AssemblyName` 參數和完整名稱，執行組件中的安裝程式元件。  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 下列命令會執行檔案名稱及強式名稱所指定之組件中的安裝程式元件。 請注意，所有依檔案名稱指定的組件必須在命令列中以強式名稱指定的組件之前，因為不可覆寫 `/AssemblyName` 選項。  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 下列命令會執行 `myAssembly.exe` 組件中的解除安裝程式元件。  
  
```  
installutil /u myAssembly.exe   
```  
  
 下列命令會執行組件 `myAssembly1.exe` 和 `myAssembly2.exe` 中的解除安裝程式元件。  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 因為 `/u` 選項在命令列中的位置並不重要，因此這會等於下列指令。  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 下列命令會執行 `myAssembly.exe` 組件中的安裝程式，並指定將進度資訊寫入 `myLog.InstallLog`。  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 下列命令會執行組件 `myAssembly.exe` 中的安裝程式、指定要將進度資訊寫入 `myLog.InstallLog`，然後使用安裝程式的自訂 `/reg` 選項指定要對系統登錄進行更新。  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 下列命令會執行組件 `myAssembly.exe` 中的安裝程式、使用安裝程式的自訂 `/email` 選項指定使用者的電子郵件地址，並隱藏對記錄檔的輸出。  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 下列命令會將 `myAssembly.exe` 的安裝進度寫入到 `myLog.InstallLog`，並且將 `myTestAssembly.exe` 的進度寫入到 `myTestLog.InstallLog`。  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Configuration.Install>  
 [工具](../../../docs/framework/tools/index.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
