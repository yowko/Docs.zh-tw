---
title: ADO.NET 中的資料類型對應
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: ddb3c1c5551336ace66bab53af3beb83b6cd2d34
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950406"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET 中的資料類型對應
.NET Framework 是以一般型別系統為基礎，其中定義了型別在執行階段的宣告、使用和管理方式。 它同時包含了都衍生自 <xref:System.Object> 基底類型的實值型別 (Value Type) 和參考型別 (Reference Type)。 使用資料來源時，如果沒有明確指定資料型別，就會從資料提供者 (Data Provider) 推斷資料型別。 例如，<xref:System.Data.DataSet> 物件與任何特定資料來源無關。 `DataSet` 內的資料是由資料來源擷取而來，且變更會藉由 `DataAdapter` 存回資料來源； 這表示當`DataAdapter` `DataSet`使用資料來源中<xref:System.Data.DataTable>的值填滿中的時, 在中的資料行所`DataTable`產生的資料類型會是 .NET Framework 類型, 而不是 .NET Framework Data Provider 特定的類型。用來連接到資料來源。  
  
 同樣地, 當`DataReader`從資料來源傳回值時, 產生的值會儲存在具有 .NET Framework 類型的本機變數中。 針對的`Fill` `DataAdapter` 作業`Get`和的方法,會從.NETFrameworkDataProvider傳回的值推斷.NETFramework類型。`DataReader`  
  
 如果您知道傳回值的特定型別，就可以使用 `DataReader` 具型別的存取子方法，而不用仰賴推斷的資料型別。 具型別的存取子方法藉由傳回值做為特定 .NET Framework 型別, 讓您更好的效能, 而不需要進行其他類型轉換。  
  
> [!NOTE]
> .NET Framework Data Provider 資料類型的 Null 值會以表示`DBNull.Value`。  
  
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
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型和 ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [設定參數和參數資料類型](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [一般類型系統](../../../standard/base-types/common-type-system.md)
- [轉換類型](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
