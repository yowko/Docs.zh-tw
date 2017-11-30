---
title: "LINQ to SQL 的功能"
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
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26d20a220f1d88cee0b577d112048c8bb0e84285
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="what-you-can-do-with-linq-to-sql"></a>LINQ to SQL 的功能
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援 SQL 開發人員需要的所有重要功能。 您可以查詢資訊，以及在資料表中插入、更新和刪除資訊。  
  
## <a name="selecting"></a>選取  
 選取 (「*投影*」(Projection)) 的方式很簡單，只要以您自己的程式語言撰寫 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 查詢，再執行該查詢來擷取結果即可。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將所有必要的作業轉譯成熟悉的 SQL 作業。 如需詳細資訊，請參閱 [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md)。  
  
 在下列範例中，會擷取 London 客戶的公司名稱，並將它們顯示在主控台視窗中。  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>插入  
 若要執行 SQL `Insert`，只要將物件加入至所建立的物件模型，並在 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 上呼叫 <xref:System.Data.Linq.DataContext>即可。  
  
 在下列範例中，會使用 `Customers` 將新的客戶與該客戶的相關資訊加入至 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>資料表。  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Updating  
 若要更新 ( `Update` ) 資料庫項目，請先擷取該項目，然後直接在物件模型中編輯該項目。 修改物件之後，再於 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 上呼叫 <xref:System.Data.Linq.DataContext> 以更新資料庫。  
  
 在下列範例中，會擷取所有來自 London 的客戶， 然後將城市的名稱從 "London" 變更為 "London - Metro"。 最後，會呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ，以將變更傳送至資料庫。  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Deleting  
 若要刪除 ( `Delete` ) 項目，請從項目所屬的集合中移除該項目，然後在 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 上呼叫 <xref:System.Data.Linq.DataContext> ，以認可變更。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]無法辨識串聯刪除作業。 如果您想要刪除資料表中的資料列具有條件約束，請參閱[How to： 資料列從資料庫刪除](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)。  
  
 在下列範例中，會從資料庫中擷取 `CustomerID` 為 `98128` 的客戶。 然後會在確認已擷取該客戶的資料列之後，呼叫 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> ，以從集合中移除該物件。 最後，會呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ，以將刪除轉送至資料庫。  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 [程式設計手冊](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [快速入門](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
