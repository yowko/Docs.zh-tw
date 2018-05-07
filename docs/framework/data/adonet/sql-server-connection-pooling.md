---
title: SQL Server 連接共用 (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 78e852e2f1894f92e5b43228faedfad0d78981fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sql-server-connection-pooling-adonet"></a>SQL Server 連接共用 (ADO.NET)
連接到資料庫伺服器通常需要執行幾個很費時的步驟。 必須要建立實體頻道 (如通訊端或具名管道)，必須建立與伺服器的初始信號交換、必須剖析連接字串資訊、伺服器必須要驗證連接，以及必須檢查是否已在現行交易中登記等。  
  
 實際上，大部分應用程式僅使用一個或幾個不同的連接組態。 這表示應用程式執行期間，將會重複開啟及關閉許多相同的連接。 若要開啟連接的成本降至最低[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]使用呼叫的最佳化技術*連接共用*。  
  
 連接共用可減少開啟新連接的必要次數。 *共用器*維護實體連接的擁有權。 它藉由讓每個指定連接組態的作用中連接集保持運行狀態，來管理連接。 只要使用者針對連接呼叫 `Open`，共用器便會查看集區中是否有可用的連接。 如果共用的連接可用，則共用器會將其傳回至呼叫端，而不會開啟新的連接。 應用程式針對連接呼叫 `Close` 時，共用器會將其傳回至共用的作用中連接集，而不會真正關閉它。 連接一旦傳回至集區，便已備妥在下一次 `Open` 呼叫中重複使用。  
  
 只能共用具有相同組態的連接。 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 會同時保持數個集區，每個組態一個集區。 使用整合安全性時，會按連接字串及 Windows 識別將連接分成多個集區。 連接也會根據是否登記於交易中而進行共用。 當使用 <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A> 時，<xref:System.Data.SqlClient.SqlCredential> 執行個體會影響連線集區。 即使使用者 ID 和密碼相同，不同的 <xref:System.Data.SqlClient.SqlCredential> 執行個體仍將使用不同的連線集區。  
  
 共用連接可顯著提高應用程式的效能及延展性。 依預設，[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中的連接共用是啟用的。 除非您明確停用，否則在應用程式中開啟及關閉連接時，共用器會對連接進行最佳化。 您也可提供幾個連接字串修飾詞，以控制連接共用行為。 如需詳細資訊，請參閱本章稍後的＜使用連接字串關鍵字控制連接共用＞。  
  
> [!NOTE]
>  啟用連線集區時，若發生逾時錯誤或其他登入錯誤，就會擲回例外狀況，且在接下來五秒的「封鎖期間」內，後續連接嘗試都會失敗。 如果應用程式嘗試在封鎖期間內連接，將再次擲回第一個例外狀況。 封鎖期間結束後若仍失敗，會造成新的封鎖期間，且時間為前一次封鎖期間的兩倍，最長一分鐘。  
  
## <a name="pool-creation-and-assignment"></a>集區的建立及指派  
 第一次開啟連接時，會根據精確的比對演算法建立連接集區，該演算法可將集區與連接中的連接字串相關聯。 每個連接集區與不同的連接字串相關聯。 開啟新連接時，如果連接字串與現有集區並不完全相符，則會建立新集區。 連接共用的方式是以每個處理序、每個應用程式定義域、每個連接字串，及 (使用整合安全性時) 每個 Windows 識別進行的。 連接字串必須完全符合；以不同順序針對同一連接所提供的關鍵字將會個別共用。  
  
 在下列 C# 範例中，會建立三個新的 <xref:System.Data.SqlClient.SqlConnection> 物件，但是只需要兩個連接集區來管理它們。 請注意，第一個及第二個連接字串的不同之處在於指派給 `Initial Catalog` 的值不同。  
  
```  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // Pool A is created.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=pubs"))  
    {  
        connection.Open();        
        // Pool B is created because the connection strings differ.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // The connection string matches pool A.  
    }  
```  
  
 如果連接字串中未指定 `MinPoolSize` 或其指定為零，則會在一段非作用中期間後關閉集區中的連接。 不過，如果指定的 `MinPoolSize` 大於零，則在卸載 `AppDomain` 且處理序結束之前，不會損毀連接集區。 維護非作用中或空的集區僅會導致最小的系統負荷量。  
  
> [!NOTE]
>  發生嚴重錯誤 (如容錯移轉) 時，會自動清除集區。  
  
## <a name="adding-connections"></a>加入連接  
 針對每個唯一連接字串可建立連接集區。 建立集區時，會建立多個連接物件並加入集區，以滿足最小集區大小需求。 視需要將連接加入集區，直到達到指定的最大集區大小 (預設值是 100)。 連接關閉或處置時，會被釋放回集區。  
  
 要求 <xref:System.Data.SqlClient.SqlConnection> 物件時，如果存在可用的連接，則會從集區取得該物件。 若要連接可用，則連接必須未使用、具有相符的交易內容或不與任何交易內容關聯，並具有到伺服器的有效連結。  
  
 連接共用器會藉由重新配置釋放回集區的連接，來滿足連接的請求。 如果已達到最大集區大小，但仍沒有可用的連接，則會將要求排入佇列。 共用器接下來會嘗試回收所有連接，直到達到逾時 (預設值是 15 秒)。 如果連接逾時之前共用器無法滿足要求，則會擲回例外狀況。  
  
> [!CAUTION]
>  強烈建議您在使用完連接後一律關閉該連接，以便將連接傳回集區。 您可以使用`Close`或`Dispose`方法`Connection`物件，或藉由開啟內的所有連線`using`C# 中的陳述式或`Using`在 Visual Basic 中的陳述式。 可能不會將未明確關閉的連接加入或傳回集區。 如需詳細資訊，請參閱[使用陳述式](~/docs/csharp/language-reference/keywords/using-statement.md)或[如何： 處置系統資源](~/docs/visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)適用於 Visual Basic。  
  
> [!NOTE]
>  請不要在您類別之 `Close` 方法中的 `Dispose`、`Connection` 或任何其他 Managed 物件上呼叫 `DataReader` 或 `Finalize`。 在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。 如果類別未擁有任何 Unmanaged 資源，請不要在類別定義中包含 `Finalize` 方法。 如需詳細資訊，請參閱[回收](../../../../docs/standard/garbage-collection/index.md)。  
  
> [!NOTE]
>  從連接集區中擷取連接或將連接傳回連接集區時，系統不會在伺服器上引發登入和登出事件。 這是因為當連接傳回連接集區時，連接實際上並未關閉。 如需詳細資訊，請參閱[Audit Login Event Class](http://msdn2.microsoft.com/library/ms190260.aspx)和[Logout Event Class<](http://msdn2.microsoft.com/library/ms175827.aspx) SQL Server 線上叢書 》 中。  
  
## <a name="removing-connections"></a>移除連接  
 如果集區中的連接已閒置大約 4 到 8 分鐘，或如果共用器偵測到與伺服器的連接已嚴重損毀，則連接共用器會從集區中移除該連接。 請注意，只有嘗試與伺服器進行通訊後，才能偵測到嚴重損毀的連接。 如果發現連接已不再連接到伺服器，則會將其標記為無效。 只當關閉或回收無效的連接時，才會將它們從連接集區中移除。  
  
 如果連接是與已消失的伺服器連接，即使連接共用器尚未偵測到已嚴重損毀的連接並將其標記為無效，此連接還是會從集區中建立。 這是因為檢查連接是否仍然有效的額外負荷抵銷了集區的優點，它導致了與伺服器之間的往返通訊。 發生此情況時，第一次嘗試使用該連接時將偵測到連接已嚴重損毀，並擲回例外狀況。  
  
## <a name="clearing-the-pool"></a>清除集區  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 引進兩種清除集區的新方法：<xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> 和 <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>。 `ClearAllPools` 會清除指定提供者的連接集區， `ClearPool` 會清除與特定連接相關聯的連接集區。 如果呼叫時有正在使用中的連接，則會適當地標記它們。 而當連接關閉時，會捨棄它們，而不是將其傳回集區。  
  
## <a name="transaction-support"></a>異動支援  
 從集區中描繪連接，並根據交易內容進行指派。 除非已在連接字串中指定 `Enlist=false`，否則連接集區會確保將連接登記在 <xref:System.Transactions.Transaction.Current%2A>內容中。 連接關閉並傳回到具有已登記 `System.Transactions` 交易的集區時會先擱置。如果下一個要求發出時此連接是可用狀態，具有相同 `System.Transactions` 交易之連接集區就會傳回相同的連接。 如果這類要求發出，但沒有可用的共用連接，則會從集區的非交易部分建立連接並登記。 如果共用的連接可用，則共用器會將其傳回至呼叫端，而不會開啟新的連接。  
  
 連接關閉時，會根據其交易內容將其釋放回集區，並置於適當的子區塊中。 因此，即使分散式交易仍處於暫止狀態，您仍可以關閉連接，而不會產生錯誤。 這可讓您稍後再認可或中止分散式交易。  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>使用連接字串關鍵字控制連接共用  
 `ConnectionString` 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性支援連接字串索引鍵/值配對，這些配對可用於調整連接共用邏輯的行為。 如需詳細資訊，請參閱<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。  
  
## <a name="pool-fragmentation"></a>集區片段  
 集區片段是許多 Web 應用程式中的常見問題，這些應用程式可能會建立大量集區，並且直至處理序結束後才釋放它們。 這會使大量連接保持開啟狀態並消耗記憶體，導致效能降低。  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>整合安全性導致的集區片段  
 可根據連接字串及使用者識別共用連接。 因此，如果您在網站上使用基本驗證或 Windows 驗證，並使用整合安全性登入，則每個使用者會獲得一個集區。 雖然這會提升單一使用者之後續資料庫要求的效能，但該使用者無法利用其他使用者的連接。 這也會導致每個使用者至少存在一個與資料庫伺服器的連接。 這是特定 Web 應用程式架構的副作用，是開發人員在針對安全性與稽核需求方面必須考量的問題。  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>多個資料庫導致的集區片段  
 許多網際網路服務提供者在單一伺服器上裝載多個網站。 他們可以使用單一資料庫確認表單驗證登入，然後開啟該使用者或使用者群組之特定資料庫的連接。 驗證資料庫的連接可供所有人共用和使用。 不過，每個資料庫存在單獨的連接集區，而這會增加伺服器連接的數目。  
  
 這也是應用程式設計的副作用。 有一個比較簡單的方法可避免此副作用，同時不會影響連接到 SQL Server 時的安全性。 連接到伺服器上的同一個資料庫 (而不是連接到每個使用者或群組的個別資料庫)，然後執行 [!INCLUDE[tsql](../../../../includes/tsql-md.md)] USE 陳述式，以變更為想要的資料庫。 下列程式碼片段會示範如何建立與 `master` 資料庫的初始連接，然後切換至 `databaseName` 字串變數中指定之目標資料庫。  
  
```vb  
' Assumes that command is a valid SqlCommand object and that  
' connectionString connects to master.  
    command.Text = "USE DatabaseName"  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
// Assumes that command is a SqlCommand object and that  
// connectionString connects to master.  
command.Text = "USE DatabaseName";  
using (SqlConnection connection = new SqlConnection(  
  connectionString))  
  {  
    connection.Open();  
    command.ExecuteNonQuery();  
  }  
```  
  
## <a name="application-roles-and-connection-pooling"></a>應用程式角色和連接共用  
 呼叫 `sp_setapprole` 系統預存程序來啟動 SQL Server 應用程式角色後，便無法重設該連接的安全性內容。 不過，啟用共用後，連接會傳回到集區，並且在重複使用共用連接時發生錯誤。 如需詳細資訊，請參閱知識庫文件中，「[SQL 應用程式角色錯誤 OLE DB 資源共用](http://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)。 」  
  
### <a name="application-role-alternatives"></a>應用程式角色替代方案  
 建議您善加利用安全機制，以取代應用程式角色。 如需詳細資訊，請參閱[SQL Server 中建立應用程式角色](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [連接共用](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [SQL Server 和 ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [效能計數器](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
