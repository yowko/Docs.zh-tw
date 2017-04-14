---
title: "逐步解說：跨關聯性查詢 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 逐步解說：跨關聯性查詢 (Visual Basic)
此逐步解說會示範如何使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]「*關聯*」\(Association\) 來表示資料庫中的外部索引鍵關聯性 \(Relationship\)。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 這個逐步解說是使用 Visual Basic 開發設定所撰寫。  
  
## 必要條件  
 您必須已完成[逐步解說：簡單的物件模型和查詢 \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)。  本逐步解決建置於該逐步解決之上，包含存在於 c:\\linqtest 中的 northwnd.mdf 檔。  
  
## 概觀  
 此逐步解說包含三項主要工作：  
  
-   加入實體類別，以表示 Northwind 範例資料庫中的 Orders 資料表。  
  
-   補充 `Customer` 類別的附註，以加強 `Customer` 和 `Order` 類別之間的關聯性。  
  
-   建立和執行查詢，以測試使用 `Customer` 類別取得 `Order` 資訊的處理序。  
  
## 跨資料表對應關聯性  
 在 `Customer` 類別定義之後，建立包含下列程式碼的 `Order` 實體類別定義，這表示 `Orders.Customer` 為 `Customers.CustomerID` 的外部索引鍵。  
  
#### 若要加入 Order 實體類別  
  
-   在 `Customer` 類別之後輸入或貼上下列程式碼：  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## 加入 Customer 類別的附註  
 在這個步驟中，您會加入 `Customer` 類別的附註，指出其與 `Order` 類別的關聯性  \(此加入動作並非絕對必要，因為定義任一方向的關聯性就足以建立連結。  但加入此附註確實可讓您輕易地以任一方向巡覽物件\)。  
  
#### 若要加入 Customer 類別的附註  
  
-   將下列程式碼輸入或貼到 `Customer` 類別中：  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## 建立和執行客戶\-訂單關聯性的查詢  
 您現在可以直接從 `Customer` 物件存取 `Order` 物件，反之亦然。  您不需要客戶和訂單之間的明確「*聯結*」\(Join\)。  
  
#### 若要使用 Customer 物件存取 Order 物件  
  
1.  將下列程式碼輸入或貼到 `Sub Main` 方法，進而修改此方法：  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  按 F5 對應用程式進行偵錯。  
  
     訊息方塊中會出現兩個名稱，而主控台視窗則會顯示所產生的 SQL 程式碼。  
  
3.  關閉訊息方塊以停止偵錯。  
  
## 建立資料庫的強型別檢視  
 從資料庫的強型別檢視著手會容易許多。  透過建立強型別 <xref:System.Data.Linq.DataContext> 物件，您就不需要呼叫 <xref:System.Data.Linq.DataContext.GetTable%2A>。  當您使用強型別 <xref:System.Data.Linq.DataContext> 物件時，可以在所有查詢中使用強型別資料表。  
  
 在下列步驟中，您會將 `Customers` 建立為強型別資料表，以對應資料庫中的 Customers 資料表。  
  
#### 若要建立強型別 DataContext 物件  
  
1.  在 `Customer` 類別宣告之上加入下列程式碼。  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  修改 `Sub Main` 以使用強型別 <xref:System.Data.Linq.DataContext>，如下所示：  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  按 F5 對應用程式進行偵錯。  
  
     主控台視窗輸出為：  
  
     `ID=WHITC`  
  
4.  在 \[主控台\] 視窗中按 Enter 鍵，以關閉應用程式。  
  
5.  如果您想儲存此應用程式，請按一下 \[**檔案**\] 功能表上的 \[**全部儲存**\]。  
  
## 後續步驟  
 下一個逐步解說 \([逐步解說：操作資料 \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)\) 會示範如何管理資料。  該逐步解說並不要求您儲存這系列中已完成的兩個逐步解說。  
  
## 請參閱  
 [從逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)