---
title: 將 DataTable 加入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 3554790bb65310031b00ca5fb320aa4c111e1e11
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758538"
---
# <a name="adding-a-datatable-to-a-dataset"></a>將 DataTable 加入至資料集
ADO.NET 可讓您建立 <xref:System.Data.DataTable> 物件，並將它們加入現有的 <xref:System.Data.DataSet>。 您可以使用 <xref:System.Data.DataTable> 和 <xref:System.Data.DataTable.PrimaryKey%2A> 屬性，為 <xref:System.Data.DataColumn.Unique%2A> 設定條件約束 (Constraint) 資訊。  
  
## <a name="example"></a>範例  
 下列範例會建構 <xref:System.Data.DataSet>、將新的 <xref:System.Data.DataTable> 物件加入至 <xref:System.Data.DataSet>，然後再將三個 <xref:System.Data.DataColumn> 物件加入至資料表。 最後，程式碼會將一個資料行設定為主索引鍵資料行。  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>區分大小寫  
 <xref:System.Data.DataSet> 中可能有兩個或兩個以上具有相同名稱，但不同大小寫的資料表或關聯。 在這種情況下，按照資料表和關聯名稱進行參考時是區分大小寫的。 例如，如果<xref:System.Data.DataSet>**資料集**包含資料表**Table1**和**table1**，您應該要參考**Table1**使用名稱做為**dataSet.Tables["Table1"]**，和**table1**為**dataSet.Tables["table1"]**。 嘗試參考的資料表做為**dataSet.Tables["TABLE1"]** 仍會產生例外狀況。  
  
 如果只有一個具有特定名稱的資料表或關聯，則不適用區分大小寫規則。 例如，如果<xref:System.Data.DataSet>只剩**Table1**，您可以參考使用**dataSet.Tables["TABLE1"]**。  
  
> [!NOTE]
>  <xref:System.Data.DataSet.CaseSensitive%2A> 的 <xref:System.Data.DataSet> 屬性不會影響這項行為。 <xref:System.Data.DataSet.CaseSensitive%2A> 屬性會套用至 <xref:System.Data.DataSet> 內的資料，並影響排序、搜尋、篩選、強制執行條件約束等方面。  
  
## <a name="namespace-support"></a>命名空間支援   
 在 2.0 之前的 ADO.NET 版本中，兩個資料表不能有相同的名稱，即使它們在不同的命名空間也一樣。 ADO.NET 2.0 已移除這項限制。 <xref:System.Data.DataSet> 可能會包含兩個 <xref:System.Data.DataTable.TableName%2A> 屬性值相同，但 <xref:System.Data.DataTable.Namespace%2A> 屬性值不同的資料表。  
  
## <a name="see-also"></a>另請參閱  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
