---
title: "Mage.exe (資訊清單產生和編輯工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
caps.latest.revision: "68"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 405503ac824ccf443d8ada7387d65e55876cb3e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (資訊清單產生和編輯工具)
「資訊清單產生和編輯工具」(Mage.exe) 是命令列工具，可支援建立和編輯應用程式與部署資訊清單。 由於 Mage.exe 是命令列工具，因此可以從批次指令碼及其他 Windows 架構應用程式 (包括 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式) 中執行。  
  
 您也可以使用 MageUI.exe 這個圖形應用程式來取代 Mage.exe。 如需詳細資訊，請參閱 [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 安裝程式有兩個版本的 Mage.exe 和 MageUI.exe 做為隨附元件。 若要查看版本資訊，請執行 MageUI.exe，並依序選取 [ **說明**] 和 [ **關於**]。 本文件說明 4.0.x.x 版本的 Mage.exe 和 MageUI.exe。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
Mage [commands] [commandOptions]  
```  
  
#### <a name="parameters"></a>參數  
 下表顯示 Mage.exe 所支援的命令。 如需這些命令所支援選項的詳細資訊，請參閱 [新的和更新的命令選項](#NewUpdate) 和 [Sign 命令選項](#Sign)。  
  
|命令|描述|  
|-------------|-----------------|  
|**-cc, ClearApplicationCache**|清除所有僅供線上使用之應用程式的已下載應用程式快取。|  
|**-n, -New** *fileType [newOptions]*|建立指定類型的新檔案。 有效的類型如下：<br /><br /> -   `Deployment`：建立新的部署資訊清單。<br />-   `Application`：建立新的應用程式資訊清單。<br /><br /> 如果這個命令沒有指定額外的參數，就會以適當的預設標記和屬性值，建立適當類型的檔案。<br /><br /> 使用 **-ToFile** 選項 (見下表) 可以指定新檔案的檔案名稱和路徑。<br /><br /> 使用 **-FromDirectory** 選項 (見下表) 可以建立應用程式資訊清單，並在此資訊清單的 \<相依性> 區段中新增應用程式的所有組件。|  
|**-u, -Update** *[filePath] [updateOptions]*|對資訊清單檔案進行一項或多項變更。 您不必指定要編輯的檔案類型。 Mage.exe 會使用一組啟發學習法來檢查檔案並判斷它是部署資訊清單或應用程式資訊清單。<br /><br /> 如果您已經使用憑證簽署檔案， **-Update** 會移除金鑰簽章區塊。 這是因為金鑰簽章含有檔案的雜湊，修改檔案會使得雜湊變成無效。<br /><br /> 使用 **-ToFile** 選項 (見下表) 可以指定新檔案名稱和路徑，而不會覆寫現有檔案。|  
|**-s, -Sign** `[signOptions]`|使用金鑰組或 X509 憑證簽署檔案。 簽章會以 XML 項目的形式插入檔案內。<br /><br /> 簽署指定 **-TimestampUri** 值的資訊清單時，您必須連線到網際網路。|  
|**-h, -?, -Help** *[verbose]*|描述所有可用命令及其選項。 指定 `verbose` 可取得詳細的說明。|  
  
<a name="NewUpdate"></a>   
## <a name="new-and-update-command-options"></a>新的和更新的命令選項  
 下表顯示 `-New` 和 `-Update` 命令支援的選項。  
  
|選項|預設值|適用於|描述|  
|-------------|-------------------|----------------|-----------------|  
|**-a, -Algorithm**|sha1RSA|應用程式資訊清單。<br /><br /> 部署資訊清單。|指定產生相依性摘要的演算法。 值必須是 "sha256RSA" 或 "sha1RSA"。<br /><br /> 搭配 "-Update" 選項一起使用。 這個選項在使用 "-Sign" 選項時會被忽略。|  
|**-appc, -AppCodeBase** `manifestReference`||部署資訊清單。|插入應用程式資訊清單檔案的 URL 或檔案路徑參考。 這個值必須是應用程式資訊清單的完整路徑。|  
|**-appm, -AppManifest** `manifestPath`||部署資訊清單。|將部署的應用程式資訊清單參考插入其部署資訊清單中。<br /><br /> `manifestPath` 所表示的檔案必須存在，否則 Mage.exe 會發出錯誤訊息。 如果 `manifestPath` 所參考的檔案不是應用程式資訊清單，Mage.exe 會發出錯誤訊息。|  
|**-cf, -CertFile** `filePath`||所有檔案類型。|指定為資訊清單簽署之 X509 數位憑證的位置。 如果憑證需要密碼，這個選項就可以與 **-Password** 選項搭配使用。|  
|**-ch, -CertHash** `hashSignature`||所有檔案類型。|數位憑證的雜湊儲存在用戶端電腦的個人憑證存放區內。 它對應到數位憑證的指模字串，此字串可以從 Windows 憑證主控台檢視。<br /><br /> `hashSignature` 大小寫都可，提供的格式可以是單一字串，或是將整個指模以引號括起來 (指模中每八個位元組以空格隔開)。|  
|**-fd, -FromDirectory** `directoryPath`||應用程式資訊清單。|將 `directoryPath`中找到的所有組件和檔案的描述，填入應用程式資訊清單中，包括所有的子目錄，其中 `directoryPath` 是您想部署應用程式所在的目錄。 Mage.exe 會判斷目錄中的每個檔案是組件或靜態檔。 如果是組件，它會在應用程式中加入 `<dependency>` 標記和 `installFrom` 屬性，以及這個組件的名稱、程式碼基底和版本。 如果是靜態檔案，它會加入 `<file>` 標記。 Mage.exe 也會使用一組簡單的啟發學習法來偵測應用程式的主要可執行檔，並在資訊清單中將它標示為 ClickOnce 應用程式的進入點。<br /><br /> Mage.exe 不會自動將檔案標示為「資料」檔。 您必須手動標示。 如需詳細資訊，請參閱 [How to: Include a Data File in a ClickOnce Application](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application)。<br /><br /> Mage.exe 也會依據每個檔案的大小來產生雜湊。 ClickOnce 使用這些雜湊來確保自從建立資訊清單後，沒有遭他人修改過這個部署的檔案。 如果部署中的任何檔案有所變更，您可以搭配使用 **-Update** 命令和 **-FromDirectory** 選項來執行 Mage.exe，以更新所有參考檔案的雜湊和組件版本。<br /><br /> **-FromDirectory** 會包含 `directoryPath`內所有子目錄的全部檔案。<br /><br /> 如果您搭配 **-FromDirectory** 使用 **-Update** 命令，Mage.exe 會從應用程式資訊清單中移除已不在目錄中的檔案。|  
|**-if, -IconFile**  `filePath`||應用程式資訊清單。|指定 .ICO 圖示檔的完整路徑。 這個圖示會出現在 [開始] 功能表中您的應用程式名稱旁，以及 [新增或移除程式] 項目中。 如果沒有提供圖示，就會使用預設圖示。|  
|**-ip, -IncludeProviderURL**  `url`|true|部署資訊清單。|指出部署資訊清單是否包括由 **-ProviderURL**設定的更新位置值。|  
|**-i, -Install** `willInstall`|true|部署資訊清單。|指出 ClickOnce 應用程式是否要安裝到本機電腦上，或者它是否要從 Web 執行安裝。 應用程式在安裝後會出現在 Windows [ **開始** ] 功能表中。 有效值為 "true" (或 "t") 和 "false" (或 "f")。<br /><br /> 如果您指定 **-MinVersion** 選項，但使用者擁有的版本低於所安裝的 **-MinVersion** ，這時會強制應用程式進行安裝，不管您傳遞至 **-Install**的值為何。<br /><br /> 這個選項無法與 **-BrowserHosted** 選項搭配使用。 嘗試在相同的資訊清單同時指定這兩個選項會導致錯誤。|  
|**-mv, -MinVersion**  `[version]`|列於 ClickOnce 部署資訊清單中，由 **-Version** 旗標指定的版本。|部署資訊清單。|使用者可以執行的應用程式最小版本。 這個旗標可讓應用程式的具名版本成為必要的更新項目。 如果您發行的產品版本具有重大變更的更新或嚴重的安全性問題，即可使用這個旗標，指定必須安裝這個更新項目，且使用者不可再繼續執行舊版。<br /><br /> `version` 的語意與 **-Version** 旗標的引數相同。|  
|**-n, -Name** `nameString`|部署|所有檔案類型。|用來識別應用程式的名稱。 ClickOnce 會使用這個名稱來識別 [開始] 功能表 (如果應用程式是設定為自行安裝) 和 [使用權限提高] 對話方塊中的應用程式。 **注意：**如果您要更新現有的資訊清單，但未使用此選項來指定發行者名稱，Mage.exe 會更新含電腦上定義之組織名稱的資訊清單。 若要使用不同的名稱，請務必使用這個選項，並指定所需的發行者名稱。|  
|**-pwd, -Password** `passwd`||所有檔案類型。|以數位憑證替資訊清單簽章時所使用的密碼。 必須與 **-CertFile** 選項搭配使用。|  
|**-p, Processor** `processorValue`|Msil|應用程式資訊清單。<br /><br /> 部署資訊清單。|這項散發所要執行的微處理器架構。 如果您正準備進行一或數個安裝，且其組件已針對特定微處理器先行編譯過，則需要這個值。 有效值包括 `msil`、 `x86`、 `ia64`和 `amd64`。 `msil` 為 Microsoft 中繼語言，這表示您的所有組件都與平台無關，而且當您的應用程式首次執行時，通用語言執行平台 (CLR) 會對它們進行 Just-In-Time 編譯。|  
|**-pu,** **-ProviderURL** `url`||部署資訊清單。|指定 URL，讓 ClickOnce 從該處檢查是否有應用程式更新。|  
|**-pub, -Publisher** `publisherName`||應用程式資訊清單。<br /><br /> 部署資訊清單。|將發行者名稱加入到部署或應用程式資訊清單的描述項目。 使用在應用程式資訊清單上時，也必須使用值 "true" 或 "t" 指定 **-UseManifestForTrust** ，否則此參數會引發錯誤。|  
|**-s, -SupportURL**  `url`||應用程式資訊清單。<br /><br /> 部署資訊清單。|指定出現在 [新增或移除程式] 中的 ClickOnce 應用程式連結。|  
|**-ti, -TimestampUri** `uri`||應用程式資訊清單。<br /><br /> 部署資訊清單。|數位時間戳記服務的 URL。 在資訊清單加上時間戳記之後，若數位憑證在您部署應用程式的下一個版本之前到期，就無須重新簽署資訊清單。 如需詳細資訊，請參閱 [Windows 根憑證程式成員](http://go.microsoft.com/fwlink/?LinkId=159000)。|  
|**-t, -ToFile** `filePath`|-   新增：<br />-   部署：deploy.application<br />-   應用程式：application.exe.manifest<br />-   更新：<br />-   輸入檔。|所有檔案類型。|指定已建立或已修改之檔案的輸出路徑。<br /><br /> 如果使用 **-New** 時未提供 **-ToFile**，就會將輸出寫入目前的工作目錄。 如果使用 **-Update** 時未提供 **-ToFile**，Mage.exe 就會將檔案寫回輸入檔。|  
|**-tr, -TrustLevel** `level`|以應用程式 URL 所在區域為基礎。|應用程式資訊清單。|要授與用戶端電腦上應用程式的信任層級。 可用的值包括 "Internet"、"Intranet" 和 "FullTrust"。|  
|**-um, -UseManifestForTrust** `willUseForTrust`|False|應用程式資訊清單。|指定當應用程式在用戶端上執行時，是否會使用應用程式資訊清單的數位簽章進行信任決策。 指定 "true" 或 "t" 表示信任決策會使用應用程式資訊清單。 指定 "false" 或 "f" 則表示會使用部署資訊清單的簽章。|  
|**-v, -Version** `versionNumber`|1.0.0.0|應用程式資訊清單。<br /><br /> 部署資訊清單。|部署的版本。 引數必須是格式為 "*N.N.N.N*" 的有效版本字串，其中 "*N*" 是不帶正負號的 32 位元整數。|  
|**-wpf, -WPFBrowserApp**  `isWPFApp`|False|應用程式資訊清單。<br /><br /> 部署資訊清單。|只有在應用程式是裝載在 Internet Explorer 內的 Windows Presentation Foundation (WPF) 應用程式，且不是獨立的可執行檔時，才使用這個旗標。 有效值為 "true" (或 "t") 和 "false" (或 "f")。<br /><br /> 若為應用程式資訊清單，會在應用程式資訊清單的 `hostInBrowser` 項目底下插入 `entryPoint` 屬性。<br /><br /> 若為部署資訊清單，會將 `install` 項目上的 `deployment` 屬性設為 false，並將部署資訊清單儲存成副檔名為 .xbap 的檔案。 這個引數與 **-Install** 引數一起指定時會產生錯誤，因為瀏覽器裝載的應用程式不能是已安裝的離線應用程式。|  
  
<a name="Sign"></a>   
## <a name="sign-command-options"></a>Sign 命令選項  
 下表顯示 `-Sign` 命令支援的選項，這些選項可以套用至所有類型的檔案。  
  
|選項|描述|  
|-------------|-----------------|  
|**-cf, -CertFile** `filePath`|指定為資訊清單簽署之數位憑證的位置。 這個選項可以與 **-Password** 選項搭配使用。|  
|**-ch, -CertHash** `hashSignature`|數位憑證的雜湊儲存在用戶端電腦的個人憑證存放區內。 它對應到數位憑證的 Thumbprint 屬性，此屬性可以從 Windows 憑證主控台檢視。<br /><br /> `hashSignature` 大小寫都可，提供的格式可以是單一字串，或是將整個指模以引號括起來 (指模中每八個位元組以空格隔開)。|  
|**-pwd, -Password** `passwd`|以數位憑證替資訊清單簽章時所使用的密碼。 必須與 **-CertFile** 選項搭配使用。|  
|**-t, -ToFile** `filePath`|指定已建立或已修改之檔案的輸出路徑。|  
  
## <a name="remarks"></a>備註  
 Mage.exe 的所有引數都不區分大小寫。 命令和選項可以使用破折號 (-) 或正斜線 (/) 當做前置字元。  
  
 搭配 **-Sign** 命令使用的所有引數，也隨時都能搭配 **-New** 或 **-Update** 命令使用。 下列命令是相同的。  
  
```  
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx  
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx  
```  
  
> [!NOTE]
>  從 .NET Framework 4.6.2 版開始，也支援 CNG 憑證。  
  
 最後要執行的工作是簽署，因為簽署後的文件會使用檔案雜湊來驗證此簽章對文件是否有效。 如果您已對簽署後的檔案進行任何變更，就必須重新簽署一次。 如果您對先前簽署過的文件再次簽章，Mage.exe 會以新簽章取代舊簽章。  
  
 當您使用 **-AppManifest** 選項填入部署資訊清單時，Mage.exe 會假設應用程式資訊清單位於以目前的部署版本命名的子目錄下，與部署資訊清單相同的目錄中，並且會適當地設定部署資訊清單。 如果您的應用程式資訊清單要位於其他位置，請使用 **-AppCodeBase** 選項設定替代位置。  
  
 在部署應用程式之前，必須先替部署和應用程式資訊清單簽章。 如需簽署資訊清單的相關指引，請參閱 [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview)。  
  
 應用程式資訊清單的 **-TrustLevel** 選項，描述了要在用戶端電腦上執行應用程式時所需的使用權限集合。 根據預設，應用程式的信任層級是依據其 URL 所在的「 *區域* 」(Zone) 來指派。 透過公司網路所部署的應用程式，通常都位於內部網路區域，而透過網際網路所部署的應用程式，則位於網際網路區域。 這兩個安全性區域對應用程式存取本機資源的能力都有限制，其中內部網路區域的使用權限稍微大於網際網路區域。 FullTrust 區域授與應用程式完整的存取權限，可以存取電腦的本機資源。 如果使用 **-TrustLevel** 選項將應用程式放在這個區域，則 CLR 的「信任管理員」元件將會提示使用者決定是否要授與這個較高層次的信任。 如果您透過公司網路來部署應用程式，即可使用「受信任的應用程式部署」來提高應用程式的信任層次，而不需要提示使用者做決定。  
  
 應用程式資訊清單同時也支援自訂信任的區段。 這可以協助應用程式遵守「要求最少使用權限」的安全性原則，因為您可以將資訊清單設定成只要求執行應用程式所需的特定使用權限。 Mage.exe 不直接支援加入自訂信任區段。 您可以使用文字編輯器、XML 剖析器或圖形工具 MageUI.exe 來加入一個區段。 如需如何使用 MageUI.exe 加入自訂信任區段的詳細資訊，請參閱 [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)。  
  
 以 Mage.exe 第 4 版建立的新資訊清單，該程式隨附在 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)]中，會以 [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]為目標。 若要以舊版的 .NET Framework 為目標，您必須使用舊版的 Mage.exe。 當從現有的資訊清單新增或移除組件或重新簽署現有的資訊清單時，Mage.exe 並不會以 [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]為目標更新資訊清單。 下表顯示這些功能和限制。  
  
|資訊清單版本|運算|Mage v2.0|Mage v4.0|  
|----------------------|---------------|---------------|---------------|  
|以 .NET Framework 2.0 或 3.x 為目標之應用程式的資訊清單|開啟|確定|確定|  
||關閉|確定|確定|  
||儲存|確定|確定|  
||重新簽署|確定|確定|  
||新增|確定|不支援|  
||更新 (請參閱下方)|確定|確定|  
|以 .NET Framework 第 4 版為目標之應用程式的資訊清單|開啟|確定|確定|  
||關閉|確定|確定|  
||儲存|確定|確定|  
||重新簽署|確定|確定|  
||新增|不支援|確定|  
||更新 (請參閱下方)|不支援|確定|  
  
|資訊清單版本|更新作業詳細資料|Mage v2.0|Mage v4.0|  
|----------------------|------------------------------|---------------|---------------|  
|以 .NET Framework 2.0 或 3.x 為目標之應用程式的資訊清單|修改組件|確定|確定|  
||加入組件|確定|確定|  
||移除組件|確定|確定|  
|以 .NET Framework 第 4 版為目標之應用程式的資訊清單|修改組件|不支援|確定|  
||加入組件|不支援|確定|  
||移除組件|不支援|確定|  
  
 Mage.exe 會建立以 [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]為目標的新資訊清單。 以 [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] 為目標的 ClickOnce 應用程式可以在 [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] 及 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]完整版本上執行。 如果您的應用程式以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 的完整版本為目標，而且無法在 [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]上執行，請使用文字編輯器移除用戶端 `<framework>` 項目，並且重新簽署資訊清單。 下列是以 `<framework>` 為目標的 [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]項目範例。  
  
```xml  
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />  
```  
  
## <a name="examples"></a>範例  
 下列範例會開啟 Mage (MageUI.exe) 的使用者介面。  
  
```  
mage  
```  
  
 下列範例會建立預設部署資訊清單和應用程式資訊清單。 這些檔案都在目前工作目錄中建立，名稱分別是 deploy.application 和 application.exe.manifest。  
  
```  
mage -New Deployment  
mage -New Application  
```  
  
 下列範例會建立應用程式資訊清單，其中將填入目前目錄的所有組件和資源檔案。  
  
```  
mage -New Application -FromDirectory . -Version 1.0.0.0  
```  
  
 下列範例延續前一個範例，其中會指定部署名稱和目標微處理器。 此外也會指定 URL，讓 ClickOnce 從該位置檢查是否有更新。  
  
```  
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/  
```  
  
 下列範例示範如何建立一組資訊清單，以部署裝載在 Internet Explorer 中的 WPF 應用程式。  
  
```  
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true  
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true  
```  
  
 下列範例會以應用程式資訊清單的資訊來更新部署資訊清單，並針對應用程式資訊清單的位置設定程式碼基底。  
  
```  
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy  
```  
  
 下列範例會編輯部署資訊清單，以強制更新使用者所安裝的版本。  
  
```  
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0  
```  
  
 下列範例會告知部署資訊清單從另一個目錄擷取應用程式資訊清單。  
  
```  
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/  
```  
  
 下列範例會使用目前工作目錄中的數位憑證，替現有的部署資訊清單簽章。  
  
```  
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>  
```  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)  
 [逐步解說：手動部署 ClickOnce 應用程式](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 [受信任的應用程式部署概觀](/visualstudio/deployment/trusted-application-deployment-overview)  
 [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
