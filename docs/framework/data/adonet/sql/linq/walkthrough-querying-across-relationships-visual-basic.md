---
title: 逐步解說：跨關聯性查詢 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: abd4941697639ec7bdda545b1ead8d57091e9e7f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314655"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>逐步解說：跨關聯性查詢 (Visual Basic)
本逐步解說示範如何使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]*關聯*表示在資料庫中的外部索引鍵關聯性。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 這個逐步解說是使用 Visual Basic 開發設定所撰寫。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說：簡單的物件模型和查詢 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)。 本逐步解決建置於該逐步解決之上，包含存在於 c:\linqtest 中的 northwnd.mdf 檔。  
  
## <a name="overview"></a>總覽  
 此逐步解說包含三項主要工作：  
  
-   加入實體類別，以表示 Northwind 範例資料庫中的 Orders 資料表。  
  
-   補充 `Customer` 類別的附註，以加強 `Customer` 和 `Order` 類別之間的關聯性。  
  
-   建立和執行查詢，以測試使用 `Order` 類別取得 `Customer` 資訊的處理序。  
  
## <a name="mapping-relationships-across-tables"></a>跨資料表對應關聯性  
 在 `Customer` 類別定義之後，建立包含下列程式碼的 `Order` 實體類別定義，這表示 `Orders.Customer` 為 `Customers.CustomerID` 的外部索引鍵。  
  
#### <a name="to-add-the-order-entity-class"></a>若要加入 Order 實體類別  
  
-   在 `Customer` 類別之後輸入或貼上下列程式碼：  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>加入 Customer 類別的附註  
 在這個步驟中，您會加入 `Customer` 類別的附註，指出其與 `Order` 類別的關聯性 (此加入動作並非絕對必要，因為定義任一方向的關聯性就足以建立連結。 但加入此附註確實可讓您輕易地以任一方向巡覽物件)。  
  
#### <a name="to-annotate-the-customer-class"></a>若要標註 Customer 類別  
  
-   將下列程式碼輸入或貼到 `Customer` 類別中：  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>建立和執行客戶-訂單關聯性的查詢  
 您現在可以直接從 `Order` 物件存取 `Customer` 物件，反之亦然。 您不需要明確*聯結*客戶和訂單之間。  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>若要使用 Customer 物件存取 Order 物件  
  
1. 將下列程式碼輸入或貼到 `Sub Main` 方法，進而修改此方法：  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. 按 F5 對應用程式進行偵錯。  
  
     訊息方塊中會出現兩個名稱，而主控台視窗則會顯示所產生的 SQL 程式碼。  
  
3. 關閉訊息方塊以停止偵錯。  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>建立資料庫的強型別檢視  
 從資料庫的強型別檢視著手會容易許多。 透過建立強型別 <xref:System.Data.Linq.DataContext> 物件，您就不需要呼叫 <xref:System.Data.Linq.DataContext.GetTable%2A>。 當您使用強型別 <xref:System.Data.Linq.DataContext> 物件時，可以在所有查詢中使用強型別資料表。  
  
 在下列步驟中，您會將 `Customers` 建立為強型別資料表，以對應資料庫中的 Customers 資料表。  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>若要建立強型別 DataContext 物件  
  
1. 在 `Customer` 類別宣告之上加入下列程式碼。  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. 修改 `Sub Main` 以使用強型別 <xref:System.Data.Linq.DataContext>，如下所示：  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. 按 F5 對應用程式進行偵錯。  
  
     主控台視窗輸出為：  
  
     `ID=WHITC`  
  
4. 在 [主控台] 視窗中按 Enter 鍵，以關閉應用程式。  
  
5. 在 **檔案**功能表上，按一下**全部儲存**如果您想要儲存此應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 下一個逐步解說 ([逐步解說：操作資料 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) 示範如何操作資料。 該逐步解說並不要求您儲存這系列中已完成的兩個逐步解說。  
  
## <a name="see-also"></a>另請參閱

- [依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
