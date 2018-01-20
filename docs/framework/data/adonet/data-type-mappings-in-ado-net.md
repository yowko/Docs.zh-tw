---
title: "ADO.NET 中的資料類型對應"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a75914e032adf5b160724e17966b683a119b69a7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET 中的資料類型對應
.NET Framework 是以一般型別系統為基礎，其中定義了型別在執行階段的宣告、使用和管理方式。 它同時包含了都衍生自 <xref:System.Object> 基底類型的實值型別 (Value Type) 和參考型別 (Reference Type)。 使用資料來源時，如果沒有明確指定資料型別，就會從資料提供者 (Data Provider) 推斷資料型別。 例如，<xref:System.Data.DataSet> 物件與任何特定資料來源無關。 `DataSet` 內的資料是由資料來源擷取而來，且變更會藉由 `DataAdapter` 存回資料來源； 也就是說，當 `DataAdapter` 將來自資料來源的值填入 <xref:System.Data.DataTable> 內的 `DataSet`時，`DataTable` 內資料行的結果資料型別屬於 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別，而非 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者用於連接資料來源的特定型別。  
  
 同樣的道理，當 `DataReader` 從資料來源傳回值時，結果值會儲存在具有 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別的本機變數內。 `Fill` 的 `DataAdapter` 作業與 `Get` 的 `DataReader` 方法都是以 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者傳回的值來推斷 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別。  
  
 如果您知道傳回值的特定型別，就可以使用 `DataReader` 具型別的存取子方法，而不用仰賴推斷的資料型別。 具型別的存取子方法能達到較高的效能，因為它能將值當作特定的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別傳回，不需要另外轉換型別。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者資料型別的 Null 值都是由 `DBNull.Value` 表示。  
  
## <a name="in-this-section"></a>本節內容  
 [SQL Server 資料類型對應](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 列出 <xref:System.Data.SqlClient> 的推斷資料型別對應和資料存取子方法。  
  
 [OLE DB 資料類型對應](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 列出 <xref:System.Data.OleDb> 的推斷資料型別對應和資料存取子方法。  
  
 [ODBC 資料類型對應](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 列出 <xref:System.Data.Odbc> 的推斷資料型別對應和資料存取子方法。  
  
 [Oracle 資料類型對應](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 列出 <xref:System.Data.OracleClient> 的推斷資料型別對應和資料存取子方法。  
  
 [浮點數](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 說明開發人員在使用浮點數值 (Floating-Point Number) 時經常遇到的問題。  
  
## <a name="see-also"></a>請參閱  
 [SQL Server 資料類型和 ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [設定參數和參數資料類型](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [一般類型系統](../../../../docs/standard/base-types/common-type-system.md)  
 [轉換類型](http://msdn.microsoft.com/library/6038316e-bdaf-4f55-8006-407f591ce156)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
