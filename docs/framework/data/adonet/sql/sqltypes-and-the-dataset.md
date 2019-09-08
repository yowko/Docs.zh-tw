---
title: SqlTypes 和資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791494"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes 和資料集
ADO.NET 2.0 透過 `DataSet` 命名空間 (Namespace) 導入了 <xref:System.Data.SqlTypes> 的增強型別支援。 <xref:System.Data.SqlTypes> 中型別的設計目的是要提供與 SQL Server 資料庫中的資料型別具有相同語意 (Semantics) 及精確度的資料型別。 <xref:System.Data.SqlTypes> 中的每個資料型別，在 SQL Server 中都具有對應的資料型別，並且具有相同的基礎資料表示。  
  
 使用 SQL Server 資料型別時，若在 <xref:System.Data.SqlTypes> 中直接使用 <xref:System.Data.DataSet> 會有一些優點。 <xref:System.Data.SqlTypes> 與 SQL Server 原生資料型別支援相同的語意。 在 <xref:System.Data.SqlTypes> 的定義中指定其中一個 <xref:System.Data.DataColumn> 可避免將 decimal 或 numeric 資料型別轉換成其中一種 Common Language Runtime (CLR) 資料型別時可能會發生的精確度遺失。  
  
## <a name="example"></a>範例  
 下列範例會建立 <xref:System.Data.DataTable> 物件，它會使用 <xref:System.Data.DataColumn> 而非 CLR 型別來明確定義 <xref:System.Data.SqlTypes> 資料型別。 該程式碼會將 SQL Server 中 AdventureWorks 資料庫內 Sales.SalesOrderDetail 資料表的資料，填入 <xref:System.Data.DataTable>。 出現在主控台視窗中的輸出顯示每個資料行的資料型別，以及從 SQL Server 擷取出來的值。  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型對應](../sql-server-data-type-mappings.md)
- [設定參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md)
- [ADO.NET 概觀](../ado-net-overview.md)
