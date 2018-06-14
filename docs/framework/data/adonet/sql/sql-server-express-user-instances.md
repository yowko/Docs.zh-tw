---
title: SQL Server Express 使用者執行個體
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 0af929de17a29d497ce6cf6c8cb055d416ab8761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365406"
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express 使用者執行個體
Microsoft SQL Server Express Edition (SQL Server Express) 支援使用者執行個體功能，只有在使用 .NET Framework Data Provider for SQL Server (`SqlClient`) 時才提供此功能。 使用者執行個體是 SQL Server Express Database Engine 的獨立執行個體，由父執行個體所產生。 不是系統管理員的使用者可以透過使用者執行個體，從本機電腦附加及連接至 SQL Server Express 資料庫。 每個執行個體都會依照「每個使用者一個執行個體」的基礎，在個別使用者的安全性內容下執行。  
  
## <a name="user-instance-capabilities"></a>使用者執行個體功能  
 使用者執行個體對於在最小權限使用者帳戶 (LUA) 下執行的使用者而言很有用，因為每個使用者都對在其電腦上執行的執行個體擁有 SQL Server 系統管理員 (`sysadmin`) 權限，而不需同時以 Windows 系統管理員的身分執行。 在使用者執行個體上執行但僅具有有限權限的軟體不能進行整個系統範圍的變更，因為 SQL Server Express 的執行個體是在使用者的非系統管理員 Windows 帳戶下執行，而非以服務方式執行。 每個使用者執行個體都與其父執行個體以及在相同電腦上執行的任何其他使用者執行個體隔離。 在使用者執行個體上執行的資料庫只會以單一使用者模式開啟，因此無法連接多個使用者。 使用者執行個體的複寫及分散式查詢功能也會停用。  
  
 如需詳細資訊，請參閱《SQL Server 線上叢書》的＜使用者執行個體＞。  
  
> [!NOTE]
>  對於已是自己電腦系統管理員的使用者，或在牽涉到多個資料庫使用者的案例中，就不需要使用者執行個體。  
  
## <a name="enabling-user-instances"></a>啟用使用者執行個體  
 若要產生使用者執行個體，必須有執行中的 SQL Server Express 父執行個體。 依預設會啟用使用者執行個體，SQL Server Express 安裝時，而且它們可以明確地啟用或停用系統管理員執行**sp_configure**系統預存程序與父執行個體上。  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 使用者執行個體的網路通訊協定必須為本機「具名管道」(Named Pipe)。 無法在 SQL Server 的遠端執行個體上啟動使用者執行個體，也不允許 SQL Server 登入。  
  
## <a name="connecting-to-a-user-instance"></a>連接至使用者執行個體  
 `User Instance`和`AttachDBFilename`<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>關鍵字可以讓<xref:System.Data.SqlClient.SqlConnection>連接到使用者執行個體。 使用者執行個體也受到 <xref:System.Data.SqlClient.SqlConnectionStringBuilder>`UserInstance` 和 `AttachDBFilename` 屬性的支援。  
  
 請注意下列所示的範例連接字串：  
  
-   `Data Source` 關鍵字參考到產生使用者執行個體的 SQL Server Express 父執行個體。 預設執行個體是 \sqlexpress。  
  
-   `Integrated Security` 設定為 `true`。 若要連接至使用者執行個體，必須使用「Windows 驗證」；SQL Server 登入則不受支援。  
  
-   `User Instance` 會設定為 `true`，如此會叫用 (Invoke) 使用者執行個體  (預設值為 `false`)。  
  
-   `AttachDbFileName` 連接字串關鍵字是用以附加主要資料庫檔案 (.mdf)，其中必須包括完整的路徑名稱。 `AttachDbFileName` 也會對應至 <xref:System.Data.SqlClient.SqlConnection> 連接字串中的 "extended properties" 與 "initial file name" 索引鍵。  
  
-   包含在垂直線符號中的 `|DataDirectory|` 替代字串參考到開啟連接之應用程式的資料目錄，且提供相關路徑，指出 .mdf 和 .ldf 資料庫以及記錄檔的位置。 如果想要在其他位置尋找這些檔案，則必須提供檔案的完整路徑。  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  您也可以使用<xref:System.Data.SqlClient.SqlConnectionStringBuilder><xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A>和<xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A>屬性，以建立連接字串，在執行階段。  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>使用&#124;DataDirectory&#124;替代字串  
 `AttachDbFileName` 在 ADO.NET 2.0 中已藉由引進 `|DataDirectory|` (放在垂直線符號內) 替代字串而擴充。 `DataDirectory` 可與 `AttachDbFileName` 搭配使用以表示資料檔案的相對路徑，開發人員因此能根據資料來源的相對路徑建立連接字串，而不需指定完整路徑。  
  
 `DataDirectory` 所指向的實體位置，是根據應用程式的類型而定。 在這個範例中，要附加的 Northwind.mdf 檔案是位於應用程式的 \app_data 資料夾中。  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 在使用 `DataDirectory` 時，產生的檔案路徑在目錄結構中不能高過替代字串所指向的目錄。 例如，如果完全展開的 `DataDirectory` 為 C:\AppDirectory\app_data，則可以使用上述的範例連接字串，因為它是在 c:\AppDirectory 之下。 不過，嘗試將 `DataDirectory` 指定為 `|DataDirectory|\..\data` 將會導致錯誤，因為 \data 不是 \AppDirectory 的子目錄。  
  
 如果連接字串具有格式設定錯誤的替代字串，則會顯示 <xref:System.ArgumentException>。  
  
> [!NOTE]
>  <xref:System.Data.SqlClient> 會根據本機電腦檔案系統，將替代字串解析為完整路徑。 因此，遠端伺服器、HTTP 和 UNC 路徑名稱並不受支援。 如果伺服器不位於本機電腦，則在開啟連接時會擲回例外狀況。  
  
 當 <xref:System.Data.SqlClient.SqlConnection> 開啟時，會從預設的 SQL Server Express 執行個體重新導向至在執行階段初始化，且在呼叫端帳戶下執行的執行個體。  
  
> [!NOTE]
>  可能需要增加 <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> 值可能需要增加，因為載入使用者執行個體所花費的時間可能比一般的執行個體長。  
  
 下列的程式碼片段會開啟新的 `SqlConnection`、在主控台 (Console) 視窗中顯示連接字串，然後在結束 `using` 程式碼區塊時關閉連接。  
  
```vb  
Private Sub OpenSqlConnection()  
    ' Retrieve the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Using connection As New SqlConnection(connectionString)  
        connection.Open()  
        Console.WriteLine("ConnectionString: {0}", _  
           connection.ConnectionString)  
    End Using  
End Sub  
```  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =   
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",   
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
>  在 SQL Server 內執行的 Common Language Runtime (CLR) 程式碼中不支援使用者執行個體。 如果在連接字串中有 <xref:System.InvalidOperationException> 的 `Open` 上呼叫 <xref:System.Data.SqlClient.SqlConnection>，則會擲回 `User Instance=true`。  
  
## <a name="lifetime-of-a-user-instance-connection"></a>使用者執行個體連接的存留期  
 與以服務方式執行的 SQL Server 版本不同，SQL Server Express 執行個體不需要以手動方式啟動及停止。 使用者每次登入及連接至使用者執行個體時，使用者執行個體即會啟動 (如果尚未執行)。 使用者執行個體資料庫會設定 `AutoClose` 選項，如此資料庫在一段時間未使用後，就會自動關閉。 啟動的 sqlservr.exe 處理序會在最後的執行個體連接關閉後持續執行一段有限的逾時期限，這樣如果在逾時過期之前開啟另一個連接，就不需要重新啟動此處理序。 如果在逾時期限過期之前沒有開啟任何新的連接，使用者執行個體就會自動關閉。 父執行個體上的系統管理員可以使用設定的使用者執行個體的逾時期限的持續時間**sp_configure**變更**使用者執行個體逾時**選項。 預設值是 60 分鐘。  
  
> [!NOTE]
>  如果在連接字串中使用值大於零的 `Min Pool Size`，則連接集區一定會維持一些開啟的連接，而使用者執行個體也不會自動關閉。  
  
## <a name="how-user-instances-work"></a>使用者執行個體的運作方式  
 每個使用者產生使用者執行個體第一次**主要**和**msdb**系統資料庫會從 Template Data 資料夾複製到下使用者的本機應用程式資料儲存機制的路徑專供使用者執行個體的目錄。 這個路徑通常是 `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`。 當使用者執行個體啟動時， **tempdb**、 記錄檔，以及追蹤檔案也會寫入到這個目錄。 接著執行個體的名稱就會產生，而每個使用者的名稱保證都是唯一的。  
  
 根據預設，Windows Builtin\Users group 的所有成員都將獲得本機執行個體的連接權限，以及 SQL Server 二進位檔的讀取及執行權限。 一旦確認裝載使用者執行個體的呼叫使用者認證，該使用者即可成為該執行個體的 `sysadmin`。 只能針對使用者執行個體啟用共用記憶體，這表示只能在本機電腦上進行作業。  
  
 連接字串中所指定之 .mdf 和 .ldf 檔案的讀取及寫入權限都必須授與使用者。  
  
> [!NOTE]
>  .mdf 和 .ldf 檔案分別代表資料庫及記錄檔， 這兩個檔是相對應的組合，所以在備份及還原作業時必須特別小心。 資料庫檔案包含有關記錄檔確實版本的詳細資訊，而且如果配對的記錄檔錯誤，就無法開啟資料庫。  
  
 為了避免資料毀損，使用者執行個體中的資料庫將使用獨佔存取權開啟。 如果兩個不同的使用者執行個體共用同一台電腦的相同資料庫，則第一個執行個體上的使用者必須先關閉資料庫，才能在第二個執行個體中開啟該資料庫。  
  
## <a name="user-instance-scenarios"></a>使用者執行個體案例  
 使用者執行個體為資料庫應用程式的開發人員提供 SQL Server 資料存放區，且開發人員不需擁有開發電腦的系統管理員帳戶。 使用者執行個體是以 Access/Jet 模型為基礎，在此模型中，資料庫應用程式只需連接至檔案，使用者即可自動擁有所有資料庫物件的完整權限，而不需系統管理員介入授與權限。 執行個體是針對使用者在最小權限使用者帳戶 (LUA) 下執行，且不具有伺服器或本機電腦的系統管理員權限，但又需要建立資料庫物件和應用程式的狀況而設計。 使用者執行個體可以讓使用者在執行階段建立執行個體，以在使用者本身的安全性內容下執行，而不是在權限更高的系統服務安全性內容中執行。  
  
> [!IMPORTANT]
>  適用使用者執行個體的案例，只限當所有使用它的應用程式都完全受到信任時。  
  
 使用者執行個體案例包括：  
  
-   任何不需共用資料的單一使用者應用程式。  
  
-   ClickOnce 佈署。 如果目標電腦上已安裝 .NET Framework 2.0 (或更新版本) 和 SQL Server Express，則非系統管理員的使用者也可以安裝及使用因採取 ClickOnce 動作而下載的安裝套件。 請注意，如果 SQL Server Express 是安裝的一部分，則系統管理員必須加以安裝。 如需詳細資訊，請參閱[ClickOnce 部署的 Windows Form 應用程式](http://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df)。  
  
-   使用「Windows 驗證」的專屬 ASP . NET 裝載。 單一的 SQL Server Express 執行個體可以裝載在內部網路上。 應用程式會使用 ASPNET Windows 帳戶連接，而不是使用模擬。 使用者執行個體不該用於協力廠商或共用裝載的案例，因為在這些情況下，所有的應用程式都會共用相同的使用者執行個體，而無法彼此保持隔離。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 和 ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [連接字串](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [連接至資料來源](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
