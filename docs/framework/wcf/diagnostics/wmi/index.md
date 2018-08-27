---
title: 使用 Windows Management Instrumentation 進行診斷
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: b1ebb6b438df6d7efb5342a82e42220a58ea5cbd
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908142"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>使用 Windows Management Instrumentation 進行診斷
Windows Communication Foundation (WCF) 公開服務，以在透過 WCF Windows Management Instrumentation (WMI) 提供者的執行階段檢查的資料。  
  
## <a name="enabling-wmi"></a>啟用 WMI  
 WMI 是 Microsoft 對「Web 架構企業管理」(Web-Based Enterprise Management，WBEM) 標準的實作。 如需有關 WMI SDK 的詳細資訊，請參閱 < [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page)。 WBEM 是一套業界標準，說明應用程式如何將管理測試設備公開至外部管理工具。  
  
 WMI 提供者是一個元件，可透過 WBEM 相容介面，在執行階段公開測試設備。 它是由一組含有屬性/值配對的 WMI 物件所組成。 配對可以是數個簡單型別。 管理工具可以在執行階段，透過介面連接到服務。 WCF 會公開服務，例如位址、 繫結、 行為和接聽程式的屬性。  
  
 內建的 WMI 提供者可以在應用程式的組態檔中啟動。 這是透過`wmiProviderEnabled`的屬性[\<診斷 >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)中[ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)區段，如下列範例所示組態設定。  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 這個組態項目會公開 WMI 介面。 現在，管理應用程式可以透過這個介面進行連線，並存取應用程式的管理測試設備。  
  
## <a name="accessing-wmi-data"></a>存取 WMI 資料  
 您可以使用各種不同的方式來存取 WMI 資料。 Microsoft 指令碼、 Visual Basic 應用程式、 c + + 應用程式，提供了 WMI Api 和[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 使用 WMI](http://go.microsoft.com/fwlink/?LinkId=95183)。  
  
> [!CAUTION]
>  如果您使用 .NET Framework 提供的方法，以程式設計方式存取 WMI 資料，您要注意，當連線建立時，這類方法可能會擲回例外狀況。 連線不是在建構 <xref:System.Management.ManagementObject> 執行個體期間建立的，而是在第一次要求實際資料交換時建立。 因此，您應該使用 `try..catch` 區塊攔截可能的例外狀況。  
  
 您可以在 WMI 中變更 `System.ServiceModel` 追蹤來源的追蹤和訊息記錄層級，以及訊息記錄選項。 這可以藉由存取[AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)執行個體，它會公開下列布林值屬性： `LogMessagesAtServiceLevel`， `LogMessagesAtTransportLevel`， `LogMalformedMessages`，和`TraceLevel`。 因此，如果您為訊息記錄設定一個追蹤接聽項，但在組態中將這些選項設定為 `false`，那麼您可以在稍後應用程式執行時，將選項變更為 `true`。 這將會在執行階段有效地啟用訊息記錄。 同樣地，如果您在組態檔中啟用訊息記錄，則您可以在執行階段使用 WMI 來停用訊息記錄。  
  
 您要注意，如果沒有為訊息記錄設定訊息記錄追蹤接聽項，或者組態檔中沒有指定 `System.ServiceModel` 追蹤接聽項來進行追蹤，則您所做的變更不會有任何作用，即使 WMI 接受這些變更也一樣。 如需正確設定各接聽項的詳細資訊，請參閱[設定訊息記錄](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)並[設定追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)。 組態所指定之所有其他追蹤來源的追蹤層級，會在應用程式啟動時生效，並且無法變更。  
  
 WCF 會公開`GetOperationCounterInstanceName`指令碼處理方法。 如果您提供了一個作業名稱，這個方法就會傳回一個效能計數器執行個體名稱。 不過，它不會驗證您的輸入。 因此，如果您提供的作業名稱不正確，就會傳回錯誤的計數器名稱。  
  
 `OutgoingChannel`的屬性`Service`執行個體不會計算內未建立至目的地服務的 WCF 用戶端連線到另一個服務，服務所開啟的通道`Service`方法。  
  
 **請小心**WMI 只支援<xref:System.TimeSpan>值最多 3 個小數位數。 例如，如果您的服務將其中一個屬性設定為 <xref:System.TimeSpan.MaxValue>，則透過 WMI 檢視時，小數點後三位之後的值將被截斷。  
  
## <a name="security"></a>安全性  
 因為 WCF WMI 提供者允許在環境中的探索服務，所以您應該特別小心謹慎授與存取權。 如果您將預設僅供系統管理員存取的限制放寬，可能導致信賴度較低的一方存取環境中的敏感性資料。 特別是，如果您放寬遠端 WMI 存取的權限，可能導致氾濫攻擊。 如果某個處理序湧入了大量 WMI 要求，可能會使它的效能降低。  
  
 此外，如果您放寬了 MOF 檔案的存取權限，信賴度較低的一方就可以操控 WMI 的行為，並改變 WMI 結構描述中載入的物件。 例如，欄位可能會遭到移除，導致管理員無法看見重要資料，或是原本不會填入或造成例外狀況的欄位會加入至檔案。  
  
 根據預設，WCF WMI 提供者授與 「 執行方法 」、 「 提供者寫入 」 和 「 啟用帳戶 」 為系統管理員的權限，以及 ASP.NET、 本機服務和網路服務的 「 啟用帳戶 」 權限。 特別是，在非 [!INCLUDE[wv](../../../../../includes/wv-md.md)] 平台上，ASP.NET 帳戶具有 WMI ServiceModel 命名空間的讀取權限。 如果您不想將這些權限授與特定使用者群組，則應該停用 WMI 提供者 (預設為停用) 或停用特定使用者群組的存取。  
  
 此外，當您嘗試透過組態啟用 WMI 時，可能因為使用者權限不足，而無法啟用 WMI。 不過，事件記錄內不會寫入任何事件以記錄這項失敗。  
  
 若要修改使用者權限層級，請依照下列步驟執行。  
  
1.  按一下 [開始]，然後執行，並輸入**compmgmt.msc**。  
  
2.  以滑鼠右鍵按一下**服務和應用程式 /WMI 控制項**來選取**屬性**。  
  
3.  選取 **安全性**索引標籤上，並瀏覽至**Root/ServiceModel**命名空間。 按一下 [**安全性**] 按鈕。  
  
4.  選取 特定群組或您想要控制存取和使用的使用者**允許**或是**拒絕**核取方塊以設定權限。  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>將 WCF WMI 註冊權限授與其他使用者  
 WCF 會將管理資料公開至 WMI。 它會裝載同處理序 WMI 提供者，有時也稱為 「 低耦合提供者 」。 若要讓管理資料公開，註冊此提供者的帳戶必須有適當權限。 在 Windows 中，預設只有一小組授權的帳戶可以登錄低耦合提供者。 這是一個問題，因為使用者通常想要從非預設集合中之帳戶下執行的 WCF 服務公開 WMI 資料。  
  
 若要提供此存取權，系統管理員必須依下列順序將下列權限授與其他帳戶：  
  
1.  存取 WCF WMI 命名空間的權限。  
  
2.  註冊 WCF 低耦合 WMI 提供者的權限。  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>若要授與 WMI 命名空間存取權限  
  
1.  執行下列 PowerShell 指令碼。  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     此 PowerShell 指令碼使用 Security Descriptor Definition Language (SDDL) 授與內建的使用者群組存取"root/servicemodel"WMI 命名空間。 它指定下列 ACL：  
  
    -   內建系統管理員 (BA) - 已經有存取權。  
  
    -   網路服務 (NS) - 已經有存取權。  
  
    -   本機系統 (LS) - 已經有存取權。  
  
    -   內建使用者 - 要授與存取權的目標群組。  
  
#### <a name="to-grant-provider-registration-access"></a>若要授與提供者註冊存取  
  
1.  執行下列 PowerShell 指令碼。  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>授與任意使用者或群組存取權  
 本節中的範例會將 WMI 提供者註冊權限授與所有本機使用者。 如果您要授與非內建使用者或群組存取權，必須取得該使用者或群組的安全性識別碼 (SID)。 目前沒有簡易的方法可以取得任意使用者的 SID。 一個方法是以所要的使用者身分登入，然後發出下列 Shell 命令。  
  
```  
Whoami /user  
```  
  
 這個方法會提供目前使用者的 SID，但無法用來取得任意使用者的 SID。 另一個取得 SID，方法是使用[getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467)工具[Windows 2000 Resource Kit 工具用於系統管理工作](http://go.microsoft.com/fwlink/?LinkId=178660)。 此工具會比較兩個使用者 (本機或網域) 的 SID，並以副作用方式將兩個 SID 列印至命令列。 如需詳細資訊，請參閱 <<c0> [ 已知 Sid](http://go.microsoft.com/fwlink/?LinkId=186468)。  
  
## <a name="accessing-remote-wmi-object-instances"></a>存取遠端 WMI 物件執行個體  
 如果您需要存取 WCF WMI 執行個體，在遠端電腦上的，您必須啟用您用來存取的工具上的封包私密性。 下列小節說明如何使用 WMI CIM Studio、Windows Management Instrumentation 測試器以及 .NET SDK 2.0 來完成這項工作。  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 如果您已安裝[WMI 系統管理工具](http://go.microsoft.com/fwlink/?LinkId=95185)，您可以使用 WMI CIM Studio 來存取 WMI 執行個體。 工具位於下列資料夾中  
  
 **%windir%\Program Files\WMI 工具\\**  
  
1.  在 **連接至命名空間：** 視窗中，輸入**root\ServiceModel**按一下**確定。**  
  
2.  在 [ **WMI CIM Studio 登入**] 視窗中，按一下**選項 >>** 按鈕展開視窗。 選取**封包私密性**for**驗證層級**，然後按一下**確定**。  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Management Instrumentation 測試器  
 這個工具是由 Windows 進行安裝。 若要執行它，請啟動命令主控台中輸入**cmd.exe**中**開始/執行**對話方塊中，然後按一下**確定**。 然後，輸入**wbemtest.exe**命令視窗中。 [Windows Management Instrumentation 測試器] 工具隨即啟動。  
  
1.  按一下  **Connect**視窗的右上角的按鈕。  
  
2.  在新視窗中，輸入**root\ServiceModel** for**命名空間**欄位，然後選取**封包私密性**如**驗證層級**。 按一下 **[Connect]**(連線)。  
  
### <a name="using-managed-code"></a>使用 Managed 程式碼  
 您也可以使用 <xref:System.Management> 命名空間提供的類別，以程式設計方式存取遠端 WMI 執行個體。 下列程式碼範例示範如何執行這項操作。  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
