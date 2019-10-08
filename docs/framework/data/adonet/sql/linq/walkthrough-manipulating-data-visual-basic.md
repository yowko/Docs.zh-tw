---
title: 逐步解說：操作資料 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 7acce3f8483fab3c2978de7cbd1b9d875900f1d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003391"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>逐步解說：操作資料 (Visual Basic)
本逐步解說針對加入、修改和刪除資料庫中的資料，提供基本的端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。 您將使用範例 Northwind 資料庫的複本來加入客戶、變更客戶名稱，以及刪除訂單。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 這個逐步解說是使用 Visual Basic 開發設定所撰寫。  
  
## <a name="prerequisites"></a>必要條件  
 本逐步解說需要下列項目：  
  
- 本逐步解說會使用專用資料夾 ("c:\linqtest2") 來保存檔案。 請先建立這個資料夾，再開始逐步解說。  
  
- Northwind 範例資料庫。  
  
     如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。 如需指示，請參閱[下載範例資料庫](downloading-sample-databases.md)。 下載資料庫之後，請將 northwnd.mdf 檔案複製至 c:\linqtest2 資料夾。  
  
- 從 Northwind 資料庫產生的 Visual Basic 程式碼檔。  
  
     您可以使用物件關聯式設計工具或 SQLMetal 工具來產生這個檔案。 本逐步解說是使用 SQLMetal 工具，以下列命令列所撰寫：  
  
     **sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**  
  
     如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。  
  
## <a name="overview"></a>總覽  
 此逐步解說包含六個主要工作：  
  
- 在 Visual Studio 中建立 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 解決方案。  
  
- 將資料庫程式碼檔案加入至專案。  
  
- 建立新的客戶物件。  
  
- 修改客戶的連絡人名稱。  
  
- 刪除訂單。  
  
- 將這些變更送出至 Northwind 資料庫。  
  
## <a name="creating-a-linq-to-sql-solution"></a>建立 LINQ to SQL 方案  
 在第一項工作中，您會建立 Visual Studio 方案，其中包含組建和執行 @no__t 0 專案所需的參考。  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>若要建立 LINQ to SQL 方案  
  
1. 在 Visual Studio 的 [檔案] 功能表上，按一下 [新增專案]。  
  
2. 在 [**新增專案**] 對話方塊的 [**專案類型**] 窗格中，按一下 [ **Visual Basic**]。  
  
3. 按一下 [範本] 窗格中的 [主控台應用程式]。  
  
4. 在 [**名稱**] 方塊中，輸入**LinqDataManipulationApp**。  
  
5. 按一下 [確定]。  
  
## <a name="adding-linq-references-and-directives"></a>加入 LINQ 參考和指示詞  
 本逐步解說使用的組件，可能在您的專案中預設為不安裝。 如果 `System.Data.Linq` 未列為專案中的參考（按一下**方案總管**中的 [**顯示所有**檔案]，然後展開 [**參考**] 節點），請將它加入，如下列步驟所述。  
  
#### <a name="to-add-systemdatalinq"></a>若要加入 System.Data.Linq  
  
1. 在**方案總管**中，以滑鼠右鍵按一下 [**參考**]，然後按一下 [**加入參考**]。  
  
2. 在 [**加入參考**] 對話方塊中，按一下 [ **.net**]，再按一下 [system.string] 元件，然後按一下 **[確定]** 。  
  
     組件隨即加入至專案。  
  
3. 在 [程式碼編輯器] 中，于**Module1**上方加入下列指示詞：  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>將 Northwind 程式碼檔案加入至專案  
 這些步驟假設您已使用 SQLMetal 工具，從 Northwind 範例資料庫產生程式碼檔案。 如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>若要將 Northwind 程式碼檔案加入至專案  
  
1. 在 [**專案**] 功能表上，按一下 [**加入現有專案**]。  
  
2. 在 [**加入現有專案**] 對話方塊中，流覽至 [c:\linqtest2\northwind.vb]，然後按一下 [**新增**]。  
  
     northwind.vb file 隨即加入至專案。  
  
## <a name="setting-up-the-database-connection"></a>設定資料庫連接  
 請先測試與資料庫的連接。 請特別注意，資料庫的名稱 (Northwnd) 沒有字母 i。 如果在後續步驟發生錯誤，則請檢閱 northwind.vb 檔案，以判斷 Northwind 部分類別的拼法。  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>若要設定和測試資料庫連接  
  
1. 在 `Sub Main` 中輸入或貼上下列程式碼：  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. 按 F5，立即測試應用程式。  
  
     **主控台**視窗隨即開啟。  
  
     在**主控台**視窗中按 enter 鍵，或按一下 [Visual Studio] [**調試**程式] 功能表上的 [**停止**偵測]，以關閉應用程式。  
  
## <a name="creating-a-new-entity"></a>建立新的實體  
 建立新的實體十分簡單。 您可以使用 `Customer` 關鍵字，建立物件 (如 `New`)。  
  
 在本節和下列各節中，您變更的只是本機快取。 在本逐步解說最後呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 之前，都不會將變更傳送至資料庫。  
  
#### <a name="to-add-a-new-customer-entity-object"></a>若要加入新的 Customer 實體物件  
  
1. 在 `Customer` 中的 `Console.ReadLine` 之前加入下列程式碼，以建立新的 `Sub Main`：  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. 按 F5 對方案進行偵錯。  
  
     主控台視窗中顯示的結果如下：  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     請注意，新的資料列不會出現在結果中。 新的資料尚未送出至資料庫。  
  
3. 在**主控台**視窗中按 enter 鍵，以停止進行調試。  
  
## <a name="updating-an-entity"></a>更新實體  
 在下列步驟中，您會擷取 `Customer` 物件，並修改它的其中一個屬性。  
  
#### <a name="to-change-the-name-of-a-customer"></a>若要變更 Customer 的名稱  
  
- 將下列程式碼加入至 `Console.ReadLine()` 的上方：  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>刪除實體  
 您可以使用同一個客戶物件，刪除第一份訂單。  
  
 在下列程式碼中，會示範如何中斷資料列之間的關聯性 (Relationship)，以及如何刪除資料庫中的資料列。  
  
#### <a name="to-delete-a-row"></a>若要刪除資料列  
  
- 將下列程式碼加入至 `Console.ReadLine()` 的正上方：  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>將變更送出至資料庫  
 建立、更新和刪除物件所需的最後一個步驟是實際將變更送出至資料庫。 沒有這個步驟，所進行的變更只是針對本機，並不會出現在查詢結果中。  
  
#### <a name="to-submit-changes-to-the-database"></a>若要將變更送出至資料庫  
  
1. 將下列程式碼插入至 `Console.ReadLine` 的正上方：  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. 將下列程式碼插入至 `SubmitChanges` 的後面，以顯示送出變更之前和之後的效果：  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. 按 F5 對方案進行偵錯。  
  
     主控台視窗隨即出現如下內容：  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. 在**主控台**視窗中按 enter 鍵，以停止進行調試。  
  
> [!NOTE]
> 送出變更以加入新的客戶之後，因為您無法再原樣加入同一位客戶，所以無法再原樣執行這個方案。 若要再執行一次這個方案，請變更要加入的客戶 ID 值。  
  
## <a name="see-also"></a>另請參閱

- [依逐步解說學習](learning-by-walkthroughs.md)
