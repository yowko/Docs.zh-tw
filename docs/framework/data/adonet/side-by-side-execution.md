---
title: ADO.NET 中的並存執行
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 0ada258f74338fc7cbc9435fdea8fc896bd2efd6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782706"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET 中的並存執行
.NET Framework 中的並存執行是在已安裝多個版本之 .NET Framework 的電腦上執行應用程式的能力，以獨佔方式使用已編譯應用程式的版本。 如需設定並存執行的詳細資訊，請參閱[並存執行](../../deployment/side-by-side-execution.md)。  
  
 使用其中一個版本的 .NET Framework 所編譯的應用程式，可以在不同版本的 .NET Framework 上執行。 不過，我們建議您針對每個已安裝的 .NET Framework 版本編譯應用程式的版本，並分別執行它們。 在任一情況下，您都應該留意可能會影響應用程式向前相容性或回溯相容性的版本之間的 ADO.NET 變更。  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>向前相容性和回溯相容性  
 向前相容性表示可以使用舊版的 .NET Framework 來編譯應用程式，但仍可在較新版本的 .NET Framework 上順利執行。 針對 .NET Framework 1.1 版所撰寫的 ADO.NET 程式碼會向前相容于較新的版本。  
  
 回溯相容性表示會針對較新版本的 .NET Framework 編譯應用程式，但會繼續在舊版的 .NET Framework 上執行，而不會遺失任何功能。 當然，新版本的 .NET Framework 中引進的功能並不是這種情況。  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC 的 .NET Framework 資料提供者  
 從1.1 版開始，ODBC （<xref:System.Data.Odbc>）的 .NET Framework Data Provider 會包含為 .NET Framework 的一部分。 ODBC 資料提供者可從[資料存取和儲存開發人員中心](https://go.microsoft.com/fwlink/?linkid=4173)，.NET Framework 版本1.0 開發人員做為 Web 下載。 針對 ODBC 下載的 .NET Framework Data Provider 的命名空間是**Microsoft. Data. odbc**。  
  
 如果您的應用程式是針對使用 ODBC 資料提供者連接到資料來源的 .NET Framework 1.0 版所開發，而您想要在 .NET Framework 版本1.1 或更新版本上執行該應用程式，您必須更新 ODBC dat 的命名空間**system.object**的提供者。 接著，您必須針對較新版本的 .NET Framework 重新編譯它。  
  
 如果您的應用程式是針對使用 ODBC 資料提供者連接至資料來源的 .NET Framework 2.0 版或更新版本所開發，而您想要在 .NET Framework 1.0 版上執行該應用程式，則必須下載 ODBC 資料提供者並加以安裝在 .NET Framework 版本1.0 系統上。 接著，您必須將 ODBC 資料提供者的命名空間變更為**Microsoft. data**，然後重新編譯應用程式，以取得 .NET Framework 版本1.0。  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle 的 .NET Framework 資料提供者  
 從1.1 版開始，Oracle （<xref:System.Data.OracleClient>）的 .NET Framework Data Provider 會納入做為 .NET Framework 的一部分。 資料提供者可從[資料存取和儲存開發人員中心](https://go.microsoft.com/fwlink/?linkid=4173)，.NET Framework 版本1.0 開發人員做為 Web 下載。  
  
 如果您的應用程式是針對使用資料提供者連接至資料來源的 .NET Framework 2.0 版或更新版本所開發，而您想要在 .NET Framework 1.0 版上執行該應用程式，則必須下載資料提供者，並將它安裝在 NE 上T Framework 版本1.0 系統。  
  
## <a name="code-access-security"></a>程式碼存取安全性  
 .NET Framework 1.0 版（<xref:System.Data.SqlClient>， <xref:System.Data.OleDb>）中的 .NET Framework 資料提供者必須以 FullTrust 許可權執行。 嘗試在許可權低於 FullTrust 的區域中，使用來自 .NET Framework 1.0 版的 .NET Framework k 資料提供者，會導致<xref:System.Security.SecurityException>。  
  
 不過，從 .NET Framework 版本2.0 開始，所有 .NET Framework 資料提供者都可以在部分信任的區域中使用。 此外，新的安全性功能已新增至 .NET Framework 版本1.1 中的 .NET Framework 資料提供者。 這個功能可讓您限制能在特定安全性區域中使用的連接字串。 您也可以在特定安全性地區內停用空白密碼。 如需詳細資訊，請參閱 [Code Access Security and ADO.NET](code-access-security.md)。  
  
 因為 .NET Framework 的每個安裝都有個別的安全性設定檔，所以安全性設定沒有任何相容性問題。 不過，如果您的應用程式相依于 .NET Framework 1.1 版和更新版本中所包含的其他 ADO.NET 安全性功能，您將無法將它散發至1.0 版系統。  
  
## <a name="sqlcommand-execution"></a>SqlCommand 之執行  
 從 .NET Framework 版本1.1 開始，在資料來源<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>執行命令的方式已變更。  
  
 在 .NET Framework 版本1.0 中， <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>會在**sp_executesql**預存程式的內容中執行所有命令。 結果，凡是會影響連接狀態的命令 (例如，SET NOCOUNT ON) 只適用於目前命令的執行。 若連接已開啟，連接狀態就不會因為任何後續命令的執行而被修改。  
  
 在 .NET Framework 1.1 版和更新版本中<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> ，只有當命令包含參數時，才會在**sp_executesql**預存程式的內容中執行命令，以提供效能優勢。 這樣的結果是，若連接已開啟，凡是會影響連接狀態的命令 (它包含於非參數化命令中) 都會修改已執行之所有後續命令的連接狀態。  
  
 請考慮使用下列在 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 呼叫中執行的命令批次。  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 在 .NET Framework 1.1 版和更新版本中，在開啟連接時，NOCOUNT 將會針對任何後續執行的命令維持開啟狀態。 在 .NET Framework 版本1.0 中，NOCOUNT 只會在目前命令執行的上開啟。  
  
 這項變更可能會影響應用程式的向前和回溯相容性（如果您相依于任一<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>版本的 .NET Framework 的行為）。  
  
 對於在舊版和更新版本的 .NET Framework 上執行的應用程式，您可以撰寫程式碼，以確保不論您執行的版本為何，行為都相同。 如果您想要確保某個命令會針對所有後續命令修改連接的狀態，我們建議您使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 來執行命令。 如果您想要確保命令不會針對所有後續命令修改連接，則我們建議您在命令中加入要重設連接狀態的命令。 例如：  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](ado-net-overview.md)
- [在 ADO.NET 中擷取和修改資料](retrieving-and-modifying-data.md)
