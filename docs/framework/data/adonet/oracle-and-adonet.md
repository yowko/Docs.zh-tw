---
title: Oracle 和 ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: ce92705d22edfc832e894dd2feaafcd11088bf26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120662"
---
# <a name="oracle-and-adonet"></a>Oracle 和 ADO.NET
> [!NOTE]
>  <xref:System.Data.OracleClient> 中的型別已被取代。 目前版本的 .NET Framework 仍然支援這些型別，不過未來的版本就會將其移除。 Microsoft 建議您使用協力廠商的 Oracle 提供者。  
  
 本節說明 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle 特定的功能與行為。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle 利用 Oracle 用戶端軟體所提供的「Oracle 呼叫介面」(OCI) 來存取 Oracle 資料庫。 資料提供者的功能設計類似於的[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]的 SQL Server、 OLE DB 和 ODBC 資料提供者。  
  
 若要使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle，應用程式必須參考 <xref:System.Data.OracleClient> 命名空間，如下所示：  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 當您編譯程式碼時，還必須將參考併入 DLL 中。 例如，如果編譯 C# 程式，則命令列應包括：  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>本節內容  
 [系統需求](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 說明使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle 的需求，以及一些在使用時所要注意的問題。  
  
 [Oracle BFILE](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 說明用來與 Oracle BFILE 資料型別搭配使用的 <xref:System.Data.OracleClient.OracleBFile> 類別。  
  
 [Oracle LOB](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 說明用來與 Oracle LOB 資料型別搭配使用的 <xref:System.Data.OracleClient.OracleLob> 類別。  
  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 說明 Oracle REF CURSOR 資料型別的支援。  
  
 [OracleType](../../../../docs/framework/data/adonet/oracletypes.md)  
 說明可用來與 Oracle 資料型別搭配使用的結構，包括 <xref:System.Data.OracleClient.OracleNumber> 及 <xref:System.Data.OracleClient.OracleString>。  
  
 [Oracle 序列](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 說明針對擷取伺服器產生的索引鍵 Oracle Sequence 值所提供的支援。  
  
 [Oracle 資料類型對應](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 列出 Oracle 資料型別及其與 <xref:System.Data.OracleClient.OracleDataReader> 的對應。  
  
 [Oracle 分散式異動](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 說明如果 <xref:System.Data.OracleClient.OracleConnection> 物件判定異動處於作用中，它會如何自動登記在現有的分散式異動中。  
  
## <a name="related-sections"></a>相關章節  
 [設定 ADO.NET 應用程式的安全性](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 說明使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 的安全程式碼撰寫實施方針。  
  
 [DataSet、DataTable 和 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 說明如何建立及使用 `DataSets`、具型別 `DataSets`、`DataTables` 和 `DataViews`。  
  
 [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 說明如何使用 ADO.NET 中的資料。  
  
 [SQL Server 和 ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 說明如何使用 SQL Server 特有的特性和功能。  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 說明可讓您在 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中撰寫提供者獨立程式碼的泛用類別。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
