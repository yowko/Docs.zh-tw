---
title: 安全性考量 (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 1865afb384cfff41ede953c00f01cc96aea9a080
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854256"
---
# <a name="security-considerations-entity-framework"></a>安全性考量 (Entity Framework)
本主題說明開發、部署和執行 Entity Framework 應用程式特有的安全性考慮。 您也應該遵循建立安全 .NET Framework 應用程式的建議。 如需詳細資訊, 請參閱[安全性總覽](../security-overview.md)。  
  
## <a name="general-security-considerations"></a>一般安全性考量  
 下列安全性考慮適用于所有使用 Entity Framework 的應用程式。  
  
#### <a name="use-only-trusted-data-source-providers"></a>僅使用信任的資料來源提供者。  
 若要與資料來源通訊，提供者必須進行下列作業：  
  
- 接收來自 Entity Framework 的連接字串。  
  
- 將命令樹轉譯成資料來源的原生 (Native) 查詢語言。  
  
- 組合並傳回結果集。  
  
 進行登入作業期間，以使用者密碼為基礎的資訊會透過基礎資料來源的網路程式庫傳遞至伺服器。 惡意提供者可能會竊取使用者認證、產生惡意查詢，或竄改結果集。  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>加密您的連接以便保護機密資料。  
 Entity Framework 不會直接處理資料加密。 如果使用者透過公用 (Public) 網路存取資料，您的應用程式就應該建立資料來源的加密連接，以便提升安全性。 如需詳細資訊，請參閱資料來源的安全性相關文件。 如需 SQL Server 資料來源，請參閱[SQL Server 的加密連接](https://go.microsoft.com/fwlink/?LinkId=119544)。  
  
#### <a name="secure-the-connection-string"></a>保護連接字串的安全。  
 保護應用程式時的最重要目標之一就是保護資料來源的存取。 如果連接字串未受保護，或者建構方式不當，它就會成為可能的弱點。 如果您以純文字方式儲存連接資訊，或將它保存在記憶體中，就會面臨危害整個系統的風險。 下面是保護連接字串安全的建議方法：  
  
- 使用 Windows 驗證搭配 SQL Server 資料來源。  
  
     當您使用 Windows 驗證來連接至 SQL Server 資料來源時，連接字串不會包含登入和密碼資訊。  
  
- 使用受保護的組態來加密組態檔區段。  
  
     ASP.NET 提供了一項稱為受保護組態的功能，可讓您加密組態檔中的機密資訊。 雖然主要是針對 ASP.NET 所設計，不過您也可以使用受保護的組態來加密 Windows 應用程式中組態檔的區段。 如需新的受保護設定功能的詳細說明，請參閱[使用受保護](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))的設定來加密設定資訊。  
  
- 將連接字串儲存在受保護的組態檔中。  
  
     請勿將連接字串內嵌在原始程式碼中。 您可以將連接字串儲存在組態檔中，如此就不需要將它們內嵌在應用程式的程式碼中。 根據預設，Entity Data Model 精靈會將連接字串儲存在應用程式組態檔中。 您必須保護這個檔案的安全，避免未經授權的存取。  
  
- 以動態方式建立連接時使用連接字串產生器 (Builder)。  
  
     如果您必須在執行階段建構連接字串，請使用 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 類別 (Class)。 這個字串產生器類別會透過驗證和逸出無效的輸入資訊，協助避免連接字串插入式攻擊。 如需詳細資訊，請參閱[如何：建立 EntityConnection 連接字串](how-to-build-an-entityconnection-connection-string.md)。 也請使用適當的字串產生器類別，來建立屬於 Entity Framework 連接字串一部分的資料來源連接字串。 如需 ADO.NET 提供者之連接字串產生器的詳細資訊，請參閱[連接字串](../connection-string-builders.md)產生器。  
  
 如需詳細資訊，請參閱[保護連線資訊](../protecting-connection-information.md)。  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>請勿將 EntityConnection 公開 (Expose) 給未受信任的使用者。  
 <xref:System.Data.EntityClient.EntityConnection> 物件會公開基礎連接的連接字串。 擁有 <xref:System.Data.EntityClient.EntityConnection> 物件存取權的使用者也可以變更基礎連接的 <xref:System.Data.ConnectionState>。 <xref:System.Data.EntityClient.EntityConnection> 類別不具備執行緒安全。  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>請勿在安全性內容外部傳遞連接。  
 已經建立連接之後，您就不得在安全性內容外部傳遞連接。 例如，某個具有開啟連接之權限的執行緒不應該將連接儲存在全域位置中。 如果可以在全域位置中使用此連接，則其他惡意執行緒可能會在沒有明確授與權限的情況下，使用開啟的連接。  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>請注意，登入資訊和密碼可能會顯示在記憶體傾印中。  
 當連接字串提供了資料來源的登入和密碼資訊時，這項資訊就會保留在記憶體中，直到記憶體回收作業回收了這些資源為止。 這樣做可讓人無法判斷密碼字串不再位於記憶體中的時間。 如果應用程式損毀，記憶體傾印檔可能會包含機密安全性資訊，而且執行應用程式的使用者和擁有電腦管理存取權的任何使用者都可以檢視此記憶體傾印檔。 您可以使用 Windows 驗證來連接到 Microsoft SQL Server。  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>只授與資料來源中的必要權限給使用者。  
 資料來源管理員應該只授與必要的權限給使用者。 即使 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 不支援修改資料的 DML 陳述式 (Statement) (例如 INSERT、UPDATE 或 DELETE)，使用者仍然可以存取資料來源的連接。 不過，惡意使用者可能會使用這個連接，以資料來源的原生語言執行 DML 陳述式。  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>使用最低權限來執行應用程式。  
 當您允許受控應用程式以完全信任許可權執行時，.NET Framework 不會限制應用程式對您電腦的存取權。 這樣做可能會讓應用程式存在安全性弱點，進而危害整個系統。 若要在 .NET Framework 中使用代碼啟用安全性和其他安全性機制，您應該使用部分信任許可權，以及讓應用程式正常運作所需的最小許可權集來執行應用程式。 下列代碼存取權限是 Entity Framework 應用程式所需的最小許可權：  
  
- <xref:System.Security.Permissions.FileIOPermission>：<xref:System.Security.Permissions.FileIOPermissionAccess.Write> (用以開啟指定的中繼資料檔案) 或 <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> (用以搜尋中繼資料檔案的目錄)。  
  
- <xref:System.Security.Permissions.ReflectionPermission>：<xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (用以支援 LINQ to Entities 查詢)。  
  
- <xref:System.Transactions.DistributedTransactionPermission>：<xref:System.Security.Permissions.PermissionState.Unrestricted> (用以在 <xref:System.Transactions><xref:System.Transactions.Transaction> 中登記)。  
  
- <xref:System.Security.Permissions.SecurityPermission>：<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> (用以使用 <xref:System.Runtime.Serialization.ISerializable> 介面來序列化例外狀況 (Exception))。  
  
- 開啟資料庫連接以及對資料庫執行命令<xref:System.Data.SqlClient.SqlClientPermission>的許可權，例如 SQL Server 資料庫。  
  
 如需詳細資訊，請參閱 [Code Access Security and ADO.NET](../code-access-security.md)。  
  
#### <a name="do-not-install-untrusted-applications"></a>請勿安裝未受信任的應用程式。  
 Entity Framework 不會強制執行任何安全性許可權，而且將會叫用進程中任何使用者提供的資料物件程式碼，不論其是否受信任。 請確定資料存放區和應用程式都會執行用戶端的驗證與授權。  
  
#### <a name="restrict-access-to-all-configuration-files"></a>限制所有組態檔的存取權。  
 系統管理員必須限制指定應用程式之設定的所有檔案的寫入存取權，包括 enterprisesec .config、security .config、machine.config 和應用程式佈建檔\<案*應用*程式 >。config.xml。  
  
 提供者非變異名稱可在 app.config 中修改。用戶端應用程式必須負責使用強式名稱 (Strong Name) 透過標準提供者 Factory 模型存取基礎提供者。  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>限制模型和對應檔的權限。  
 管理員必須將模型和對應檔 (.edmx、.csdl、.ssdl 和 .msl) 的寫入存取權限制為只有修改模型或對應的使用者。 Entity Framework 只需要在執行時間讀取這些檔案的許可權。 系統管理員也應該限制存取由實體資料模型工具產生的物件層和預先編譯的視圖原始程式碼檔。  
  
## <a name="security-considerations-for-queries"></a>查詢的安全性考量  
 查詢概念模型時適用下列安全性考量。 這些考量適用於使用 EntityClient 的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢以及使用 LINQ、[!INCLUDE[esql](../../../../../includes/esql-md.md)] 的物件，並查詢產生器方法。  
  
#### <a name="prevent-sql-injection-attacks"></a>避免 SQL 插入式攻擊。  
 應用程式經常會接受外部輸入 (來自使用者或其他外部代理程式) 以及根據該項輸入執行動作。 任何直接或間接衍生自使用者或外部代理程式的輸入都可能會具有使用目標語言語法以便執行未授權動作的內容。 當目的語言是結構化查詢語言 (SQL) （SQL）（例如 Transact-sql）時，這種操作就稱為 SQL 插入式攻擊。 惡意使用者可能會將命令直接插入查詢中，並且卸除資料庫資料表、導致阻斷服務攻擊，或以其他方式變更正在執行之作業的本質。  
  
- [!INCLUDE[esql](../../../../../includes/esql-md.md)] 插入式攻擊：  
  
     使用者可能會透過提供惡意輸入給查詢述詞 (Predicate) 和參數名稱所使用的值，在 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 中執行 SQL 插入式攻擊。 若要避免 SQL 插入式攻擊的風險，請勿結合使用者輸入與 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 命令文字。  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢會在可接受常值 (Literal) 的任何位置接受參數。 您應該使用參數型查詢，而非直接將外部代理程式的常值插入查詢中。 您也應該考慮使用[查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896238(v=vs.100))產生器方法，安全地建立 Entity SQL。  
  
- LINQ to Entities 的插入式攻擊：  
  
     雖然可以在 LINQ to Entities 中撰寫查詢，但它是透過物件模型 API 來執行。 不同[!INCLUDE[esql](../../../../../includes/esql-md.md)]于查詢，LINQ to Entities 查詢不是使用字串操作或串連所撰寫，而且它們不會受到傳統 SQL 插入式攻擊的影響。  
  
#### <a name="prevent-very-large-result-sets"></a>避免非常龐大的結果集。  
 如果用戶端正在執行耗用資源與結果集大小成正比的作業，非常龐大的結果集可能會導致用戶端系統關閉。 意外龐大的結果集可能會在下列狀況下發生：  
  
- 在針對大型資料庫而且不包含適當篩選條件的查詢中。  
  
- 在針對伺服器建立 Cartesian 聯結 (Join) 的查詢中。  
  
- 在巢狀 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢中。  
  
 接受使用者輸入時，您必須確定輸入不會導致結果集變成超過系統能夠處理的大小。 您也可以使用 LINQ to Entities <xref:System.Linq.Queryable.Take%2A>中的方法或中 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 的 [LIMIT](./language-reference/limit-entity-sql.md) 運算子，以限制結果集的大小。  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>避免在將方法公開至可能未受信任的呼叫端時傳回 IQueryable 結果。  
 基於下列原因，應避免從公開至可能未受信任之呼叫端的方法傳回 <xref:System.Linq.IQueryable%601> 類型：  
  
- 會公開 <xref:System.Linq.IQueryable%601> 類型的查詢消費者可能會針對結果呼叫方法，而該些方法會公開安全資料或增加結果集的大小。 例如，請考慮下列方法簽章：  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     此查詢的消費者可能會針對傳回的 `.Include("Orders")`呼叫 `IQueryable<Customer>` ，以擷取查詢未打算公開的資料。 將方法的傳回型別變更為 <xref:System.Collections.Generic.IEnumerable%601> 並呼叫會具體化結果的方法 (例如 `.ToList()`)，便可以避免發生此情況。  
  
- 因為 <xref:System.Linq.IQueryable%601> 查詢會在反覆查看結果時執行，所以會公開 <xref:System.Linq.IQueryable%601> 型別的查詢消費者可以攔截被擲回的例外狀況。 例外狀況可能包含消費者不適用的資訊。  
  
## <a name="security-considerations-for-entities"></a>實體的安全性考量  
 下列安全性考量會在產生和使用實體類型時適用。  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>請勿在應用程式定義域中共用 ObjectContext。  
 與多個應用程式定義域共用 <xref:System.Data.Objects.ObjectContext> 可能會公開連接字串中的資訊。 您應該改為將序列化物件或物件圖形傳輸至其他應用程式定義域，然後將這些物件附加至該應用程式定義域中的 <xref:System.Data.Objects.ObjectContext>。 如需詳細資訊，請參閱序列化[物件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100))。  
  
#### <a name="prevent-type-safety-violations"></a>避免型別安全 (Type Safety) 違規。  
 如果違反型別安全，Entity Framework 就無法保證物件中資料的完整性。 如果您允許未受信任的應用程式使用完全信任的程式碼存取安全性來執行，可能就會發生型別安全違規。  
  
#### <a name="handle-exceptions"></a>處理例外狀況。  
 存取 try-catch 區塊內 <xref:System.Data.Objects.ObjectContext> 的方法和屬性。 攔截例外狀況可避免未處理的例外狀況將 <xref:System.Data.Objects.ObjectStateManager> 中的項目或模型資訊 (例如資料表名稱) 公開給應用程式的使用者。  
  
## <a name="security-considerations-for-aspnet-applications"></a>ASP.NET 應用程式的安全性考量  

當您使用 ASP.NET 應用程式中的路徑時，應該考慮下列各項。  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>確認主應用程式 (Host) 是否執行路徑檢查。  
 當使用`|DataDirectory|` （以分隔號符號括住）替代字串時，ADO.NET 會確認是否支援已解析的路徑。 例如，不允許在 `DataDirectory` 後面使用 ".."。 解析 Web 應用程式根運算子（`~`）的相同檢查是由裝載 ASP.NET 的進程所執行。 IIS 會執行這項檢查。不過，IIS 以外的主應用程式可能不會確認是否支援已解析的路徑。 您應該知道部署 Entity Framework 應用程式之主機的行為。  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>請勿針對已解析的路徑名稱提出任何假設。  
 雖然根運算子（`~`） `DataDirectory`和替代字串解析的值應該在應用程式的執行時間期間保持不變，但 Entity Framework 不會限制主機修改這些值。  
  
#### <a name="verify-the-path-length-before-deployment"></a>在部署之前確認路徑長度。  
 部署 Entity Framework 應用程式之前，您應該確定根運算子（~）和`DataDirectory`替代字串的值不會超過作業系統中路徑長度的限制。 ADO.NET 資料提供者不會確定路徑長度是否在有效的限制範圍內。  
  
## <a name="security-considerations-for-adonet-metadata"></a>ADO.NET 中繼資料的安全性考量  
 下列安全性考量會在產生和使用模型與對應檔時適用。  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>請勿透過記錄公開機密資訊。  
ADO.NET 中繼資料服務元件不會記錄任何私用資訊。 如果存在由於存取限制而無法傳回的結果，資料庫管理系統和檔案系統應該會傳回零筆結果，而非引發可能包含機密資訊的例外狀況。  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>請勿接受來自未受信任來源的 MetadataWorkspace 物件。  
 應用程式不應該接受來自未受信任來源之 <xref:System.Data.Metadata.Edm.MetadataWorkspace> 類別的執行個體 (Instance)。 您應該改為根據這類來源明確建構並填入工作區 (Workspace)。  
  
## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../securing-ado-net-applications.md)
- [部署考量](deployment-considerations.md)
- [移轉考量](migration-considerations.md)
