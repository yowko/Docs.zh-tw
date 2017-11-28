---
title: "如何：更新資料庫中的資料列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ba7d6369b534edf5e8c61605b09823a36143a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-update-rows-in-the-database"></a>如何：更新資料庫中的資料列
您可以藉由修改與相關聯之物件的成員值來更新資料庫中的資料列[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Table%601>集合，然後將變更提交至資料庫。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]將轉譯成適當的 SQL 變更`UPDATE`命令。  
  
> [!NOTE]
>  您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。 如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。  
>   
>  使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來開發預存程序，以達到相同的目的。  
  
 下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。 如需詳細資訊，請參閱[如何： 連接到資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。  
  
### <a name="to-update-a-row-in-the-database"></a>若要更新資料庫中的資料列  
  
1.  查詢資料庫，以找出要更新的資料列。  
  
2.  對結果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件中的成員值進行所需的變更。  
  
3.  將變更提交至資料庫。  
  
## <a name="example"></a>範例  
 下列程式碼範例會查詢資料庫中的訂單編號 11000，然後變更結果 `ShipName` 物件中 `ShipVia` 和 `Order` 的值。 最後，這些成員值的變更會提交至資料庫，成為 `ShipName` 和 `ShipVia` 資料行的變更。  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [建立和提交資料變更](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
