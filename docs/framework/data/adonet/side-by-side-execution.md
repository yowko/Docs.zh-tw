---
title: 並存執行
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 609fc7b7cefd92e38ecfff54e5ac1651e855e4b7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188934"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET 中的並存執行

.NET Framework 中並存執行的能力，是能夠在已安裝多個版本 .NET Framework 的電腦上執行應用程式，以獨佔方式使用已編譯應用程式的版本。 如需有關設定並存執行的詳細資訊，請參閱 [並存執行](../../deployment/side-by-side-execution.md)。  
  
 使用一個 .NET Framework 版本編譯的應用程式可以在不同版本的 .NET Framework 上執行。 不過，我們建議您針對每個已安裝的 .NET Framework 版本，編譯應用程式的版本，並個別加以執行。 在這兩種情況下，您應該留意 ADO.NET 之間的變更，這些版本可能會影響應用程式的向前相容性或回溯相容性。  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>向前相容性和回溯相容性  

 向前相容性表示可以使用舊版的 .NET Framework 來編譯應用程式，但仍可在較新版本的 .NET Framework 上順利執行。 針對 .NET Framework 版本1.1 撰寫的 ADO.NET 程式碼會向前相容于較新的版本。  
  
 回溯相容性表示會針對較新版本的 .NET Framework 編譯應用程式，但會繼續在舊版 .NET Framework 上執行，而不會遺失任何功能。 當然，這並不是 .NET Framework 新版本所引進之功能的情況。  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC 的 .NET Framework 資料提供者  

 從1.1 版開始，ODBC () 的 .NET Framework Data Provider <xref:System.Data.Odbc> 會納入為 .NET Framework 的一部分。
  
 如果您針對使用 ODBC 資料提供者連接到資料來源的 .NET Framework 版本1.0 開發應用程式，而且想要在 .NET Framework 1.1 版或更新版本上執行該應用程式，則必須將 ODBC 資料提供者的命名空間更新為 **system.object**。 然後，您必須針對較新版本的 .NET Framework 重新編譯它。  
  
 如果您針對使用 ODBC 資料提供者連接到資料來源的 .NET Framework 2.0 版或更新版本所開發的應用程式，而且您想要在 .NET Framework 1.0 版上執行該應用程式，則必須下載 ODBC 資料提供者，並將它安裝在 .NET Framework 1.0 版系統上。 接著，您必須將 ODBC 資料提供者的命名空間變更為 **node.js，然後**針對 .NET Framework 版本1.0 重新編譯應用程式。  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle 的 .NET Framework 資料提供者  

 從1.1 版開始，Oracle () 的 .NET Framework Data Provider <xref:System.Data.OracleClient> 會納入為 .NET Framework 的一部分。
  
 如果您已針對 .NET Framework 2.0 版或更新版本所開發的應用程式使用資料提供者連接到您的資料來源，而您想要在 .NET Framework 1.0 版上執行該應用程式，則必須下載資料提供者，並將它安裝在 .NET Framework 1.0 版系統上。  
  
## <a name="code-access-security"></a>程式碼存取安全性  

 .NET Framework 1.0 版 (中的 .NET Framework 資料提供者 <xref:System.Data.SqlClient> ， <xref:System.Data.OleDb>) 必須以 FullTrust 許可權執行。 嘗試在許可權低於 FullTrust 的區域中，使用 .NET Framework 1.0 版的 .NET Framework k 資料提供者，會導致 <xref:System.Security.SecurityException> 。  
  
 不過，從 .NET Framework 版本2.0 開始，所有 .NET Framework 資料提供者都可以在部分信任的區域中使用。 此外，已將新的安全性功能新增至 .NET Framework 1.1 版的 .NET Framework 資料提供者。 這個功能可讓您限制能在特定安全性區域中使用的連接字串。 您也可以在特定安全性地區內停用空白密碼。 如需詳細資訊，請參閱 [Code Access Security and ADO.NET](code-access-security.md)。  
  
 因為 .NET Framework 的每個安裝都有個別的 Security.config 檔案，所以沒有安全性設定的相容性問題。 但是，如果您的應用程式相依于 .NET Framework 1.1 版和更新版本中所包含之 ADO.NET 的額外安全性功能，您將無法將其散發至1.0 版系統。  
  
## <a name="sqlcommand-execution"></a>SqlCommand 之執行  

 從 .NET Framework 版本1.1 開始，在 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 資料來源執行命令的方式已變更。  
  
 在 .NET Framework 1.0 版中，會 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 在 **sp_executesql** 預存程式的內容中執行所有命令。 結果，凡是會影響連接狀態的命令 (例如，SET NOCOUNT ON) 只適用於目前命令的執行。 若連接已開啟，連接狀態就不會因為任何後續命令的執行而被修改。  
  
 在 .NET Framework 1.1 版和更新版本中， <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 只有當命令包含可提供效能優勢的參數時，才會在 **sp_executesql** 預存程式的內容中執行命令。 這樣的結果是，若連接已開啟，凡是會影響連接狀態的命令 (它包含於非參數化命令中) 都會修改已執行之所有後續命令的連接狀態。  
  
 請考慮使用下列在 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 呼叫中執行的命令批次。  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 在 .NET Framework 1.1 版和更新版本中，當連接開啟時，NOCOUNT 會針對執行的任何後續命令保持開啟狀態。 在 .NET Framework 1.0 版中，NOCOUNT 僅適用于目前的命令執行。  
  
 如果您相依于任一 .NET Framework 版本的行為，這項變更可能會影響應用程式的向前和回溯相容性 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 。  
  
 針對在 .NET Framework 舊版和更新版本上執行的應用程式，您可以撰寫程式碼，以確定無論您正在執行的版本為何，行為都相同。 如果您想要確保某個命令會針對所有後續命令修改連接的狀態，我們建議您使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 來執行命令。 如果您想要確保命令不會針對所有後續命令修改連接，則我們建議您在命令中加入要重設連接狀態的命令。 例如：  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
- [在 ADO.NET 中傳送和修改資料](retrieving-and-modifying-data.md)
