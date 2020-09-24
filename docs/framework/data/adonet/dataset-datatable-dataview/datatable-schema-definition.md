---
title: DataTable 結構描述定義
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 0c14c6012c65039e1e2e7e2d2d8c38c4202b45a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153244"
---
# <a name="datatable-schema-definition"></a>DataTable 結構描述定義

資料表的結構描述 (或結構) 是由資料行或條件約束來表示。 您可以使用 <xref:System.Data.DataTable> 物件以及 <xref:System.Data.DataColumn> 和 <xref:System.Data.ForeignKeyConstraint> 物件來定義 <xref:System.Data.UniqueConstraint> 的結構描述。 資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。  
  
 依名稱參考資料表的資料行、關聯和條件約束時必須區分大小寫。 兩個或兩個以上名稱相同的資料行、關聯或條件約束可因此存在於同一個資料表中，但其大小寫必須不同。 例如，您可以有 **col1** 和 **col1**。 在這種情況下，依名稱參考其中一個資料行時，必須與資料行名稱的大小寫完全相符，否則將發生例外狀況。 例如，如果資料表 **myTable** 包含資料行 **col1** 和 **col1**，您就會依名稱將 **col1** 參考為 **mytable. columns ["col1"]**，並將 **col1** 視為 **mytable. columns ["col1"]**。 嘗試以 MyTable 的形式參考其中一個資料行 **。資料行 ["COL1"]** 會產生例外狀況。  
  
 如果只有一個資料行、關聯和條件約束使用特定的名稱，則不適用區分大小寫的規則。 也就是說，如果資料表中沒有其他的資料行、關聯和條件約束物件與該特定資料行、關聯或條件約束物件的名稱相符，您在依名稱參考物件時就不需區分大小寫，而且也不會發生任何例外狀況。 例如，如果資料表只有 **Col1**，您可以使用 my 來參考它 **。資料行 ["COL1"]**。  
  
> [!NOTE]
> <xref:System.Data.DataTable.CaseSensitive%2A> **DataTable**的屬性不會影響此行為。 **CaseSensitive**屬性適用于資料表中的資料，並會影響排序、搜尋、篩選、強制執行條件約束等，而不會影響資料行、關聯和條件約束的參考。  
  
## <a name="in-this-section"></a>本節內容  

 [將資料行加入至 DataTable](adding-columns-to-a-datatable.md)  
 描述如何使用 **DataColumn** 物件來定義資料表的資料行。  
  
 [建立運算式資料行](creating-expression-columns.md)  
 說明如何使用資料行的 **Expression** 屬性，根據資料列中的其他資料行值來計算值。  
  
 [建立自動遞增資料行](creating-autoincrement-columns.md)  
 說明如何將資料行設定為自動累加數值，以確保每個資料列都有唯一的資料行值。  
  
 [定義主索引鍵](defining-primary-keys.md)  
 描述如何從一個或多個 **DataColumn** 物件指定資料表的主鍵。  
  
 [DataTable 條件約束](datatable-constraints.md)  
 說明如何在資料表中定義資料行的外部索引鍵條件約束和唯一的條件約束。  
  
## <a name="see-also"></a>另請參閱

- [DataTables](datatables.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
