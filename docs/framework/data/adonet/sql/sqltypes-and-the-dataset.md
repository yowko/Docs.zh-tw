---
title: SqlTypes 和資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: 04f95cd7d3f6e52f644f23dd8a32c77d56a5ddda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147504"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes 和資料集

ADO.NET 2.0 透過 <xref:System.Data.SqlTypes> 命名空間引進了對 `DataSet` 的增強類型支援。 <xref:System.Data.SqlTypes> 中的類型其設計目的是提供與 SQL Server 資料庫中的資料類型具有相同語意及精確度的資料類型。 <xref:System.Data.SqlTypes> 中的每個資料類型，在 SQL Server 中都具有對應的資料類型，並具有相同的基礎資料表示。  
  
 直接在 <xref:System.Data.DataSet> 中使用 <xref:System.Data.SqlTypes>，會在使用 SQL Server 資料類型時帶來數個優點。 <xref:System.Data.SqlTypes> 支援與 SQL Server 原生資料類型相同的語意。 在 <xref:System.Data.DataColumn> 的定義中指定其中一個 <xref:System.Data.SqlTypes>，在將十進位或數值資料類型轉換為通用語言執行平台 (CLR) 資料類型之一時就不會發生精確度遺失。  
  
## <a name="example"></a>範例  

 下列範例建立 <xref:System.Data.DataTable> 物件，其會使用 <xref:System.Data.SqlTypes> 而非 CLR 類型，來明確定義 <xref:System.Data.DataColumn> 資料類型。 該程式碼會將 SQL Server 中 AdventureWorks 資料庫內 Sales.SalesOrderDetail 資料表的資料，填入 <xref:System.Data.DataTable>。 主控台視窗中顯示的輸出會顯示每個資料行的資料類型，以及擷取自 SQL Server 的值。  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型對應](../sql-server-data-type-mappings.md)
- [設定參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
