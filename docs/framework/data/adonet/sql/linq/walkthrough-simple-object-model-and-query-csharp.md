---
title: "逐步解說：簡單的物件模型和查詢 (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 444692cb035d97b0fe57c1ea9ba7802491ca2160
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>逐步解說：簡單的物件模型和查詢 (C#)
這個逐步解說提供極為簡單的基本端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。 您將建立的實體類別會構成 Northwind 範例資料庫中的 Customers 資料表。 接著，您會建立簡單查詢，以便列出位於倫敦的客戶。  
  
 這個逐步解說的設計是以程式碼為導向，以協助說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 概念。 一般來說，您會使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來建立物件模型。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 本逐步解說的內容是依據 Visual C# 開發設定所撰寫的。  
  
## <a name="prerequisites"></a>必要條件  
  
-   本逐步解說會使用專用資料夾 ("c:\linqtest5") 來保存檔案。 請先建立這個資料夾，再開始逐步解說。  
  
-   這個逐步解說需要使用 Northwind 範例資料庫。 如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。 如需指示，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。 下載此資料庫之後，請將檔案複製到 c:\linqtest5 資料夾。  
  
## <a name="overview"></a>概觀  
 此逐步解說包含六個主要工作：  
  
-   在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中建立 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案。  
  
-   將類別對應至資料庫資料表。  
  
-   指定類別的屬性以表示資料庫資料表。  
  
-   指定與 Northwind 資料庫的連接。  
  
-   建立要對資料庫執行的簡單查詢。  
  
-   執行查詢並觀察結果。  
  
## <a name="creating-a-linq-to-sql-solution"></a>建立 LINQ to SQL 方案  
 在第一個工作中，您要建立一個 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案內含必要的參考，以建置並執行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案。  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>若要建立 LINQ to SQL 方案  
  
1.  在[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2.  在**專案類型**窗格**新專案**對話方塊中，按一下  **Visual C#**。  
  
3.  按一下 [範本] 窗格中的 [主控台應用程式]。  
  
4.  在**名稱**方塊中，輸入**LinqConsoleApp**。  
  
5.  在**位置**方塊中，確認您要儲存專案檔。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="adding-linq-references-and-directives"></a>加入 LINQ 參考和指示詞  
 本逐步解說使用的組件，可能在您的專案中預設為不安裝。 如果 System.Data.Linq 未列為專案中參考 (展開**參考**節點**方案總管 中**)，請將它加入下列步驟所述。  
  
#### <a name="to-add-systemdatalinq"></a>若要加入 System.Data.Linq  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。  
  
2.  在**加入參考**對話方塊中，按一下  **.NET**，按一下 System.Data.Linq 組件，然後按一下**確定**。  
  
     組件隨即加入至專案。  
  
3.  在最上方加入下列指示詞**Program.cs**:  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>將類別對應至資料庫資料表  
 在這個步驟中，您會建立類別並將它對應至資料庫資料表。 這類類別稱為*實體類別*。 請注意，只要加入 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性，即可完成對應。 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性會指定資料庫中資料表的名稱。  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>若要建立實體類別並將它對應至資料庫資料表  
  
-   在 Program.cs 中的 `Program` 類別宣告正上方輸入或貼上下列程式碼：  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>指定類別的屬性以表示資料庫資料行  
 在這個步驟中，您會完成下列幾項工作：  
  
-   您會使用 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute) 指定實體類別的 `CustomerID` 和 `City` 屬性 (Property)，以表示資料庫資料表中的資料行。  
  
-   您會指定 `CustomerID` 屬性 (Property)，以表示資料庫中的主索引鍵資料行。  
  
-   您會指定 `_CustomerID` 和 `_City` 欄位做為私用儲存區。 然後，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可以直接儲存和擷取值，而不必使用可能含有商務邏輯的公用存取子。  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>若要表示兩個資料庫資料行的特性  
  
-   在 Program.cs 中 `Customer` 類別的大括號內輸入或貼上列程式碼：  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>指定與 Northwind 資料庫的連接  
 在這個步驟中，您會使用 <xref:System.Data.Linq.DataContext> 物件，在程式碼架構的資料結構與資料庫本身間建立連接。 <xref:System.Data.Linq.DataContext> 為主要通道，您可透過該通道擷取資料庫中的物件以及送出變更。  
  
 您也可以宣告 `Table<Customer>` 做為邏輯具型別資料表，供您查詢資料庫中的 Customers 資料表。 您會在後面幾個步驟中，建立和執行這些查詢。  
  
#### <a name="to-specify-the-database-connection"></a>若要指定資料庫連接  
  
-   將下列程式碼輸入或貼到 `Main` 方法中。  
  
     請注意，`northwnd.mdf` 檔案會假設位於 linqtest5 資料夾中。 如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a>建立簡單查詢  
 在這個步驟中，您會建立查詢以尋找資料庫 Customers 資料表中有哪些客戶位於倫敦。 這個步驟中的查詢程式碼只會描述查詢， 而不會實際執行。 這種方法稱為*延後執行*。 如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
 此外，您還會產生記錄檔輸出，以顯示 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 所產生的 SQL 命令。 這項記錄功能 (其使用 <xref:System.Data.Linq.DataContext.Log%2A>) 有助於進行偵錯，以及判斷要傳送至資料庫的命令是否正確地表示您的查詢。  
  
#### <a name="to-create-a-simple-query"></a>建立簡單查詢  
  
-   在 `Main` 方法中的 `Table<Customer>` 宣告之後輸入或貼上下列程式碼。  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a>執行查詢  
 在這個步驟中，您要實際執行這個查詢。 而在需要結果時，才會評估您在前面的步驟中建立的查詢運算式。 當您開始 `foreach` 反覆運算時，會對資料庫執行 SQL 命令，並且將物件具體化。  
  
#### <a name="to-execute-the-query"></a>查詢查詢  
  
1.  在 `Main` 方法的尾端輸入或貼上下列程式碼 (在查詢描述之後)。  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  按 F5，進行應用程式偵錯。  
  
    > [!NOTE]
    >  如果您的應用程式產生執行階段錯誤，請參閱 < 疑難排解 > 一節的[依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)。  
  
     主控台視窗中的查詢結果應如下所示：  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  在主控台視窗中按 Enter 鍵，以關閉應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 [逐步解說： 跨關聯性查詢 (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)主題會繼續本逐步解說結束的位置。 跨關聯性查詢 > 逐步解說將示範如何[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]跨資料表，類似於查詢*聯結*關聯式資料庫中。  
  
 如果您想執行＜跨關聯性查詢＞逐步解說，請務必儲存您剛在本逐步解說完成的方案，這是必要的條件。  
  
## <a name="see-also"></a>請參閱  
 [依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
