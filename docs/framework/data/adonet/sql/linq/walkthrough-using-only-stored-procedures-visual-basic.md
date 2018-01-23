---
title: "逐步解說：僅使用預存程序 (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 800cc7d6a1e4aa836ebe75afcbe29a3532ee173a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a>逐步解說：僅使用預存程序 (Visual Basic)
本逐步解說會針對只用預存程序來存取資料，提供基本的端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。 資料庫管理員會使用這個方法來限制對資料存放區的存取。  
  
> [!NOTE]
>  妳也可以使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式中的預存程序來覆寫預設行為，特別是針對 `Create`、`Update` 和 `Delete` 處理序。 如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。  
  
 基於本逐步解說的目的，您會使用兩個已對應至 Northwind 範例資料庫中之預存程序的方法：CustOrdersDetail 和 CustOrderHist。 當您執行 SqlMetal 命令列工具以產生 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 檔時，就會進行對應。 如需詳細資訊，請參閱本逐步解說後面的「必要條件」一節。  
  
 這個逐步解說並不依賴[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]。 使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員也可以使用 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] 來實作預存程序功能。 請參閱[LINQ to SQL 工具，Visual Studio 中](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 這個逐步解說是使用 Visual Basic 開發設定所撰寫。  
  
## <a name="prerequisites"></a>必要條件  
 本逐步解說需要下列項目：  
  
-   本逐步解說會使用專用資料夾 ("c:\linqtest3") 來保存檔案。 請先建立這個資料夾，再開始逐步解說。  
  
-   Northwind 範例資料庫。  
  
     如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。 如需指示，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。 下載此資料庫之後，請將 northwnd.mdf 檔複製到 c:\linqtest3 資料夾。  
  
-   [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 程式碼檔案會從 Northwind 資料庫產生。  
  
     這個逐步解說是使用 SqlMetal 工具，以下列命令列所撰寫：  
  
     **sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**  
  
     如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
## <a name="overview"></a>總覽  
 此逐步解說包含六個主要工作：  
  
-   在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中設定 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 解決方案。  
  
-   將 System.Data.Linq 組件加入至專案。  
  
-   將資料庫程式碼檔案加入至專案。  
  
-   建立資料庫的連接。  
  
-   設定使用者介面。  
  
-   執行和測試應用程式。  
  
## <a name="creating-a-linq-to-sql-solution"></a>建立 LINQ to SQL 方案  
 在第一個工作中，您要建立一個 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案內含必要的參考，以建置並執行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案。  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>若要建立 LINQ to SQL 方案  
  
1.  在[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]**檔案**功能表上，按一下 **新專案**。  
  
2.  在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 窗格中，展開 [ **Visual Basic**]，然後按一下 [ **Windows**]。  
  
3.  在 [範本]  窗格中，按一下 [Windows Form 應用程式] 。  
  
4.  在**名稱**方塊中，輸入**SprocOnlyApp**。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
     Windows Forms 設計工具隨即開啟。  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>加入 LINQ to SQL 組件參考  
 標準 [Windows Form 應用程式] 範本不包含 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 組件。 您必須按照下列步驟所述自行加入組件：  
  
#### <a name="to-add-systemdatalinqdll"></a>若要加入 System.Data.Linq.dll  
  
1.  在**方案總管] 中**，按一下 [**顯示所有檔案**。  
  
2.  在**方案總管] 中**，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。  
  
3.  在**加入參考**對話方塊中，按一下  **.NET**，按一下 System.Data.Linq 組件，然後按一下**確定**。  
  
     組件隨即加入至專案。  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>將 Northwind 程式碼檔案加入至專案  
 這個步驟假設您已使用 SqlMetal 工具，從 Northwind 範例資料庫產生程式碼檔。 如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>若要將 Northwind 程式碼檔案加入至專案  
  
1.  在**專案**功能表上，按一下 **加入現有項目**。  
  
2.  在**加入現有項目**對話方塊中，移至 c:\linqtest3\northwind.vb，，然後按一下 **新增**。  
  
     northwind.vb file 隨即加入至專案。  
  
## <a name="creating-a-database-connection"></a>建立資料庫連接  
 在這個步驟中，您會定義與 Northwind 範例資料庫的連接。 本逐步解說會使用 "c:\linqtest3\northwnd.mdf" 做為路徑。  
  
#### <a name="to-create-the-database-connection"></a>若要建立資料庫連接  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**Form1.vb**，然後按一下 [**檢視程式碼**。  
  
     `Class Form1` 會顯示在程式碼編輯器中。  
  
2.  在 `Form1` 程式碼區塊中輸入下列程式碼：  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a>設定使用者介面  
 在這項工作中您會建立介面，供使用者執行預存程序來存取資料庫中的資料。 在您按照本逐步解說開發的應用程式中，使用者只能透過應用程式內嵌的預存程序來存取資料庫中的資料。  
  
#### <a name="to-set-up-the-user-interface"></a>若要設定使用者介面  
  
1.  返回 [Windows Form 設計工具 (**form1.vb]**)。  
  
2.  在 [ **檢視** ] 功能表上，按一下 [ **工具箱**]。  
  
     工具箱隨即開啟。  
  
    > [!NOTE]
    >  按一下**自動隱藏**圖釘，保持工具箱 中開啟，當您執行的剩餘時這一節的步驟。  
  
3.  將兩個按鈕、 兩個文字方塊和兩個標籤從工具箱拖曳至拖曳**Form1**。  
  
     如附圖所示排列控制項。 展開**Form1** ，讓控制項輕易納入。  
  
4.  以滑鼠右鍵按一下**Label1**，然後按一下 **屬性**。  
  
5.  變更**文字**屬性從**Label1**至**輸入 OrderID:**。  
  
6.  相同的方式對**Label2**，變更**文字**屬性從**Label2**至**輸入 CustomerID:**。  
  
7.  同樣地，在變更**文字**屬性**Button1**至**Order Details**。  
  
8.  變更**文字**屬性**Button2**至**訂單記錄**。  
  
     使按鈕控制項變寬，才能看見所有文字。  
  
#### <a name="to-handle-button-clicks"></a>若要處理按鈕按一下動作  
  
1.  按兩下**Order Details**上**Form1**建立`Button1`事件處理常式並開啟程式碼編輯器。  
  
2.  將下列程式碼輸入到 `Button1` 處理常式中：  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  現在按兩下**Button2**上建立的 Form1`Button2`事件處理常式並開啟程式碼編輯器。  
  
4.  將下列程式碼輸入到 `Button2` 處理常式中：  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 現在開始測試您的應用程式。 請注意，您與資料存放區的接觸受限於這兩個預存程序可以採取的所有動作。 這些動作是為了傳回任何您輸入之 orderID 所含的產品，或傳回任何您輸入之 CustomerID 所訂購的產品記錄。  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  按 F5 鍵啟動偵錯作業。  
  
     Form1 隨即出現。  
  
2.  在**輸入 OrderID**方塊中，輸入**10249** ，然後按一下  **Order Details**。  
  
     訊息方塊會列出訂單 10249 中所含的產品。  
  
     按一下**確定**以關閉訊息方塊。  
  
3.  在**輸入 CustomerID**方塊中，輸入`ALFKI`，然後按一下 **訂單記錄**。  
  
     訊息方塊會列出客戶 ALFKI 的訂單記錄。  
  
     按一下**確定**以關閉訊息方塊。  
  
4.  在**輸入 OrderID**方塊中，輸入`123`，然後按一下  **Order Details**。  
  
     訊息方塊會顯示 "No results."  
  
     按一下**確定**以關閉訊息方塊。  
  
5.  在**偵錯**功能表上，按一下 **停止偵錯**。  
  
     偵錯工作階段 (Session) 隨即關閉。  
  
6.  如果您已完成實驗，您可以按一下**關閉專案**上**檔案**功能表上，並儲存您的專案，當系統提示您。  
  
## <a name="next-steps"></a>後續步驟  
 您可以進行一些變更，以強化這個專案。 例如，您可以在清單方塊中列出可用的預存程序，讓使用者選取所要執行的程序。 您也可以將報表輸出送至文字檔。  
  
## <a name="see-also"></a>請參閱  
 [依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
