---
title: 非同步作業
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: 72c2cc33185cb7fba5b8c8ce8d3805a6bb76f8d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116034"
---
# <a name="asynchronous-operations"></a>非同步作業
某些資料庫作業 (如命令執行) 要花費相當長的時間才能完成。 在此情況下，單一執行緒應用程式必須封鎖其他作業並等待命令完成後，才能繼續它們自己的作業。 相反的，將長期執行作業指派給背景執行緒，可讓前景執行緒在作業過程中保持作用中狀態。 例如，若在 Windows 應用程式中將長期執行作業委派給背景執行緒，可讓使用者介面執行緒在作業執行時保持回應狀態。  
  
 .NET Framework 提供數個標準非同步設計模式，可供開發人員用於利用背景執行緒，讓使用者介面或高優先權執行緒可以完成其他作業。 ADO.NET 在其 <xref:System.Data.SqlClient.SqlCommand> 類別中，支援這些相同的設計模式。 尤其是，<xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> 及 <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> 方法，搭配 <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A> 及 <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> 方法，都可以提供非同步支援。  
  
> [!NOTE]
>  非同步程式設計是 .NET Framework 的核心功能，而 ADO.NET 可充分利用這些標準設計模式。 如需開發人員可使用之各種非同步技術的詳細資訊，請參閱[Calling Synchronous Methods Asynchronously](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)。  
  
 儘管與 ADO.NET 功能搭配使用非同步技術並不會有任何額外的特殊考量，但大多數的開發人員都只會在 ADO.NET 中使用非同步功能，而不會在 .NET Framework 中的其他領域使用。 瞭解建立多執行緒應用程式的優缺點是很重要的。 本節中接下來的範例會指出在建置包括多執行緒功能的應用程式時，開發人員需要考量的數個重要問題。  
  
## <a name="in-this-section"></a>本節內容  
 [使用回呼的 Windows 應用程式](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 提供範例，示範如何安全地執行非同步命令，以及正確地處理單獨執行緒與表單及其內容之容的互動。  
  
 [使用 Wait 控制代碼的 ASP.NET 應用程式](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 提供範例，示範如何從 ASP.NET 網頁執行多個並行命令，並在所有命令完成後使用等候控制代碼管理作業。  
  
 [在主控台應用程式中輪詢](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 提供範例，示範如何使用輪詢等待從主控台應用程式執行的非同步命令完成。 此技術在類別庫或不具使用者介面的其他應用程式中也有效。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 和 ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [非同步呼叫同步方法](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
