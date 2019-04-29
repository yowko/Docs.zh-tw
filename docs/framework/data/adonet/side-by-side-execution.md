---
title: ADO.NET 中的並存執行
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: a8747d749ed7e751ba577a2cd29c2048065f2645
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664138"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET 中的並存執行
在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中，並存執行是指在安裝多個 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 版本的電腦上執行應用程式 (單獨使用針對編譯該應用程式所用的版本) 的能力。 如需設定並排顯示執行的詳細資訊，請參閱[並排顯示執行](../../../../docs/framework/deployment/side-by-side-execution.md)。  
  
 使用某個 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 版本所編譯的應用程式可在不同的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 版本上執行。 但是，我們建議您最好先針對已安裝的每個 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 版本編譯應用程式版本，然後再個別執行。 不論是上述哪一種狀況，您都應該了解 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 各版本間的差異，因為它會影響應用程式的向前相容性或回溯相容性 (Backward Compatibility)。  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>向前相容性和回溯相容性  
 所謂向前相容性是指應用程式可以使用舊版的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 編譯，但仍可順利在新版的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 上執行。 針對 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 1.1 版所撰寫的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 程式碼可向前相容於更新版本。  
  
 所謂回溯相容性是指針對新版 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 所編譯的應用程式，但仍可在舊版 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 上繼續執行，而不會減損任何功能。 當然，這不適用於新版的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 所引入的功能。  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC 的 .NET Framework 資料提供者  
 從 1.1 版開始，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for ODBC (<xref:System.Data.Odbc>) 就包含在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中。 ODBC 資料提供者[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版的 Web 開發人員可以下載從[Data Access 和 Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173)。 已下載的命名空間[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]Data Provider for ODBC 會**Microsoft.Data.Odbc**。  
  
 如果您為開發的應用程式[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版使用 ODBC 資料提供者來連接至您的資料來源，而您想要執行這個應用程式[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.1 版或更新版本，您必須將 odbc 更新命名空間資料提供者**System.Data.Odbc**。 然後，您還要為新版的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 重新編譯該程式。  
  
 如果您的應用程式是針對 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 版或更新版本開發的，並且使用 ODBC 資料提供者來連接至資料來源，而您想在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版上執行這個應用程式，則必須下載 ODBC 資料提供者並將它安裝在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版的系統上。 您接著必須變更命名空間的 ODBC 資料提供者**Microsoft.Data.Odbc**，並重新編譯的應用程式[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版。  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle 的 .NET Framework 資料提供者  
 從 1.1 版開始，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle (<xref:System.Data.OracleClient>) 就包含在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中。 資料提供者[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版的 Web 開發人員可以下載從[Data Access 和 Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173)。  
  
 如果您為開發的應用程式[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]2.0 版或更新版本使用資料提供者來連接至您的資料來源，而您想要執行這個應用程式[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版中，您必須下載此資料提供者，並將它安裝在 <c4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  1.0 版的系統。  
  
## <a name="code-access-security"></a>程式碼存取安全性  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版中的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者 (<xref:System.Data.SqlClient> 和 <xref:System.Data.OleDb>) 是以 FullTrust 權限執行的必要項目。 如果您想在權限小於 FullTrust 的區域中嘗試使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者，結果就會出現 <xref:System.Security.SecurityException>。  
  
 不過，從 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 版開始，您就可以在部分信任的區域中使用所有 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者。 此外，系統會將新的安全性功能加入到 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 版的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者。 這個功能可讓您限制能在特定安全性區域中使用的連接字串。 您也可以在特定安全性地區內停用空白密碼。 如需詳細資訊，請參閱 [Code Access Security and ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)。  
  
 因為安裝的每個 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 都有個別的 Security.config 檔，所以安全性設定沒有相容性問題。 但是，如果您的應用程式有使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 1.1 (含) 以後版本所包含之 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的其他安全性功能，您就無法將應用程式散發到 1.0 版系統上。  
  
## <a name="sqlcommand-execution"></a>SqlCommand 之執行  
 從 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 版開始，<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 在資料來源執行命令的方式就已變更。  
  
 在  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>的內容中執行所有命令**sp_executesql**預存程序。 結果，凡是會影響連接狀態的命令 (例如，SET NOCOUNT ON) 只適用於目前命令的執行。 若連接已開啟，連接狀態就不會因為任何後續命令的執行而被修改。  
  
 在  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 版及更新版本，<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>只有在內容中執行命令**sp_executesql**預存程序，當命令包含參數，可提供效能優勢。 這樣的結果是，若連接已開啟，凡是會影響連接狀態的命令 (它包含於非參數化命令中) 都會修改已執行之所有後續命令的連接狀態。  
  
 請考慮使用下列在 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 呼叫中執行的命令批次。  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 (含) 以後版本中，若連接已開啟，則 NOCOUNT 對於所執行的所有後續命令都會保持為 ON。 而在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版中，NOCOUNT 只有對目前執行的命令才會是 ON。  
  
 如果您有使用任一 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 版本的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 行為，這個變更會影響應用程式的向前和回溯相容性。  
  
 若應用程式會在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的之前和以後版本上執行，則您可以撰寫程式碼來確保它在不同版本上的行為是相同的。 如果您想要確保某個命令會針對所有後續命令修改連接的狀態，我們建議您使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 來執行命令。 如果您想要確保命令不會針對所有後續命令修改連接，則我們建議您在命令中加入要重設連接狀態的命令。 例如：  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
