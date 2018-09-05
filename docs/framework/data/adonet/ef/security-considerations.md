---
title: 安全性考量 (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 25d313f9c6f71d946ed8d9cc5db2e99dc84983b3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534080"
---
# <a name="security-considerations-entity-framework"></a>安全性考量 (Entity Framework)
本主題將描述與開發、部署和執行 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 應用程式有關的安全性考量。 您也應該遵循建立安全 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式的建議事項。 如需詳細資訊，請參閱 <<c0> [ 安全性概觀](../../../../../docs/framework/data/adonet/security-overview.md)。  
  
## <a name="general-security-considerations"></a>一般安全性考量  
 下列安全性考量適用於使用 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的所有應用程式。  
  
#### <a name="use-only-trusted-data-source-providers"></a>僅使用信任的資料來源提供者。  
 若要與資料來源通訊，提供者必須進行下列作業：  
  
-   從 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 接收連接字串 (Connection String)。  
  
-   將命令樹轉譯成資料來源的原生 (Native) 查詢語言。  
  
-   組合並傳回結果集。  
  
 進行登入作業期間，以使用者密碼為基礎的資訊會透過基礎資料來源的網路程式庫傳遞至伺服器。 惡意提供者可能會竊取使用者認證、產生惡意查詢，或竄改結果集。  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>加密您的連接以便保護機密資料。  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 不會直接處理資料加密 (Encryption)。 如果使用者透過公用 (Public) 網路存取資料，您的應用程式就應該建立資料來源的加密連接，以便提升安全性。 如需詳細資訊，請參閱資料來源的安全性相關文件。 針對 SQL Server 資料來源，請參閱[加密 SQL Server 的連接](https://go.microsoft.com/fwlink/?LinkId=119544)。  
  
#### <a name="secure-the-connection-string"></a>保護連接字串的安全。  
 保護應用程式時的最重要目標之一就是保護資料來源的存取。 如果連接字串未受保護，或者建構方式不當，它就會成為可能的弱點。 如果您以純文字方式儲存連接資訊，或將它保存在記憶體中，就會面臨危害整個系統的風險。 下面是保護連接字串安全的建議方法：  
  
-   使用 Windows 驗證搭配 SQL Server 資料來源。  
  
     當您使用 Windows 驗證來連接至 SQL Server 資料來源時，連接字串不會包含登入和密碼資訊。  
  
-   使用受保護的組態來加密組態檔區段。  
  
     ASP.NET 提供了一項稱為受保護組態的功能，可讓您加密組態檔中的機密資訊。 雖然主要是針對 ASP.NET 所設計，不過您也可以使用受保護的組態來加密 Windows 應用程式中組態檔的區段。 新的受保護的組態功能的詳細說明，請參閱 <<c0> [ 組態加密組態資訊使用受保護的](https://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)。  
  
-   將連接字串儲存在受保護的組態檔中。  
  
     請勿將連接字串內嵌在原始程式碼中。 您可以將連接字串儲存在組態檔中，如此就不需要將它們內嵌在應用程式的程式碼中。 根據預設，Entity Data Model 精靈會將連接字串儲存在應用程式組態檔中。 您必須保護這個檔案的安全，避免未經授權的存取。  
  
-   以動態方式建立連接時使用連接字串產生器 (Builder)。  
  
     如果您必須在執行階段建構連接字串，請使用 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 類別 (Class)。 這個字串產生器類別會透過驗證和逸出無效的輸入資訊，協助避免連接字串插入式攻擊。 如需詳細資訊，請參閱 <<c0> [ 如何： 建置 Entitycollection 連接字串](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)。 也使用適當的字串產生器類別，來建構資料來源連接字串一部分[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]連接字串。 如需 ADO.NET 提供者的連接字串產生器資訊，請參閱[連接字串產生器](../../../../../docs/framework/data/adonet/connection-string-builders.md)。  
  
 如需詳細資訊，請參閱[保護連線資訊](../../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>請勿將 EntityConnection 公開 (Expose) 給未受信任的使用者。  
 <xref:System.Data.EntityClient.EntityConnection> 物件會公開基礎連接的連接字串。 擁有 <xref:System.Data.EntityClient.EntityConnection> 物件存取權的使用者也可以變更基礎連接的 <xref:System.Data.ConnectionState>。 <xref:System.Data.EntityClient.EntityConnection> 類別不具備執行緒安全。  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>請勿在安全性內容外部傳遞連接。  
 已經建立連接之後，您就不得在安全性內容外部傳遞連接。 例如，某個具有開啟連接之權限的執行緒不應該將連接儲存在全域位置中。 如果可以在全域位置中使用此連接，則其他惡意執行緒可能會在沒有明確授與權限的情況下，使用開啟的連接。  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>請注意，登入資訊和密碼可能會顯示在記憶體傾印中。  
 當連接字串提供了資料來源的登入和密碼資訊時，這項資訊就會保留在記憶體中，直到記憶體回收作業回收了這些資源為止。 這樣做可讓人無法判斷密碼字串不再位於記憶體中的時間。 如果應用程式損毀，記憶體傾印檔可能會包含機密安全性資訊，而且執行應用程式的使用者和擁有電腦管理存取權的任何使用者都可以檢視此記憶體傾印檔。 您可以使用 Windows 驗證來連接到 Microsoft SQL Server。  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>只授與資料來源中的必要權限給使用者。  
 資料來源管理員應該只授與必要的權限給使用者。 即使 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 不支援修改資料的 DML 陳述式 (Statement) (例如 INSERT、UPDATE 或 DELETE)，使用者仍然可以存取資料來源的連接。 不過，惡意使用者可能會使用這個連接，以資料來源的原生語言執行 DML 陳述式。  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>使用最低權限來執行應用程式。  
 當您允許 Managed 應用程式以完全信任的權限執行時，[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 就不會限制應用程式對電腦的存取。 這樣做可能會讓應用程式存在安全性弱點，進而危害整個系統。 若要在 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 中使用程式碼存取安全性和其他安全性機制，您應該使用部分信任的權限以及讓應用程式正常運作所需的最低權限集合來執行應用程式。 下列程式碼存取權限是 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 應用程式所需的最低權限：  
  
-   <xref:System.Security.Permissions.FileIOPermission>：<xref:System.Security.Permissions.FileIOPermissionAccess.Write> (用以開啟指定的中繼資料檔案) 或 <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> (用以搜尋中繼資料檔案的目錄)。  
  
-   <xref:System.Security.Permissions.ReflectionPermission>：<xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (用以支援 LINQ to Entities 查詢)。  
  
-   <xref:System.Transactions.DistributedTransactionPermission>：<xref:System.Security.Permissions.PermissionState.Unrestricted> (用以在 <xref:System.Transactions><xref:System.Transactions.Transaction> 中登記)。  
  
-   <xref:System.Security.Permissions.SecurityPermission>：<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> (用以使用 <xref:System.Runtime.Serialization.ISerializable> 介面來序列化例外狀況 (Exception))。  
  
-   開啟資料庫連線，而這類執行命令，針對資料庫的權限<xref:System.Data.SqlClient.SqlClientPermission>SQL Server 資料庫。  
  
 如需詳細資訊，請參閱 [Code Access Security and ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)。  
  
#### <a name="do-not-install-untrusted-applications"></a>請勿安裝未受信任的應用程式。  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 不會強制執行任何安全性權限，而且將會以同處理序方式叫用 (Invoke) 使用者提供的資料物件程式碼，不論它是否受信任都一樣。 請確定資料存放區和應用程式都會執行用戶端的驗證與授權。  
  
#### <a name="restrict-access-to-all-configuration-files"></a>限制所有組態檔的存取權。  
 管理員必須限制指定應用程式，包括 enterprisesec.config、 security.config、 machine.conf 組態的所有檔案和應用程式組態檔的寫入權限\<*應用程式*>.exe.config。  
  
 提供者非變異名稱可在 app.config 中修改。用戶端應用程式必須負責使用強式名稱 (Strong Name) 透過標準提供者 Factory 模型存取基礎提供者。  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>限制模型和對應檔的權限。  
 管理員必須將模型和對應檔 (.edmx、.csdl、.ssdl 和 .msl) 的寫入存取權限制為只有修改模型或對應的使用者。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]只在執行階段需要這些檔案的讀取權限。 管理員也應該限制 [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] 工具所產生之物件層和預先編譯檢視原始程式碼檔的存取權。  
  
## <a name="security-considerations-for-queries"></a>查詢的安全性考量  
 查詢概念模型時適用下列安全性考量。 這些考量適用於使用 EntityClient 的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢以及使用 LINQ、[!INCLUDE[esql](../../../../../includes/esql-md.md)] 的物件，並查詢產生器方法。  
  
#### <a name="prevent-sql-injection-attacks"></a>避免 SQL 插入式攻擊。  
 應用程式經常會接受外部輸入 (來自使用者或其他外部代理程式) 以及根據該項輸入執行動作。 任何直接或間接衍生自使用者或外部代理程式的輸入都可能會具有使用目標語言語法以便執行未授權動作的內容。 當目標語言是 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 等結構化查詢語言 (SQL) 時，這種操作方式就稱為 SQL 插入式攻擊。 惡意使用者可能會將命令直接插入查詢中，並且卸除資料庫資料表、導致阻斷服務攻擊，或以其他方式變更正在執行之作業的本質。  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)] 插入式攻擊：  
  
     使用者可能會透過提供惡意輸入給查詢述詞 (Predicate) 和參數名稱所使用的值，在 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 中執行 SQL 插入式攻擊。 若要避免 SQL 插入式攻擊的風險，請勿結合使用者輸入與 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 命令文字。  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢會在可接受常值 (Literal) 的任何位置接受參數。 您應該使用參數型查詢，而非直接將外部代理程式的常值插入查詢中。 您也應該考慮使用查詢產生器方法安全地建構[Entity SQL](https://msdn.microsoft.com/library/05685434-05e6-41c2-8d5e-8933b88a40b0)。  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] 插入式攻擊：  
  
     雖然可以在 [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] 中撰寫查詢，不過這項作業實際上是透過物件模型 API 執行的。 與 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢不同的是，[!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] 查詢並非使用字串操作或串連所撰寫，而且它們不會遭受傳統 SQL 插入式攻擊的威脅。  
  
#### <a name="prevent-very-large-result-sets"></a>避免非常龐大的結果集。  
 如果用戶端正在執行耗用資源與結果集大小成正比的作業，非常龐大的結果集可能會導致用戶端系統關閉。 意外龐大的結果集可能會在下列狀況下發生：  
  
-   在針對大型資料庫而且不包含適當篩選條件的查詢中。  
  
-   在針對伺服器建立 Cartesian 聯結 (Join) 的查詢中。  
  
-   在巢狀 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢中。  
  
 接受使用者輸入時，您必須確定輸入不會導致結果集變成超過系統能夠處理的大小。 您也可以使用<xref:System.Linq.Queryable.Take%2A>方法中的[!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]或[限制](../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)中的運算子[!INCLUDE[esql](../../../../../includes/esql-md.md)]來限制結果集的大小。  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>避免在將方法公開至可能未受信任的呼叫端時傳回 IQueryable 結果。  
 基於下列原因，應避免從公開至可能未受信任之呼叫端的方法傳回 <xref:System.Linq.IQueryable%601> 類型：  
  
-   會公開 <xref:System.Linq.IQueryable%601> 類型的查詢消費者可能會針對結果呼叫方法，而該些方法會公開安全資料或增加結果集的大小。 例如，請考慮下列方法簽章：  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     此查詢的消費者可能會針對傳回的 `.Include("Orders")`呼叫 `IQueryable<Customer>` ，以擷取查詢未打算公開的資料。 將方法的傳回型別變更為 <xref:System.Collections.Generic.IEnumerable%601> 並呼叫會具體化結果的方法 (例如 `.ToList()`)，便可以避免發生此情況。  
  
-   因為 <xref:System.Linq.IQueryable%601> 查詢會在反覆查看結果時執行，所以會公開 <xref:System.Linq.IQueryable%601> 型別的查詢消費者可以攔截被擲回的例外狀況。 例外狀況可能包含消費者不適用的資訊。  
  
## <a name="security-considerations-for-entities"></a>實體的安全性考量  
 下列安全性考量會在產生和使用實體類型時適用。  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>請勿在應用程式定義域中共用 ObjectContext。  
 與多個應用程式定義域共用 <xref:System.Data.Objects.ObjectContext> 可能會公開連接字串中的資訊。 您應該改為將序列化物件或物件圖形傳輸至其他應用程式定義域，然後將這些物件附加至該應用程式定義域中的 <xref:System.Data.Objects.ObjectContext>。 如需詳細資訊，請參閱 <<c0> [ 序列化的物件](https://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99)。  
  
#### <a name="prevent-type-safety-violations"></a>避免型別安全 (Type Safety) 違規。  
 如果違反了型別安全，[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 便無法保證物件中資料的完整性。 如果您允許未受信任的應用程式使用完全信任的程式碼存取安全性來執行，可能就會發生型別安全違規。  
  
#### <a name="handle-exceptions"></a>處理例外狀況。  
 存取 try-catch 區塊內 <xref:System.Data.Objects.ObjectContext> 的方法和屬性。 攔截例外狀況可避免未處理的例外狀況將 <xref:System.Data.Objects.ObjectStateManager> 中的項目或模型資訊 (例如資料表名稱) 公開給應用程式的使用者。  
  
## <a name="security-considerations-for-aspnet-applications"></a>ASP.NET 應用程式的安全性考量  
 當您在 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] 應用程式中使用路徑時，應該考量下列事項。  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>確認主應用程式 (Host) 是否執行路徑檢查。  
 使用 `|DataDirectory|` (以垂直線符號括住) 替代字串時，[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] 會確認是否支援已解析的路徑。 例如，不允許在 `DataDirectory` 後面使用 "."。 裝載 `~` 的處理序會執行解析 Web 應用程式根目錄運算子 ([!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]) 的相同檢查。 IIS 會執行這項檢查。不過，IIS 以外的主應用程式可能不會確認是否支援已解析的路徑。 您應該了解部署 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 應用程式所在之主應用程式的行為。  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>請勿針對已解析的路徑名稱提出任何假設。  
 雖然根目錄運算子 (`~`) 和 `DataDirectory` 替代字串解析而成的值應該在應用程式的執行階段期間維持不變，但是 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 不會限制主應用程式修改這些值。  
  
#### <a name="verify-the-path-length-before-deployment"></a>在部署之前確認路徑長度。  
 部署 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 應用程式之前，您應該確認根目錄運算子 (~) 和 `DataDirectory` 替代字串的值並未超過作業系統中路徑長度的限制。 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] 資料提供者不會確定路徑長度是否在有效限制內。  
  
## <a name="security-considerations-for-adonet-metadata"></a>ADO.NET 中繼資料的安全性考量  
 下列安全性考量會在產生和使用模型與對應檔時適用。  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>請勿透過記錄公開機密資訊。  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] 中繼資料服務元件不會記錄任何私人資訊。 如果存在由於存取限制而無法傳回的結果，資料庫管理系統和檔案系統應該會傳回零筆結果，而非引發可能包含機密資訊的例外狀況。  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>請勿接受來自未受信任來源的 MetadataWorkspace 物件。  
 應用程式不應該接受來自未受信任來源之 <xref:System.Data.Metadata.Edm.MetadataWorkspace> 類別的執行個體 (Instance)。 您應該改為根據這類來源明確建構並填入工作區 (Workspace)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [部署考量](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [移轉考量](../../../../../docs/framework/data/adonet/ef/migration-considerations.md)
