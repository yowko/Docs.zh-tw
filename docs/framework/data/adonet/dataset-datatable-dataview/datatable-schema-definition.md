---
title: DataTable 結構描述定義
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: e8710e7d92558f525a6feaedf8d0635c5ce6e2c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163068"
---
# <a name="datatable-schema-definition"></a>DataTable 結構描述定義
資料表的結構描述 (或結構) 是由資料行或條件約束來表示。 您可以使用 <xref:System.Data.DataTable> 物件以及 <xref:System.Data.DataColumn> 和 <xref:System.Data.ForeignKeyConstraint> 物件來定義 <xref:System.Data.UniqueConstraint> 的結構描述。 資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。  
  
 依名稱參考資料表的資料行、關聯和條件約束時必須區分大小寫。 兩個或兩個以上名稱相同的資料行、關聯或條件約束可因此存在於同一個資料表中，但其大小寫必須不同。 例如，您可以有**Col1**並**col1**。 在這種情況下，依名稱參考其中一個資料行時，必須與資料行名稱的大小寫完全相符，否則將發生例外狀況。 例如，如果資料表**myTable**包含資料行**Col1**並**col1**，您應該要參考**Col1**名稱做為**myTable.Columns["Col1"]**，並**col1**作為**myTable.Columns["col1"]**。 嘗試參考的資料行**myTable.Columns["COL1"]** 會產生例外狀況。  
  
 如果只有一個資料行、關聯和條件約束使用特定的名稱，則不適用區分大小寫的規則。 也就是說，如果資料表中沒有其他的資料行、關聯和條件約束物件與該特定資料行、關聯或條件約束物件的名稱相符，您在依名稱參考物件時就不需區分大小寫，而且也不會發生任何例外狀況。 例如，如果資料表只有**Col1**，您可以參考使用**我。資料行 ["COL1"]**。  
  
> [!NOTE]
>  <xref:System.Data.DataTable.CaseSensitive%2A>的屬性**DataTable**不會影響這個行為。 **CaseSensitive**屬性適用於資料中的資料表和影響排序、 搜尋、 篩選、 強制執行條件約束，並依此類推，但不是能參考資料行、 關聯和條件約束。  
  
## <a name="in-this-section"></a>本節內容  
 [將資料行加入至 DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 描述如何定義的資料表使用的資料行**DataColumn**物件。  
  
 [建立運算式資料行](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 說明如何**運算式**資料行屬性可以用來計算資料列中的其他資料行的值為基礎的值。  
  
 [建立自動遞增資料行](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 說明如何將資料行設定為自動累加數值，以確保每個資料列都有唯一的資料行值。  
  
 [定義主索引鍵](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 描述如何指定從一或多個資料表的主索引鍵**DataColumn**物件。  
  
 [DataTable 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 說明如何在資料表中定義資料行的外部索引鍵條件約束和唯一的條件約束。  
  
## <a name="see-also"></a>另請參閱

- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
