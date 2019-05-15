---
title: ADO.NET 中的並存執行
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 377af3c72b0a9a8eb26c8713d98f114803f08356
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583615"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET 中的並存執行
並排顯示執行.NET Framework 中的是有多個版本的.NET Framework 安裝，以獨佔方式使用的已編譯的應用程式版本的電腦上執行應用程式的能力。 如需設定並排顯示執行的詳細資訊，請參閱[並排顯示執行](../../../../docs/framework/deployment/side-by-side-execution.md)。  
  
 藉由使用一種.NET Framework 版本所編譯的應用程式可以執行不同版本的.NET framework。 不過，我們建議您編譯的.NET Framework 中，每個已安裝版本的應用程式的版本，然後再個別執行。 不論是上述哪一種狀況，您都應該了解 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 各版本間的差異，因為它會影響應用程式的向前相容性或回溯相容性 (Backward Compatibility)。  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>向前相容性和回溯相容性  
 正向相容性是指應用程式可以使用舊版.NET Framework 中，進行編譯，但仍會在更新的.NET framework 版本上順利執行。 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 針對.NET Framework 1.1 版所撰寫的程式碼是向前相容於更新版本。  
  
 回溯相容性表示應用程式針對較新版的.NET Framework 中，編譯，但仍會繼續執行舊版的.NET Framework 不會遺失任何的功能。 當然，這不是所引進的新版本的.NET framework 功能的情況。  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC 的 .NET Framework 資料提供者  
 從版本 1.1 中，.NET Framework Data Provider for ODBC (<xref:System.Data.Odbc>) 就會包含.NET Framework 的一部分。 ODBC 資料提供者的.NET Framework 1.0 版開發人員從 Web 下載[Data Access 和 Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173)。 下載.NET Framework Data Provider for ODBC 的命名空間是**Microsoft.Data.Odbc**。  
  
 如果您有適用於.NET Framework 1.0 版來連接到資料來源時，使用 ODBC 資料提供者所開發的應用程式，而且您想要在.NET Framework 1.1 版或更新版本上執行該應用程式，您必須更新 ODBC dat 的命名空間提供者**System.Data.Odbc**。 您接著必須重新編譯它較新版本的.NET Framework。  
  
 如果您有適用於使用 ODBC 資料提供者來連接到資料來源時，.NET Framework 2.0 版或更新版本開發的應用程式，而且您想要在.NET Framework 1.0 版上執行該應用程式，您必須下載 ODBC 資料提供者，並將它安裝在.NET Framework 1.0 版的系統。 您接著必須變更命名空間的 ODBC 資料提供者**Microsoft.Data.Odbc**，並重新編譯.NET Framework 1.0 版的應用程式。  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle 的 .NET Framework 資料提供者  
 從版本 1.1 中，.NET Framework Data Provider for Oracle (<xref:System.Data.OracleClient>) 就會包含.NET Framework 的一部分。 資料提供者的.NET Framework 1.0 版開發人員從 Web 下載[Data Access 和 Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173)。  
  
 如果您有連接到資料來源時，會使用此資料提供者的.NET framework 2.0 版或更新版本開發的應用程式，而且您想要在.NET Framework 1.0 版上執行該應用程式，您必須下載此資料提供者，並將它安裝在.NET Framework 1.0 版的系統。  
  
## <a name="code-access-security"></a>程式碼存取安全性  
 在.NET Framework 1.0 版的.NET Framework 資料提供者 (<xref:System.Data.SqlClient>， <xref:System.Data.OleDb>)，才能執行以 FullTrust 權限。 嘗試使用小於 FullTrust 權限的原因與區域中的.NET Framework 資料提供者從.NET Framework 1.0 版<xref:System.Security.SecurityException>。  
  
 不過，從.NET Framework 2.0 版開始，所有.NET Framework 資料提供者可以用於部分信任的區域。 此外，新的安全性功能已加入.NET Framework 1.1 版中的.NET Framework 資料提供者。 這個功能可讓您限制能在特定安全性區域中使用的連接字串。 您也可以在特定安全性地區內停用空白密碼。 如需詳細資訊，請參閱 [Code Access Security and ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)。  
  
 每個安裝的.NET framework 有個別的 Security.config 檔，因為有安全性設定沒有相容性問題。 不過，如果您的應用程式取決於額外的安全性功能的[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]包含.NET Framework 1.1 和更新版本中，您將無法將它散發給 1.0 版的系統。  
  
## <a name="sqlcommand-execution"></a>SqlCommand 之執行  
 從.NET Framework 1.1 版的方式開始，<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>執行命令，在資料來源已變更。  
  
 在.NET Framework 1.0 版<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>的內容中執行所有命令**sp_executesql**預存程序。 結果，凡是會影響連接狀態的命令 (例如，SET NOCOUNT ON) 只適用於目前命令的執行。 若連接已開啟，連接狀態就不會因為任何後續命令的執行而被修改。  
  
 在.NET Framework 1.1 版及更新版本<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>只有在內容中執行命令**sp_executesql**預存程序，當命令包含參數，可提供效能優勢。 這樣的結果是，若連接已開啟，凡是會影響連接狀態的命令 (它包含於非參數化命令中) 都會修改已執行之所有後續命令的連接狀態。  
  
 請考慮使用下列在 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 呼叫中執行的命令批次。  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 在.NET Framework 1.1 和更新版本中，NOCOUNT 會保持開啟狀態的任何後續的命令執行時，連接已開啟。 在.NET Framework 1.0 版中，NOCOUNT 是只有 ON 目前執行的命令。  
  
 這項變更可能會影響您的應用程式的向前及向後相容，如果您依賴的行為<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>任一版本的.NET framework。  
  
 在之前和以後版本的.NET framework 上執行的應用程式，您可以撰寫您的程式碼，並確定行為是不論您在執行的版本相同。 如果您想要確保某個命令會針對所有後續命令修改連接的狀態，我們建議您使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 來執行命令。 如果您想要確保命令不會針對所有後續命令修改連接，則我們建議您在命令中加入要重設連接狀態的命令。 例如：  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
