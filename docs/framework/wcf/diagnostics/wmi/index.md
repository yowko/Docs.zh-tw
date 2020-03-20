---
title: 使用 Windows Management Instrumentation 進行診斷
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 0c803e3988f7a63980d991190db87c263c992b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185681"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>使用 Windows Management Instrumentation 進行診斷
Windows 通信基礎 （WCF） 通過 WCF Windows 管理檢測 （WMI） 提供程式在運行時公開服務的檢查資料。  
  
## <a name="enabling-wmi"></a>啟用 WMI  
 WMI 是 Microsoft 對「Web 架構企業管理」(Web-Based Enterprise Management，WBEM) 標準的實作。 有關 WMI SDK 的詳細資訊，請參閱[Windows 管理檢測](/windows/desktop/WmiSdk/wmi-start-page)。 WBEM 是一套業界標準，說明應用程式如何將管理測試設備公開至外部管理工具。  
  
 WMI 提供者是一個元件，可透過 WBEM 相容介面，在執行階段公開測試設備。 它是由一組含有屬性/值配對的 WMI 物件所組成。 配對可以是數個簡單型別。 管理工具可以在執行階段，透過介面連接到服務。 WCF 公開服務的屬性，如位址、綁定、行為和攔截器。  
  
 內建的 WMI 提供者可以在應用程式的組態檔中啟動。 這是通過`wmiProviderEnabled`[\<系統中的診斷>](../../../configure-apps/file-schema/wcf/diagnostics.md)的屬性完成的>。 [ \< ](../../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 這個組態項目會公開 WMI 介面。 現在，管理應用程式可以透過這個介面進行連線，並存取應用程式的管理測試設備。  
  
## <a name="accessing-wmi-data"></a>存取 WMI 資料  
 您可以使用各種不同的方式來存取 WMI 資料。 Microsoft 為腳本、視覺化基本應用程式、C++應用程式和 .NET 框架提供 WMI API。 有關詳細資訊，請參閱使用[WMI](/windows/win32/wmisdk/using-wmi)。  
  
> [!CAUTION]
> 如果您使用 .NET Framework 提供的方法，以程式設計方式存取 WMI 資料，您要注意，當連線建立時，這類方法可能會擲回例外狀況。 連線不是在建構 <xref:System.Management.ManagementObject> 執行個體期間建立的，而是在第一次要求實際資料交換時建立。 因此，您應該使用 `try..catch` 區塊攔截可能的例外狀況。  
  
 您可以在 WMI 中變更 `System.ServiceModel` 追蹤來源的追蹤和訊息記錄層級，以及訊息記錄選項。 這可以通過訪問[AppDomainInfo](appdomaininfo.md) `LogMessagesAtServiceLevel`實例來實現，該實例公開了這些布林屬性： 、`LogMessagesAtTransportLevel``LogMalformedMessages`和`TraceLevel`。 因此，如果您為訊息記錄設定一個追蹤接聽項，但在組態中將這些選項設定為 `false`，那麼您可以在稍後應用程式執行時，將選項變更為 `true`。 這將會在執行階段有效地啟用訊息記錄。 同樣地，如果您在組態檔中啟用訊息記錄，則您可以在執行階段使用 WMI 來停用訊息記錄。  
  
 您要注意，如果沒有為訊息記錄設定訊息記錄追蹤接聽項，或者組態檔中沒有指定 `System.ServiceModel` 追蹤接聽項來進行追蹤，則您所做的變更不會有任何作用，即使 WMI 接受這些變更也一樣。 有關正確設置相應攔截器的詳細資訊，請參閱[配置消息日誌記錄](../configuring-message-logging.md)和[配置跟蹤](../tracing/configuring-tracing.md)。 組態所指定之所有其他追蹤來源的追蹤層級，會在應用程式啟動時生效，並且無法變更。  
  
 WCF 公開了`GetOperationCounterInstanceName`一種腳本化方法。 如果您提供了一個作業名稱，這個方法就會傳回一個效能計數器執行個體名稱。 不過，它不會驗證您的輸入。 因此，如果您提供的作業名稱不正確，就會傳回錯誤的計數器名稱。  
  
 如果`OutgoingChannel`WCF`Service`用戶端未在`Service`方法中創建，則實例的屬性不會計算服務打開以連接到其他服務的通道。  
  
 **注意事項**WMI 僅支援<xref:System.TimeSpan>最多 3 個小數點的值。 例如，如果您的服務將其中一個屬性設定為 <xref:System.TimeSpan.MaxValue>，則透過 WMI 檢視時，小數點後三位之後的值將被截斷。  
  
## <a name="security"></a>安全性  
 由於 WCF WMI 提供程式允許在環境中發現服務，因此在授予對服務的許可權時應格外小心。 如果您將預設僅供系統管理員存取的限制放寬，可能導致信賴度較低的一方存取環境中的敏感性資料。 特別是，如果您放寬遠端 WMI 存取的權限，可能導致氾濫攻擊。 如果某個處理序湧入了大量 WMI 要求，可能會使它的效能降低。  
  
 此外，如果您放寬了 MOF 檔案的存取權限，信賴度較低的一方就可以操控 WMI 的行為，並改變 WMI 結構描述中載入的物件。 例如，欄位可能會遭到移除，導致管理員無法看見重要資料，或是原本不會填入或造成例外狀況的欄位會加入至檔案。  
  
 預設情況下，WCF WMI 提供程式為管理員授予"執行方法"、"提供程式寫入"和"啟用帳戶"許可權，並為ASP.NET、本機服務和網路服務授予"啟用帳戶"許可權。 特別是，在非 Windows Vista 平臺上，ASP.NET帳戶已讀取對 WMI 服務模型命名空間的存取權限。 如果您不想將這些權限授與特定使用者群組，則應該停用 WMI 提供者 (預設為停用) 或停用特定使用者群組的存取。  
  
 此外，當您嘗試透過組態啟用 WMI 時，可能因為使用者權限不足，而無法啟用 WMI。 不過，事件記錄內不會寫入任何事件以記錄這項失敗。  
  
 若要修改使用者權限層級，請依照下列步驟執行。  
  
1. 按一下"開始"，然後"運行"並鍵入**compmgmt.msc**。  
  
2. 按右鍵**服務和應用程式/WMI 控制項**以選擇**屬性**。  
  
3. 選擇 **"安全**"選項卡，然後導航到**根/服務模型**命名空間。 按一下 **"安全**"按鈕。  
  
4. 選擇要控制訪問的特定組或使用者，並使用 **"允許**"或 **"拒絕"** 核取方塊配置許可權。  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>將 WCF WMI 註冊權限授與其他使用者  
 WCF 會將管理資料公開至 WMI。 它通過託管進程內 WMI 提供程式（有時稱為"分離提供程式"）來達到這一要求。 若要讓管理資料公開，註冊此提供者的帳戶必須有適當權限。 在 Windows 中，預設只有一小組授權的帳戶可以登錄低耦合提供者。 這是一個問題，因為使用者通常想要從非預設集合中之帳戶下執行的 WCF 服務公開 WMI 資料。  
  
 若要提供此存取權，系統管理員必須依下列順序將下列權限授與其他帳戶：  
  
1. 存取 WCF WMI 命名空間的權限。  
  
2. 註冊 WCF 低耦合 WMI 提供者的權限。  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>若要授與 WMI 命名空間存取權限  
  
1. 執行下列 PowerShell 指令碼。  
  
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
  
     此 PowerShell 腳本使用安全描述項定義語言 （SDDL） 授予內置使用者組對"根/服務模式"WMI 命名空間的存取權限。 它指定下列 ACL：  
  
    - 內建系統管理員 (BA) - 已經有存取權。  
  
    - 網路服務 (NS) - 已經有存取權。  
  
    - 本機系統 (LS) - 已經有存取權。  
  
    - 內建使用者 - 要授與存取權的目標群組。  
  
#### <a name="to-grant-provider-registration-access"></a>若要授與提供者註冊存取  
  
1. 執行下列 PowerShell 指令碼。  
  
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
  
```console
Whoami /user  
```  
  
 這個方法會提供目前使用者的 SID，但無法用來取得任意使用者的 SID。 獲取 SID 的另一種方法是使用 Windows 2000 資源工具組工具中的[getsid.exe](/windows/win32/wmisdk/using-wmi)工具執行管理工作。 此工具會比較兩個使用者 (本機或網域) 的 SID，並以副作用方式將兩個 SID 列印至命令列。 有關詳細資訊，請參閱已知[S](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems)。  
  
## <a name="accessing-remote-wmi-object-instances"></a>存取遠端 WMI 物件執行個體  
 如果需要在遠端電腦上訪問 WCF WMI 實例，則必須在用於訪問的工具上啟用資料包隱私。 下列小節說明如何使用 WMI CIM Studio、Windows Management Instrumentation 測試器以及 .NET SDK 2.0 來完成這項工作。  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 如果您已安裝[WMI 管理工具](https://go.microsoft.com/fwlink/?LinkId=95185)，則可以使用 WMI CIM 工作室訪問 WMI 實例。 工具位於下列資料夾中  
  
 **%windir%\程式檔\WMI 工具\\**  
  
1. 在 **"連接到命名空間："** 視窗中，鍵入**root_ServiceModel**並按一下 **"確定"。**  
  
2. 在**WMI CIM 工作室登錄**視窗中，按一下 **"選項 >>"** 按鈕以展開視窗。 選擇**身份驗證級別的****資料包隱私**，然後按一下 **"確定**"。  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Management Instrumentation 測試器  
 這個工具是由 Windows 進行安裝。 要運行它，請在 **"開始/運行"** 對話方塊中鍵入**cmd.exe**來啟動命令主控台，然後按一下"**確定**"。 然後，在命令視窗中鍵入**wbemtest.exe。** [Windows Management Instrumentation 測試器] 工具隨即啟動。  
  
1. 按一下視窗右上角的 **"連接**"按鈕。  
  
2. 在新視窗中，為**命名空間**欄位輸入**root_ServiceModel，** 並為**身份驗證級別**選擇**資料包隱私**。 按一下 [連線]****。  
  
### <a name="using-managed-code"></a>使用 Managed 程式碼  
 您也可以使用 <xref:System.Management> 命名空間提供的類別，以程式設計方式存取遠端 WMI 執行個體。 下列程式碼範例示範如何執行這項操作。  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
