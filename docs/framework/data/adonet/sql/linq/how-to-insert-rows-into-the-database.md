---
title: 如何：將資料列插入至資料庫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 4f46e38642d42e3a2e4d5f05e23cc76cf431119b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361730"
---
# <a name="how-to-insert-rows-into-the-database"></a>如何：將資料列插入至資料庫
您將資料列插入資料庫將物件加入至相關聯[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Table%601>集合，然後將變更提交至資料庫。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 將轉譯成適當的 SQL 變更`INSERT`命令。  
  
> [!NOTE]
>  您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。 如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。  
>   
>  使用 Visual Studio 的開發人員可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]來開發預存程序相同的目的。  
  
 下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。 如需詳細資訊，請參閱[如何： 連接到資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。  
  
### <a name="to-insert-a-row-into-the-database"></a>若要將資料列插入至資料庫  
  
1.  建立包含所要提交之資料欄資料的新物件。  
  
2.  將新的物件加入[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]`Table`資料庫之目標資料表相關聯的集合。  
  
3.  將變更提交至資料庫。  
  
## <a name="example"></a>範例  
 下列程式碼範例會建立 `Order` 型別的新物件，並且以適當的值填入 (Populate) 其中。 然後，將新物件加入至 `Order` 集合中。 最後，將變更當做 `Orders` 資料表中的新資料列，提交至資料庫。  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [如何：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [DataContext 方法 （O/R 設計工具）](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [變更和提交資料](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
