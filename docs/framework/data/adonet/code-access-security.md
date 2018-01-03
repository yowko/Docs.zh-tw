---
title: "程式碼存取安全性和 ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 754c380972d79343eab83b9e862e478798218ffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="code-access-security-and-adonet"></a>程式碼存取安全性和 ADO.NET
.NET Framework 會提供以角色為基礎的安全性和程式碼存取安全性 (CAS)，而這兩種安全性都是使用 Common Language Runtime (CLR) 所提供的通用基礎結構所實作的。 在 Unmanaged 程式碼的作用範圍內，大多數應用程式都是以使用者或主體的權限執行。 因此，當擁有更高權限的使用者執行惡意或充滿錯誤的軟體時，就可能損害電腦系統和竊取私人資料。  
  
 相較之下，在 .NET Framework 中執行的 Managed 程式碼具有單獨套用至程式碼的程式碼存取安全性。 系統是否允許執行程式碼會取決於程式碼的來源或程式碼識別的其他層面，而非單獨取決於主體的識別。 這能降低 Managed 程式碼被誤用的可能性。  
  
## <a name="code-access-permissions"></a>程式碼存取使用權限  
 執行程式碼時，它會顯示 CLR 安全性系統所評估的辨識項。 一般來說，這個辨識項會洩露程式碼的來源，包含 URL、大小和區域，以及用來確保組件識別的數位簽章。  
  
 CLR 僅允許程式碼執行該程式碼有權執行的這些作業。 程式碼可以要求權限，而且系統會根據系統管理員所設定的安全性原則來接受這些要求。  
  
> [!NOTE]
>  CLR 中執行的程式碼不能授與其本身的使用權限。 例如，程式碼可以要求而且被授與少於安全性原則允許的權限，但是它絕不會被授與更多權限。 授與權限時，系統是以完全沒有權限開始，然後加入執行特定工作的最少權限。 如果一開始便使用所有權限，然後再拒絕個別的權限，則會造成應用程式不安全，因為可能會授與超出必要的權限而導致意外安全性漏洞。 如需詳細資訊，請參閱[NIB： 設定安全性原則](http://msdn.microsoft.com/en-us/0f130bcd-1bba-4346-b231-0bcca7dab1a4)和[NIB： 安全性原則管理](http://msdn.microsoft.com/en-us/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)。  
  
 程式碼存取權限有三種類型：  
  
-   `Code access permissions`衍生自 <xref:System.Security.CodeAccessPermission> 類別。 為了存取受保護資源 (例如檔案和環境變數) 以及執行受保護作業 (例如存取 Unmanaged 程式碼)，因此需要權限。  
  
-   `Identity permissions` 代表可識別組件的特性。 系統會根據辨識項 (可能包含數位簽章或程式碼來源等項目)，將權限授與組件。 識別權限也衍生自 <xref:System.Security.CodeAccessPermission> 基底類別 (Base Class)。  
  
-   `Role-based security permissions`是以主體是否具有指定的識別或屬於指定角色成員為基礎。 <xref:System.Security.Permissions.PrincipalPermission> 類別允許針對使用中主體進行宣告式和必要的權限檢查。  
  
 為了判斷程式碼是否經授權可存取資源或執行某項作業，執行階段的安全性系統會周遊呼叫堆疊，並比較每個呼叫端被授與的權限與要求的權限。 如果呼叫堆疊中的任何呼叫端沒有要求的權限，系統就會擲回 <xref:System.Security.SecurityException> 並拒絕存取。  
  
### <a name="requesting-permissions"></a>要求權限  
 要求權限的目的是向執行階段通知您的應用程式需要哪些權限才能執行，以及確保它只會收到實際需要的權限。 例如，如果您的應用程式必須將資料寫入本機磁碟，它就需要 <xref:System.Security.Permissions.FileIOPermission>。 如果系統沒有授與該權限，當此應用程式嘗試寫入磁碟時，它就會失敗。 不過，如果應用程式要求 `FileIOPermission`，但系統沒有授與該權限，則此應用程式一開始將產生例外狀況而且不會載入。  
  
 在應用程式僅需要從磁碟中讀取資料的情況下，您可以要求絕不授與任何寫入權限給應用程式。 在錯誤或惡意攻擊的事件中，您的程式碼無法破壞它所運作的資料。 如需詳細資訊，請參閱[NIB： 要求權限](http://msdn.microsoft.com/en-us/0447c49d-8cba-45e4-862c-ff0b59bebdc2)。  
  
## <a name="role-based-security-and-cas"></a>以角色為基礎的安全性和 CAS  
 同時實作以角色為基礎的安全性和程式碼存取安全性 (CAS) 可強化應用程式的整體安全性。 以角色為基礎的安全性可以根據 Windows 帳戶或自訂識別，將安全性主體的相關資訊提供給目前的執行緒。 此外，應用程式通常會根據使用者所提供的認證，提供對資料或資源的存取。 基本上，這類應用程式會檢查使用者的角色並根據這些角色提供資源存取。  
  
 以角色為基礎的安全性可讓某個元件在執行階段識別目前的使用者及其相關聯的角色。 然後，系統會使用 CAS 原則來對應這項資訊，以便判斷在執行階段授與的權限集合。 若為指定的應用程式定義域，主應用程式 (Host) 就可以變更預設的以角色為基礎安全性原則，並且設定預設的安全性主體，以便代表某位使用者以及與該使用相關聯的角色。  
  
 CLR 會使用某些權限來實作在 Managed 程式碼上強制執行限制的機制。 以角色為基礎的安全性權限會提供一項機制，讓您探索某位使用者 (或代表使用者運作的代理程式) 是否具有特定識別或屬於指定角色的成員。 如需詳細資訊，請參閱[安全性權限](http://msdn.microsoft.com/en-us/b03757b4-e926-4196-b738-3733ced2bda0)。  
  
 根據您所建立的應用程式類型，您也應該考慮在資料庫中實作以角色為基礎的權限。 如需有關 SQL Server 中的 角色型安全性的詳細資訊，請參閱[SQL Server 安全性](../../../../docs/framework/data/adonet/sql/sql-server-security.md)。  
  
## <a name="assemblies"></a>組件  
 組件會構成 .NET Framework 應用程式之部署、版本控制、重複使用、啟動範圍和安全性權限的基本單位。 組件會提供針對一起運作而建立而且構成邏輯功能單位之類型和資源的組合。 對 CLR 而言，類型不會存在組件內容外部。 如需有關建立及部署組件的詳細資訊，請參閱[使用組件設計程式](../../../../docs/framework/app-domains/programming-with-assemblies.md)。  
  
### <a name="strong-naming-assemblies"></a>強式命名組件  
 強式名稱 (Strong Name) 或數位簽章包含組件的識別，其中包括簡單文字名稱、版本號碼和文化特性資訊 (如果有提供的話)，以及公開金鑰 (Public Key) 和數位簽章。 數位簽章是從使用對應之私密金鑰的組件檔中產生的。 組件檔包含組件資訊清單 (Assembly Manifest)，其中包含組成組件之所有檔案的名稱和雜湊。  
  
 強式命名組件可提供應用程式或元件唯一的識別，讓其他軟體用來明確參考該應用程式或元件。 強式命名可保護組件，讓內含惡意程式碼的組件無法假冒該組件。 此外，強式命名還能確保不同元件版本之間的版本一致性。 您必須強式命名將部署到全域組件快取 (GAC) 的組件。 如需詳細資訊，請參閱[建立和使用強式名稱的組件](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)。  
  
## <a name="partial-trust-in-adonet-20"></a>ADO.NET 2.0 中的部分信任  
 在 ADO.NET 2.0 中，.NET Framework Data Provider for SQL Server、.NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC 和 .NET Framework Data Provider for Oracle 現在都可以在部分信任的環境中執行。 在舊版的 .NET Framework 中，只有 <xref:System.Data.SqlClient> 才能在低於完全信任的應用程式中使用。  
  
 使用 SQL Server 提供者的部分信任應用程式至少必須具有執行和 <xref:System.Data.SqlClient.SqlClientPermission> 使用權限。  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>部分信任的使用權限屬性  
 在部分信任案例中，可使用 <xref:System.Data.SqlClient.SqlClientPermissionAttribute> 成員進一步限制 SQL Server 的 .NET Framework 資料提供者之可用功能。  
  
 下列表格列出可用的 <xref:System.Data.SqlClient.SqlClientPermissionAttribute> 屬性及其說明：  
  
|使用權限屬性|描述|  
|-----------------------------------|-----------------|  
|`Action`|取得或設定安全性動作。 繼承自 <xref:System.Security.Permissions.SecurityAttribute>。|  
|`AllowBlankPassword`|啟用或停用在連接字串中使用空白密碼。 有效值為 `true` (表示啟用空白密碼) 和 `false` (表示停用空白密碼)。 繼承自 <xref:System.Data.Common.DBDataPermissionAttribute>。|  
|`ConnectionString`|識別允許的連接字串。 可識別多個連接字串。 **注意：**不包含使用者識別碼或密碼在連接字串中。 在這個發行版本中，您無法使用 .NET Framework 組態工具變更連接字串限制。 <br /><br /> 繼承自 <xref:System.Data.Common.DBDataPermissionAttribute>。|  
|`KeyRestrictions`|識別是否為允許的連接字串參數。 在表單中所識別的連接字串參數*\<參數名稱 > =*。 也可以指定多個參數，只要以分號 (;) 將其分隔即可。 **注意：**如果未指定`KeyRestrictions`，但您設定`KeyRestrictionBehavior`屬性`AllowOnly`或`PreventUsage`，允許任何其他連接字串參數。 繼承自 <xref:System.Data.Common.DBDataPermissionAttribute>。|  
|`KeyRestrictionBehavior`|將連接字串參數識別為唯一允許的其他參數 (`AllowOnly`)，或識別不允許的其他參數 (`PreventUsage`)。 `AllowOnly` 是預設值。 繼承自 <xref:System.Data.Common.DBDataPermissionAttribute>。|  
|`TypeID`|在衍生類別中實作時，取得唯一識別項。 繼承自 <xref:System.Attribute>。|  
|`Unrestricted`|指示是否針對資源，宣告不受限的使用權限。 繼承自 <xref:System.Security.Permissions.SecurityAttribute>。|  
  
#### <a name="connectionstring-syntax"></a>ConnectionString 語法  
 下列範例將示範如何使用組態檔的 `connectionStrings` 項目，只允許使用特定的連接字串。 請參閱[連接字串](../../../../docs/framework/data/adonet/connection-strings.md)如需有關儲存和擷取連接字串從組態檔。  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>KeyRestrictions 語法  
 下列範例啟用相同的連接字串，可讓您使用`Encrypt`和`Packet``Size`連接字串選項，但限制使用任何其他連接字串選項。  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>含 PreventUsage 的 KeyRestrictionBehavior 語法  
 下列範例將啟用相同的連接字串，並允許 `User Id`、`Password` 和 `Persist Security Info` 以外的其他所有連接參數。  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>含 AllowOnly 的 KeyRestrictionBehavior 語法  
 下列範例啟用兩個連接字串，這兩個連接字串同時包含 `Initial Catalog`、`Connection Timeout`、`Encrypt` 和 `Packet Size` 參數。 所有其他的連接字串參數則都限制使用。  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
  
  <add name="DatabaseConnection2"   
    connectionString="Data Source=SqlServer2;Initial   
    Catalog=Northwind2;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>以自訂的使用權限集啟用部份信任  
 若要啟用特定區域的 <xref:System.Data.SqlClient> 使用權限，系統管理員必須建立自訂的使用權限集合，並將其設定為特定區域的使用權限集合。 不可修改預設的使用權限集合 (例如 `LocalIntranet`)。 例如，若要包含<xref:System.Data.SqlClient>具有程式碼的權限<xref:System.Security.Policy.Zone>的`LocalIntranet`，系統管理員無法將複製的權限集合`LocalIntranet`、 重新命名為"CustomLocalIntranet 」、 新增<xref:System.Data.SqlClient>匯入的權限，CustomLocalIntranet 使用權限集合使用[Caspol.exe （程式碼存取安全性原則工具）](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)，並將設定的權限集`LocalIntranet_Zone`CustomLocalIntranet 至。  
  
### <a name="sample-permission-set"></a>使用權限集合範例  
 下列是部分受信任案例中的「SQL Server 的 .NET Framework 資料提供者」使用權限集合範例。 如需建立自訂權限集的資訊，請參閱[NIB： 設定權限設定使用 Caspol.exe](http://msdn.microsoft.com/en-us/94e2625e-21ad-4038-af36-6d1f9df40a57)。  
  
```xml  
<PermissionSet class="System.Security.NamedPermissionSet"  
  version="1"  
  Name="CustomLocalIntranet"  
  Description="Custom permission set given to applications on  
    the local intranet">  
  
<IPermission class="System.Data.SqlClient.SqlClientPermission, System.Data, Version=2.0.0000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
version="1"  
AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Integrated Security=true;"  
 KeyRestrictions="Initial Catalog=;Connection Timeout=;  
   Encrypt=;Packet Size=;"   
 KeyRestrictionBehavior="AllowOnly" />  
 </IPermission>  
</PermissionSet>  
```  
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>使用安全性使用權限驗證 ADO.NET 程式碼存取  
 若為部分信任案例，則可指定 <xref:System.Data.SqlClient.SqlClientPermissionAttribute>，藉以取得程式碼中之特定方法的 CAS 權限。 如果生效的限制安全性原則不允許該權限，則在執行程式碼前會擲回例外狀況。 如需有關安全性原則的詳細資訊，請參閱[NIB： 安全性原則管理](http://msdn.microsoft.com/en-us/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)和[NIB： 安全性原則的最佳作法](http://msdn.microsoft.com/en-us/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05)。  
  
### <a name="example"></a>範例  
 下列範例示範如何撰寫需要特定連接字串的程式碼。 它模擬如何拒絕 <xref:System.Data.SqlClient> 的不受限權限，而系統管理員在實務上會使用 CAS 原則來實作這些權限。  
  
> [!IMPORTANT]
>  設計 ADO.NET 的 CAS 權限時，最正確的模式是以最大的限制 (完全沒有權限) 開始，然後加入程式碼必須執行之特殊工作所需的特定權限。 相反的模式 (以所有權限開始，然後再拒絕特定權限) 並不安全，因為有許多方法可表示相同的連接字串。 例如，如果您以所有權限開始，然後嘗試拒絕連接字串 "server=someserver" 的用法，您仍可使用 "server=someserver.mycompany.com" 字串。 只要以不授與任何權限開始，您就能減少權限集合具有漏洞的機會。  
  
 下列程式碼將示範 `SqlClient` 如何執行安全性需求，也就是在沒有適當的 CAS 權限時，擲回 <xref:System.Security.SecurityException>。 主控台視窗會顯示 <xref:System.Security.SecurityException> 輸出。  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 您應該在 [主控台] 視窗中看到以下輸出：  
  
```  
Failed, as expected: <IPermission class="System.Data.SqlClient.  
SqlClientPermission, System.Data, Version=2.0.0.0,   
  Culture=neutral, PublicKeyToken=b77a5c561934e089" version="1"  
  AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Initial Catalog=  
  Northwind;Integrated Security=SSPI" KeyRestrictions=""  
KeyRestrictionBehavior="AllowOnly"/>  
</IPermission>  
  
Connection opened, as expected.  
Failed, as expected: Request failed.  
```  
  
## <a name="interoperability-with-unmanaged-code"></a>與 Unmanaged 程式碼的互通性  
 在 CLR 外部執行的程式碼稱為 Unmanaged 程式碼。 因此，CAS 等安全性機制無法套用至 Unmanaged 程式碼。 COM 元件、ActiveX 介面及 Win32 API 函式都是 Unmanaged 程式碼的範例。 執行 Unmanaged 程式碼時，您應該套用特殊安全性考量，以免危及整體應用程式安全性。 如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)。  
  
 .NET Framework 也透過 COM Interop 提供存取，藉以支援現有 COM 元件的回溯相容性 (Backward Compatibility)。 您可以使用 COM Interop 工具來匯入相關的 COM 型別，以便將 COM 元件併入 .NET Framework 應用程式中。 一旦匯入之後，COM 型別便可供使用。 COM Interop 也會將組件中繼資料匯出至型別程式庫並將 Managed 元件註冊為 COM 元件，藉以讓 COM 用戶端存取 Managed 程式碼。 如需詳細資訊，請參閱[進階 COM 互通性](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)。  
  
## <a name="see-also"></a>請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [PAVE 機器碼和 .NET Framework 程式碼中的安全性](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784)  
 [程式碼存取安全性](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)  
 [以角色為基礎的安全性](http://msdn.microsoft.com/en-us/239442e3-5be4-4203-b7fd-793baffea803)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
