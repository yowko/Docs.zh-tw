---
title: 資料類型對應
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 52e64714a17448cd94723bdc216d8ea069fc5eef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177744"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET 中的資料類型對應

.NET Framework 是以一般型別系統為基礎，其中定義了型別在執行階段的宣告、使用和管理方式。 它同時包含了都衍生自 <xref:System.Object> 基底類型的實值型別 (Value Type) 和參考型別 (Reference Type)。 使用資料來源時，如果沒有明確指定資料型別，就會從資料提供者 (Data Provider) 推斷資料型別。 例如，<xref:System.Data.DataSet> 物件與任何特定資料來源無關。 `DataSet` 內的資料是由資料來源擷取而來，且變更會藉由 `DataAdapter` 存回資料來源； 這表示當使用 `DataAdapter` 資料來源中的值填滿時 <xref:System.Data.DataTable> `DataSet` ，中的資料行產生的資料類型 `DataTable` 會是 .NET Framework 類型，而不是用來連接到資料來源之 .NET Framework 資料提供者的特定類型。  
  
 同樣地，當 `DataReader` 從資料來源傳回值時，產生的值會儲存在具有 .NET Framework 類型的本機變數中。 對於的 `Fill` 作業 `DataAdapter` 和的 `Get` 方法 `DataReader` ，會從 .NET Framework 資料提供者傳回的值來推斷 .NET Framework 型別。  
  
 如果您知道傳回值的特定型別，就可以使用 `DataReader` 具型別的存取子方法，而不用仰賴推斷的資料型別。 具型別存取子方法會以特定的 .NET Framework 型別傳回值，以提供更好的效能，這樣就不需要額外的型別轉換。  
  
> [!NOTE]
> .NET Framework 資料提供者資料類型的 Null 值是以表示 `DBNull.Value` 。  
  
## <a name="in-this-section"></a>本節內容  

 [SQL Server 資料類型對應](sql-server-data-type-mappings.md)  
 列出 <xref:System.Data.SqlClient> 的推斷資料型別對應和資料存取子方法。  
  
 [OLE DB 資料類型對應](ole-db-data-type-mappings.md)  
 列出 <xref:System.Data.OleDb> 的推斷資料型別對應和資料存取子方法。  
  
 [ODBC 資料類型對應](odbc-data-type-mappings.md)  
 列出 <xref:System.Data.Odbc> 的推斷資料型別對應和資料存取子方法。  
  
 [Oracle 資料類型對應](oracle-data-type-mappings.md)  
 列出 <xref:System.Data.OracleClient> 的推斷資料型別對應和資料存取子方法。  
  
 [浮點數](floating-point-numbers.md)  
 說明開發人員在使用浮點數值 (Floating-Point Number) 時經常遇到的問題。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型和 ADO.NET](./sql/sql-server-data-types.md)
- [設定參數和參數資料類型](configuring-parameters-and-parameter-data-types.md)
- [擷取資料庫結構描述資訊](retrieving-database-schema-information.md)
- [一般類型系統](../../../standard/base-types/common-type-system.md)
- [轉換類型](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
