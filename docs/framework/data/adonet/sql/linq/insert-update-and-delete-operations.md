---
title: 插入、更新和刪除作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: e0d2889ef0aeab4a1ca60b1b44a067a221ab541c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956846"
---
# <a name="insert-update-and-delete-operations"></a>插入、更新和刪除作業
您可以加入、變更和移除物件模型 (Object Model) 中的物件，以便在 `Insert` 中執行 `Update`、`Delete` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 作業。 根據預設，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您的動作轉譯成 SQL 並將變更提交至資料庫。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]提供操作和保存您對物件所做變更的最大彈性。 一旦取得實體物件 (透過查詢加以擷取或重新加以建構)，您就可以將它們變更為應用程式中的典型物件。 也就是說, 您可以變更它們的值, 您可以將它們新增至您的集合, 也可以從集合中移除它們。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會追蹤這些變更，而且在您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時準備好將變更傳送回資料庫。  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援或辨識串聯 (Cascade) 刪除作業。 如果您想要刪除具有條件約束之資料表中的資料列, 您必須在資料庫的外`ON DELETE CASCADE`鍵條件約束中設定規則, 或者使用您自己的程式碼, 先刪除導致父物件無法刪除的子物件。 否則，會擲回例外狀況。 如需詳細資訊，請參閱[如何：從資料庫刪除資料](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)列。  
  
 下列摘錄會使用 Northwind 範例資料庫中的 `Customer` 和 `Order` 類別。 為了簡單起見，並不會顯示類別定義。  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 當您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會自動產生及執行必要的 SQL 命令，以便將變更傳送回資料庫。  
  
> [!NOTE]
> 您通常可以透過預存程序 (Stored Procedure)，使用自訂邏輯來覆寫這個行為。 如需詳細資訊, 請參閱[開發人員覆寫預設行為的責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)。  
>   
>  使用 Visual Studio 的開發人員可以使用物件關聯式設計工具來開發用於此用途的預存程式。  
  
## <a name="see-also"></a>另請參閱

- [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [自訂插入、更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
