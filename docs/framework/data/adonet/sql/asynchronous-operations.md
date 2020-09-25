---
title: 非同步作業
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: f94a33b1ff06b5433f61687b8e28096ea37b412a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197582"
---
# <a name="asynchronous-operations"></a>非同步作業

某些資料庫作業 (例如命令執行) 可能需要大量時間才能完成。 在這種情況下，單一執行緒的應用程式必須封鎖其他作業並等候命令完成，才會繼續它們自己的作業。 相反地，能夠將長時間執行的作業指定給背景執行緒，即允許前景執行緒在整個作業期間保持使用中。 例如，在 Windows 應用程式中，將長時間執行的作業委派給背景執行緒，可讓使用者介面執行緒在作業執行時維持回應。  
  
 .NET Framework 提供數個標準非同步設計模式，可供開發人員用於利用背景執行緒，讓使用者介面或高優先權執行緒可以完成其他作業。 ADO.NET 在其 <xref:System.Data.SqlClient.SqlCommand> 類別中，支援這些相同的設計模式。 具體而言，<xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> 和 <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> 方法 (與 <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A> 和 <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> 方法配對) 都提供非同步支援。  
  
> [!NOTE]
> 非同步程式設計是 .NET Framework 的核心功能，而 ADO.NET 可充分利用這些標準設計模式。 如需開發人員可使用之各種非同步技術的詳細資訊，請參閱[以非同步的方式呼叫同步方法](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) \(部分機器翻譯\)。  
  
 儘管與 ADO.NET 功能搭配使用非同步技術並不會有任何額外的特殊考量，但大多數的開發人員都只會在 ADO.NET 中使用非同步功能，而不會在 .NET Framework 中的其他領域使用。 瞭解建立多執行緒應用程式的優缺點是很重要的。 此節中後續的範例會指出在建置包含多執行緒功能的應用程式時，開發人員必須考慮的數個重要問題。  
  
## <a name="in-this-section"></a>本節內容  

 [使用回呼的 Windows 應用程式](windows-applications-using-callbacks.md)  
 提供範例來示範如何安全地執行非同步命令，並正確處理與表單及其來自不同執行緒的內容互動。  
  
 [使用等候控制碼 ASP.NET 應用程式](aspnet-apps-using-wait-handles.md)  
 提供範例來示範如何從 ASP.NET 網頁執行多個並行命令，並使用 Wait 控制代碼來管理完成所有命令的作業。  
  
 [在主控台應用程式中輪詢](polling-in-console-applications.md)  
 提供範例來示範如何使用輪詢，以等候主控台應用程式的非同步命令執行完成。 此技術在類別庫或其他沒有使用者介面的應用程式中也有效。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)
- [以非同步的方式呼叫同步方法](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
