---
title: "Caspol.exe (程式碼存取安全性原則工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permission sets, modifying security policy
- security policy [.NET Framework], Code Access Security Policy tool
- enterprise security policy
- referencing code groups and permission sets
- user security policy
- Caspol.exe
- Code Access Security Policy tool
- code groups, modifying security policy
- application development [.NET Framework], security
- machine security policy
- security policy [.NET Framework], modifying
- manually editing security configuration files
ms.assetid: d2bf6123-7b0c-4e60-87ad-a39a1c3eb2e0
caps.latest.revision: "44"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ab363e833ecde86a17d9adea3fcd26351725868
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (程式碼存取安全性原則工具)
程式碼存取安全性 (CAS) 原則工具 (Caspol.exe) 可以讓使用者和系統管理員修改電腦原則層級、使用者原則層級和企業原則層級的安全性原則。  
  
> [!IMPORTANT]
>  從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，除非將 [\<legacyCasPolicy> 項目](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) 設為 `true`，否則 Caspol.exe 不會影響 CAS 原則。 只有在您選擇使用 CAS 原則後，CasPol.exe 所顯示或修改的任何設定才會影響應用程式。 如需詳細資訊，請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。  
  
> [!NOTE]
>  64 位元電腦包含 64 位元和 32 位元版本的安全性原則。 為了確保您的原則變更同時套用至 32 位元和 64 位元應用程式，請執行 Caspol.exe 的 32 位元和 64 位元這兩種版本。  
  
 程式碼存取安全性原則工具會自動隨 .NET Framework 和 Visual Studio 安裝。 您可以在 32 位元系統上的 %windir%\Microsoft.NET\Framework\\*版本* 或 64 位元系統上的 %windir%\Microsoft.NET\Framework64\\*版本* 找到 Caspol.exe  (例如，64 位元系統上的 .NET Framework 4 位置是 %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe)。如果您的電腦並存執行多個版本的 .NET Framework，則可能會安裝此工具的多個版本。 您可以從安裝目錄執行此工具。 不過，建議您使用[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)，就不需要巡覽至安裝資料夾。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
caspol [options]  
```  
  
#### <a name="parameters"></a>參數  
  
|選項|描述|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> 或<br /><br /> **-af** *assembly_file*|將實作自訂安全物件 (例如，自訂授權或自訂成員資格條件) 的組件加入至特定原則層級的完全信任組件清單。 *assembly_file* 引數會指定要新增的組件。 此檔案必須使用[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)簽署。 您可以使用[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)，以強式名稱來簽署組件。<br /><br /> 只要將包含自訂權限的權限集合加入至原則，就必須將實作自訂權限的組件加入至該原則層級的完全信任清單。 實作安全性原則 (例如，電腦原則) 中所使用之自訂安全性物件 (例如自訂程式碼群組或成員資格條件) 的組件，應一律加入至完全信任組件清單。 **注意：**如果實作自訂安全性物件的組件有參考其他組件，您就必須先將參考的組件新增至完全信任組件清單中。 使用 Visual Basic、C++ 和 JScript 建立的自訂安全性物件會分別參考 Microsoft.VisualBasic.dll、Microsoft.VisualC.dll 或 Microsoft.JScript.dll。 依預設，這些組件不在完全信任組件清單中。 您必須在加入自訂安全性物件之前，先將適當的組件加入至完全信任清單中， 否則將會破壞安全性系統，造成所有的組件都無法載入。 在這種情況下，Caspol.exe **-all -reset** 選項將不會修復安全性。 若要修復安全性，您必須手動編輯安全性檔案，以移除自訂安全性物件。|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*flags*]<br /><br /> 或<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*flags*]|將新的程式碼群組加入至程式碼群組階層架構。 您可以指定 *parent_label* 或 *parent_name*。 *parent_label* 引數會指定所新增程式碼群組之父代的程式碼群組標籤 (例如 1. 或 1.1.)。 *parent_name* 引數會指定要新增之程式碼群組父代的程式碼群組名稱。 由於 *parent_label* 和 *parent_name* 可以交替使用，所以 Caspol.exe 必須能夠區分這兩者。 因此，*parent_name* 不能以數字開頭。 此外，*parent_name* 只能包含 A-Z、0-9 以及底線字元。<br /><br /> *mship* 引數會指定新程式碼群組的成員資格條件。 如需詳細資訊，請參閱本節稍後的 *mship* 引數表。<br /><br /> *pset_name* 引數是權限集合的名稱，其會與新的程式碼群組產生關聯。 您也可以為新群組設定一個或多個 *flags*。 如需詳細資訊，請參閱本節稍後的 *flags* 引數表。|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> 或<br /><br /> **-ap** {*named*_*psfile* &#124; *psfile* *pset_name*}|將新的具名權限集合加入至原則。 權限集合必須以 XML 撰寫並儲存於 .xml 檔案中。 如果 XML 檔案包含權限集合的名稱，則只會指定該檔案 (*psfile*)。 如果 XML 檔案未包含權限集合名稱，則必須同時指定 XML 檔案名稱 (*psfile*) 和權限集合名稱 (*pset_name*)。<br /><br /> 請注意，權限集合中使用的所有權限都必須在全域組件快取內含的組件中定義。|  
|**-a**[**ll**]|指出這個選項之後的所有選項都會套用至電腦、使用者和企業原則。 **-all** 選項一律會參考目前已登入使用者的原則。 若要參考目前使用者以外的使用者原則，請參閱 **-customall** 選項。|  
|**-chggroup** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flags* `}`<br /><br /> 或<br /><br /> **-cg** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flags* `}`|可變更程式碼群組的成員資格條件、權限集合或是 **exclusive**、**levelfinal**、**name** 或 **description** 旗標的設定。 您可以指定 *label* 或是 *name*。 *label* 引數會指定程式碼群組的標籤 (例如 1. 或 1.1.)。 *name* 引數會指定要變更的程式碼群組名稱。 由於 *label* 和 *name* 可以交替使用，所以 Caspol.exe 必須能夠區分這兩者。 因此，*name* 不能以數字開頭。 此外，*name* 只能包含 A-Z、0-9 以及底線字元。<br /><br /> *pset_name* 引數會指定要與程式碼群組產生關聯的權限集合名稱。 如需 *mship* 和 *flags* 引數的詳細資訊，請參閱本節稍後的表格。|  
|**-chgpset**  *psfile pset_name*<br /><br /> 或<br /><br /> **-cp** *psfile pset_name*|變更具名權限集合。 *psfile* 引數為權限集合提供新定義，其為 XML 格式的序列化權限集合檔案。 *pset_name* 引數會指定您想要變更的權限集合名稱。|  
|**-customall**  *path*<br /><br /> 或<br /><br /> **-ca**  *path*|指出這個選項之後的所有選項都會套用至電腦、企業和指定的自訂使用者原則。 您必須使用 *path* 引數來指定自訂使用者的安全性組態檔位置。|  
|**-cu**[**stomuser**] *path*|允許管理不屬於目前執行 Caspol.exe 之使用者的自訂使用者原則。 您必須使用 *path* 引數來指定自訂使用者的安全性組態檔位置。|  
|**-enterprise**<br /><br /> 或<br /><br /> **-en**|指出這個選項之後的所有選項都會套用至企業層級原則。 不是企業系統管理員的使用者沒有足夠的權限可修改企業原則，但是可以檢視原則。 在非企業情節中，這個原則預設不會與電腦和使用者原則牴觸。|  
|**-e**[**xecution**] {**on** &#124; **off**}|開啟或關閉在程式碼開始執行前檢查要執行之權限的機制。 **注意：**這個參數已在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 和更新版本中移除。 如需詳細資訊，請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。|  
|**-f**[**orce**]|抑制工具的自行解構測試，並依照使用者指定的方式變更原則。 一般來說，Caspol.exe 會檢查是否有造成 Caspol.exe 本身無法正常執行的任何原則變更，如果有的話，Caspol.exe 不會儲存該原則變更，而且會印出錯誤訊息。 若要強制 Caspol.exe 變更原則 (即使這個原則會造成 Caspol.exe 本身無法執行)，請使用 **–force** 選項。|  
|**-h**[**elp**]|顯示 Caspol.exe 的命令語法和選項。|  
|**-l**[**ist**]|列出程式碼群組階層架構以及所指定電腦、使用者、企業或所有原則層級的權限集合。 Caspol.exe 會先顯示程式碼群組的標籤，後面接著名稱 (如果不是 null 的話)。|  
|**-listdescription**<br /><br /> 或<br /><br /> **-ld**|列出所指定原則層級的所有程式碼群組描述。|  
|**-listfulltrust**<br /><br /> 或<br /><br /> **-lf**|列出所指定原則層級的完全信任組件清單內容。|  
|**-listgroups**<br /><br /> 或<br /><br /> **-lg**|顯示所指定原則層級或所有原則層級的程式碼群組。 Caspol.exe 會先顯示程式碼群組的標籤，後面接著名稱 (如果不是 null 的話)。|  
|**-listpset** 或 **-lp**|顯示所指定原則層級或所有原則層級的權限集合。|  
|**-m**[**achine**]|指出這個選項之後的所有選項都會套用至電腦層級原則。 不是系統管理員的使用者沒有足夠的權限可修改電腦原則，但是可以檢視原則。 對於系統管理員，**-machine** 是預設值。|  
|**-polchgprompt** {**on** &#124; **off**}<br /><br /> 或<br /><br /> **-pp** {**on** &#124; **off**}|啟用或停用每當使用會造成原則變更的選項來執行 Caspol.exe 時所顯示的提示。|  
|**-quiet**<br /><br /> 或<br /><br /> **-q**|暫時停用通常會對造成原則變更的選項顯示的提示。 不過，全域變更提示設定不會變更。 僅針對單一命令使用這個選項，如此才不會停用所有 Caspol.exe 命令的提示。|  
|**-r**[**ecover**]|從備份檔復原原則。 每當原則變更時，Caspol.exe 都會將舊原則儲存到備份檔中。|  
|**-remfulltrust** *assembly_file*<br /><br /> 或<br /><br /> **-rf**  *assembly_file*|從原則層級的完全信任清單中移除組件。 如果原則不再使用包含自訂權限的權限集合，則應該執行這項作業。 不過，只有在組件未實作任何其他仍在使用的自訂權限時，才可以從完全信任清單中移除實作自訂權限的組件。 當您從清單中移除組件時，也應該移除該組件所依存的任何其他組件。|  
|**-remgroup** {*label &#124;name*}<br /><br /> 或<br /><br /> **-rg** {l*abel &#124; name*}|移除以標籤或名稱指定的程式碼群組。 如果指定的程式碼群組包含子程式碼群組，Caspol.exe 也會移除所有子程式碼群組。|  
|**-rempset** *pset_name*<br /><br /> 或<br /><br /> **-rp** *pset_name*|從原則中移除指定的權限集合。 *pset_name* 引數會指出要移除的權限集合。 只有在權限集合未與任何程式碼群組相關聯時，Caspol.exe 才會將該權限集合移除。 無法移除預設 (內建) 權限集合。|  
|**-reset**<br /><br /> 或<br /><br /> **-rs**|將原則回復到其預設狀態並保存 (Persist) 到磁碟中。 每當變更的原則似乎無法修復，而您想要以安裝預設值重新開始時，這樣做會非常有用。 當您想要使用預設原則做為修改特定安全性設定檔的起點時，重設也會很方便。 如需詳細資訊，請參閱[手動編輯安全性組態檔](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1)。|  
|**-resetlockdown**<br /><br /> 或<br /><br /> **-rsld**|將原則回復為預設狀態的更嚴格版本並將它保存至磁碟，建立先前電腦原則的備份並將它保存至稱為 `security.config.bac` 的檔案。  鎖定原則類似於預設原則，差別在於鎖定原則不會授與可從 `Local Intranet`、`Trusted Sites` 和 `Internet` 區域撰寫程式碼的權限，而且對應的程式碼群組沒有子程式碼群組。|  
|**-resolvegroup** *assembly_file*<br /><br /> 或<br /><br /> **-rsg**  *assembly_file*|顯示特定組件 (*assembly_file*) 所屬的程式碼群組。 根據預設，這個選項會顯示組件所屬的電腦、使用者和企業原則層級。 若只要檢視一個原則層級，請搭配使用這個選項與 **-machine**、**-user** 或 **-enterprise** 選項。|  
|**-resolveperm** *assembly_file*<br /><br /> 或<br /><br /> **-rsp** *assembly_file*|在允許組件執行的情況下，顯示指定 (或預設) 的安全性原則層級會授與該組件的所有權限。 *assembly_file* 引數會指定組件。 如果指定 **-all** 選項，Caspol.exe 會根據使用者、電腦和企業原則計算組件的權限；若未指定，則會套用預設行為規則。|  
|**-s**[**ecurity**] {**on** &#124; **off**}|開啟或關閉程式碼存取安全性。 指定 **-s off** 選項時，並不會停用以角色為基礎的安全性。 **注意：**這個參數已在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 和更新版本中移除。 如需詳細資訊，請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。 **注意：**停用程式碼存取安全性時，所有的程式碼存取要求都會成功。 停用程式碼存取安全性會讓系統容易受惡意程式碼的攻擊，如病毒和破壞程式。 關閉安全性可獲得額外的效能，但是只有在已採取其他安全措施來協助確保整體系統安全性沒有漏洞的情況下，才可以這樣做。 其他安全性措施的範例，包括從公用網路中斷連結、用實際方法保全電腦等等。|  
|**-u**[**ser**]|指出這個選項之後的所有選項都會套用至執行 Caspol.exe 之使用者的使用者層級原則。 對於非系統管理使用者，**-user** 是預設值。|  
|**-?**|顯示 Caspol.exe 的命令語法和選項。|  
  
 *mship* 引數可以搭配 **-addgroup** 和 **-chggroup** 選項使用，以指定程式碼群組的成員資格條件 。 系統會以 .NET Framework 類別的形式來實作每個 *mship* 引數。 若要指定 *mship,*，請使用下列其中一種方式。  
  
|引數|描述|  
|--------------|-----------------|  
|**-allcode**|指定所有程式碼。 如需這個成員資格條件的詳細資訊，請參閱 <xref:System.Security.Policy.AllMembershipCondition>。|  
|**-appdir**|指定應用程式目錄。 如果您將 **–appdir** 指定為成員資格條件，系統會比較程式碼的 URL 辨識項與該程式碼的應用程式目錄辨識項。 如果兩個辨識項的值相同，表示符合這個成員條件。 如需這個成員資格條件的詳細資訊，請參閱 <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition>。|  
|**-custom**  *xmlfile*|加入自訂成員資格條件。 強制 *xmlfile* 引數會指定包含自訂成員資格條件之 XML 序列化的 .xml 檔。|  
|**-hash** *hashAlg* {**-hex** *hashValue* &#124; **-file** *assembly_file* }|指定具有指定組件雜湊的程式碼。 若要使用雜湊做為程式碼群組成員資格條件，則必須指定雜湊值或組件檔。 如需這個成員資格條件的詳細資訊，請參閱 <xref:System.Security.Policy.HashMembershipCondition>。|  
|**-pub** { **-cert** *cert_file_name* &#124;<br /><br /> **-file** *signed_file_name* &#124; **-hex**  *hex_string* }|指定具有所指軟體發行者的程式碼，該發行者的表示方式為憑證檔、檔案上的簽章或 X509 憑證的十六進位表示。 如需這個成員資格條件的詳細資訊，請參閱 <xref:System.Security.Policy.PublisherMembershipCondition>。|  
|**-site** *website*|指定具有所指來源網站的程式碼。 例如: <br /><br /> **-site** www.proseware.com<br /><br /> 如需這個成員資格條件的詳細資訊，請參閱 <xref:System.Security.Policy.SiteMembershipCondition>。|  
|**-strong -file** *file_name* {*name* &#124; **-noname**} {*version* &#124; **-noversion**}|可指定具有特定強式名稱的程式碼，該名稱的指定方式為檔案名稱、組件名稱 (字串形式)，以及格式為 *major*.*minor*.*build*.*revision* 的組件版本。 例如: <br /><br /> **-strong -file** myAssembly.exe myAssembly 1.2.3.4<br /><br /> 如需這個成員資格條件的詳細資訊，請參閱 <xref:System.Security.Policy.StrongNameMembershipCondition>。|  
|**-url** *URL*|指定來自所指 URL 的程式碼。 這個 URL 必須包括通訊協定，例如 http:// 或 ftp://。 此外，您可以使用萬用字元 (\*) 指定來自特定 URL 的多個組件。 **注意：**因為 URL 可以使用多個名稱來識別，所以將 URL 作為成員資格條件來確定程式碼識別並不安全。 請盡可能使用強式名稱 (Strong Name) 成員資格條件、發行者成員資格條件或雜湊成員資格條件。 <br /><br /> 如需這個成員資格條件的詳細資訊，請參閱 <xref:System.Security.Policy.UrlMembershipCondition>。|  
|**-zone** *zonename*|指定具有所指原始區域的程式碼。 *zonename* 引數可以是下列其中一個值：**MyComputer**、**Intranet**、**Trusted**、**Internet** 或 **Untrusted**。 如需這個成員資格條件的詳細資訊，請參閱 <xref:System.Security.Policy.ZoneMembershipCondition> 類別。|  
  
 *flags* 引數是使用下列其中一種方式指定，並且可以搭配 **–addgroup** 和 **–chggroup** 選項使用。  
  
|引數|描述|  
|--------------|-----------------|  
|**-description "** *description* **"**|如果搭配 **–addgroup** 選項使用，可指定要新增的程式碼群組描述。 如果搭配 **–chggroup** 選項使用，可指定要編輯的程式碼群組描述。 *description* 引數必須括在雙引號中。|  
|**-exclusive** {**on**&#124;**off**}|設為 **on** 時，表示當部分程式碼符合程式碼群組的成員資格條件時，只會考慮與您要新增或修改的程式碼群組相關聯的權限集合。 這個選項設為 **off** 時，Caspol.exe 會考慮原則層級中所有相符程式碼群組的權限集合。|  
|**-levelfinal** {**on**&#124;**off**}|設為 **on** 時，表示不會考慮新增或修改程式碼群組所在層級之下的原則層級。 這個選項通常於電腦原則層級使用。 例如，如果您在電腦層級為程式碼群組設定這個旗標，而某個程式碼符合這個程式碼群組的成員資格條件，Caspol.exe 將不會為這個程式碼計算或套用使用者層級原則。|  
|**-name "** *name* **"**|如果搭配 **–addgroup** 選項使用，可指定要新增之程式碼群組的指令碼名稱。 如果搭配 **-chggroup** 選項使用，可指定要編輯之程式碼群組的指令碼名稱。 *name* 引數必須括在雙引號中。 *name* 引數不能以數字開頭，而且只能包含 A-Z、0-9 和底線字元。 您可以藉由這個 *name* 來參考程式碼群組，而不是藉由其數值標籤。 *name* 對於編寫指令碼也非常有用。|  
  
## <a name="remarks"></a>備註  
 安全性原則是使用三個原則層級表示：電腦原則、使用者原則和企業原則。 組件收到的權限集合是由這三種原則層級允許的權限集合交集所決定。 每個原則層級是以程式碼群組的階層結構表示。 每個程式碼群組都具有成員資格條件，用以判斷哪一個程式碼是該群組的成員。 具名權限集合也會與每個程式碼群組相關聯。 這個權限集合會指定執行階段允許符合成員資格條件的程式碼具備的權限。 程式碼群組階層架構與相關聯的具名權限集合一起定義並維護每一個層級的安全性原則。 您可以使用 **–user**、**-customuser**、**–machine** 和 **-enterprise** 選項來設定安全性原則的層級。  
  
 如需安全性原則以及執行階段如何決定要授與程式碼之權限的詳細資訊，請參閱[安全性原則管理](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)。  
  
## <a name="referencing-code-groups-and-permission-sets"></a>參考程式碼群組和權限集合  
 為了簡化階層架構中程式碼群組的參考，**-list** 選項會以縮排方式顯示程式碼群組清單與其數字標籤 (1、1.1、1.1.1，以此類推)。 其他以程式碼群組為目標的命令列作業也會使用數字標籤參考特定程式碼群組。  
  
 具名權限集合是藉由其名稱參考。 **–list** 選項會顯示程式碼群組清單，後接該原則中可用的具名權限集合清單。  
  
## <a name="caspolexe-behavior"></a>Caspol.exe 行為  
 **-s**[**ecurity**] {**on** &#124; **off**} 以外的所有選項都會使用安裝 Caspol.exe 的 .NET Framework 版本。 如果您執行的 Caspol.exe 是使用 *X* 版的執行階段進行安裝，則變更只會套用至該版本。 其他並存的執行階段安裝 (如果有的話) 則不受影響。 如果您從命令列執行 Caspol.exe，而不是在特定執行階段版本的目錄中執行，則該工具會從路徑中的第一個執行階段版本目錄執行 (通常是安裝的最新執行階段版本)。  
  
 **-s**[**ecurity**] {**on** &#124; **off**} 選項是整個電腦的作業。 關閉程式碼存取安全性會終止電腦上所有 Managed 程式碼和所有使用者的安全性檢查。 如果已安裝並存的 .NET Framework 版本，這個命令會關閉電腦上安裝之所有版本的安全性。 雖然 **-list** 選項會顯示安全性已關閉，但是不會對其他使用者清楚指出安全性已關閉。  
  
 當未具備管理權限的使用者執行 Caspol.exe 時，除非指定 **–machine** 選項，否則所有選項都會參考使用者層級原則。 當系統管理員執行 Caspol.exe 時，除非指定 **–user** 選項，否則所有選項都會參考電腦原則。  
  
 Caspol.exe 必須具有與 **Everything** 權限集合對等的權限才能運作。 此工具有保護機制，可防止原則遭到修改，而造成 Caspol.exe 無法獲得執行所需的權限。 如果您嘗試進行這類變更，Caspol.exe 會通知您要求的原則變更將中斷工具，並且拒絕原則變更。 您可以使用 **–force** 選項，針對特定命令關閉這項保護機制。  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>手動編輯安全性設定檔  
 三個安全性設定檔分別對應 Caspol.exe 支援的三個原則層級：一個對應到電腦原則、一個對應到所指使用者的原則，還有一個對應到企業原則。 只有在使用 Caspol.exe 變更電腦、使用者或企業原則時，才會在磁碟上建立這些檔案。 如有需要，您可以在 Caspol.exe 中使用 **–reset** 選項，將預設的安全性原則儲存到磁碟中。  
  
 在大部分狀況下，不建議手動編輯安全性設定檔。 不過，有些情況下會需要修改這些檔案，例如系統管理員想要編輯特定使用者的安全性設定檔。  
  
## <a name="examples"></a>範例  
 **-addfulltrust**  
  
 假設已將包含自訂權限的權限集合加入至電腦原則。 這個自訂權限是在 `MyPerm.exe` 中實作，而 `MyPerm.exe` 會參考 `MyOther.exe` 中的類別。 這兩個組件都必須加入至完全信任組件清單。 下列命令會將 `MyPerm.exe` 組件加入至電腦原則的完全信任清單。  
  
```  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 下列命令會將 `MyOther.exe` 組件加入至電腦原則的完全信任清單。  
  
```  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 下列命令會將子程式碼群組加入至電腦原則程式碼群組階層架構的根。 新的程式碼群組是 **Internet** 區域的成員，並且與 **Execution** 權限集合產生關聯。  
  
```  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 下列命令會新增子節點群組，可提供共用 \\\netserver\netshare 近端內部網路權限。  
  
```  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 下列命令會將 `Mypset` 權限集合加入至使用者原則。  
  
```  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 下列命令會將標記為 1.2. 之程式碼群組的使用者原則中的權限集合，變更為 **Execution** 權限集合。  
  
```  
caspol -user -chggroup 1.2. Execution  
```  
  
 下列命令會變更標記為 1.2.1. 之程式碼群組的預設原則成員資格條件， 並且變更 **exclusive** 旗標的設定。 系統會將成員資格條件定義為源自 **Internet** 區域的程式碼，而且會開啟 **exclusive** 旗標。  
  
```  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 下列命令會將名稱為 `Mypset` 的權限集合變更為 `newpset.xml` 中包含的權限集合。 請注意，目前版本不支援變更程式碼群組階層架構所使用的權限集合。  
  
```  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 下列命令會讓使用者原則的根程式碼群組 (標記為 1) 與 **Nothing** 具名權限集合產生關聯。 這樣會使 Caspol.exe 無法執行。  
  
```  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-recover**  
  
 下列命令會復原最近儲存的電腦原則。  
  
```  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 下列命令會將標記為 1.1 的程式碼群組移除。 如果這個程式碼群組有任何子程式碼群組，則這些群組也會一併刪除。  
  
```  
caspol -remgroup 1.1.  
```  
  
 **-rempset**  
  
 下列命令會將 **Execution** 權限集合從使用者原則中移除。  
  
```  
caspol -user -rempset Execution  
```  
  
 下列命令會將 `Mypset` 從使用者原則層級中移除。  
  
```  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 下列命令會顯示 `myassembly` 所屬之電腦原則的所有程式碼群組。  
  
```  
caspol -machine -resolvegroup myassembly  
```  
  
 下列命令會顯示 `myassembly` 所屬之電腦、企業和指定之自訂使用者原則的所有程式碼群組。  
  
```  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 下列命令會依據電腦和使用者原則層級計算 `testassembly` 的權限。  
  
```  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>請參閱  
 [工具](../../../docs/framework/tools/index.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
