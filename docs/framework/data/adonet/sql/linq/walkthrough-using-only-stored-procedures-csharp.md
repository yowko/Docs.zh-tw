---
title: 逐步解說：僅使用預存程序 (C#)
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f980402c976db9ee327a7b726e36a0a4d9d6d73f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792106"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>逐步解說：僅使用預存程序 (C#)

本逐步解說會針對只執行預存程序來存取資料，提供基本的端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。 資料庫管理員會使用這個方法來限制對資料存放區的存取。

> [!NOTE]
> 妳也可以使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式中的預存程序來覆寫預設行為，特別是針對 `Create`、`Update` 和 `Delete` 處理序。 如需詳細資訊，請參閱[自訂插入、更新和刪除作業](customizing-insert-update-and-delete-operations.md)。

基於此逐步解說的目的，您將使用兩個已對應至 Northwind 範例資料庫中之預存程式的方法：CustOrdersDetail 和 CustOrderHist。 當您執行 SqlMetal 命令列工具以產生 C# 檔案時，會發生對應。 如需詳細資訊，請參閱本逐步解說後面的「必要條件」一節。

此逐步解說不依賴物件關聯式設計工具。 使用 Visual Studio 的開發人員也可以使用 O/R 設計工具來執行預存程式功能。 請參閱[Visual Studio 中的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

本逐步解說的內容是依據 Visual C# 開發設定所撰寫的。

## <a name="prerequisites"></a>必要條件

本逐步解說需要下列項目：

- 這個逐步解說會使用專用資料夾 ("c:\linqtest7") 來保存檔案。 請先建立這個資料夾，再開始逐步解說。

- Northwind 範例資料庫。

     如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。 如需指示，請參閱[下載範例資料庫](downloading-sample-databases.md)。 下載資料庫之後，請將 northwnd.mdf 檔案複製至 c:\linqtest7 資料夾。

- 會從 Northwind 資料庫產生 C# 程式碼檔案。

     這個逐步解說是使用 SqlMetal 工具，以下列命令列所撰寫：

     **sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**

     如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。

## <a name="overview"></a>總覽

此逐步解說包含六個主要工作：

- 在 Visual Studio 中設定方案。[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]

- 將 System.Data.Linq 組件加入至專案。

- 將資料庫程式碼檔案加入至專案。

- 建立與資料庫的連接。

- 設定使用者介面。

- 執行和測試應用程式。

## <a name="creating-a-linq-to-sql-solution"></a>建立 LINQ to SQL 方案

在第一項工作中，您會建立 Visual Studio 方案，其中包含組建和執行[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]專案所需的參考。

### <a name="to-create-a-linq-to-sql-solution"></a>若要建立 LINQ to SQL 方案

1. 在 **[Visual Studio 檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。

2. 在 [**新增專案**] 對話方塊的 [**專案類型**] 窗格中，按一下 [  **C#視覺效果**]。

3. 在 [範本] 窗格中，按一下 [Windows Form 應用程式]。

4. 在 [**名稱**] 方塊中，輸入**SprocOnlyApp**。

5. 在 [**位置**] 方塊中，確認您要儲存專案檔案的位置。

6. 按一下 [確定]。

     Windows Forms 設計工具隨即開啟。

## <a name="adding-the-linq-to-sql-assembly-reference"></a>加入 LINQ to SQL 組件參考

標準 [Windows Form 應用程式] 範本不包含 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 組件。 您必須按照下列步驟所述自行加入組件：

### <a name="to-add-systemdatalinqdll"></a>若要加入 System.Data.Linq.dll

1. 在**方案總管**中，以滑鼠右鍵按一下 [**參考**]，然後按一下 [**加入參考**]。

2. 在 [**加入參考**] 對話方塊中，按一下 [ **.net**]，再按一下 [system.string] 元件，然後按一下 **[確定]** 。

     組件隨即加入至專案。

## <a name="adding-the-northwind-code-file-to-the-project"></a>將 Northwind 程式碼檔案加入至專案

這個步驟假設您已使用 SqlMetal 工具，從 Northwind 範例資料庫產生程式碼檔。 如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。

### <a name="to-add-the-northwind-code-file-to-the-project"></a>若要將 Northwind 程式碼檔案加入至專案

1. 在 [**專案**] 功能表上，按一下 [**加入現有專案**]。

2. 在 [**加入現有專案**] 對話方塊中，移至 [c:\linqtest7\northwind.cs]，然後按一下 [**新增**]。

     northwind.cs 檔案會加入至專案。

## <a name="creating-a-database-connection"></a>建立資料庫連接

在這個步驟中，您會定義與 Northwind 範例資料庫的連接。 這個逐步解說會使用 "c:\linqtest7\northwnd.mdf" 做為路徑。

### <a name="to-create-the-database-connection"></a>若要建立資料庫連接

1. 在**方案總管**中，以滑鼠右鍵按一下 [ **Form1.cs**]，然後按一下 [ **View Code**]。

2. 將下列程式碼輸入至 `Form1` 類別中：

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a>設定使用者介面

在這項工作中，您會設定可供使用者執行預存程序的介面，以便存取資料庫中的資料。 在使用這個逐步解說開發的應用程式中，使用者唯有使用應用程式內嵌的預存程序，才可以存取資料庫中的資料。

### <a name="to-set-up-the-user-interface"></a>若要設定使用者介面

1. 返回 Windows Form 設計工具（form1.vb **[Design]** ）。

2. 在 [ **檢視** ] 功能表上，按一下 [ **工具箱**]。

     工具箱隨即開啟。

    > [!NOTE]
    > 按一下 [自動**隱藏**] 圖釘，讓工具箱在您執行本節中的其餘步驟時保持開啟。

3. 將兩個按鈕、兩個文字方塊和兩個標籤從 [工具箱] 拖曳至 [ **Form1**]。

     如附圖所示排列控制項。 展開 [ **Form1** ]，讓控制項輕鬆地調整。

4. 以滑鼠右鍵按一下 [ **label1**]，然後按一下 [**屬性**]。

5. 將 [ **Text** ] 屬性從 [ **label1** ] 變更為**Enter [訂單：** ]。

6. 以相同的方式**label2**，將**Text**屬性從**label2**變更為**Enter CustomerID：** 。

7. 以同樣的方式，將 [ **button1** ] 的 [ **Text** ] 屬性變更為 [**訂單詳細資料**]。

8. 將 [ **button2** ] 的 [ **Text** ] 屬性變更為 [**訂單歷程記錄**]。

     使按鈕控制項變寬，才能看見所有文字。

### <a name="to-handle-button-clicks"></a>若要處理按鈕按一下動作

1. 按兩下 [ **Form1** ] 上的 [**訂單詳細資料**]，以在程式碼編輯器中開啟 button1 事件處理常式。

2. 將下列程式碼輸入到 `button1` 處理常式中：

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. 現在按兩下**Form1**上的 [ `button2` **button2** ] 以開啟處理常式

4. 將下列程式碼輸入到 `button2` 處理常式中：

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a>測試應用程式

現在開始測試您的應用程式。 請注意，您與資料存放區的接觸受限於這兩個預存程序可以採取的所有動作。 這些動作是為了傳回任何您輸入之 orderID 所含的產品，或傳回任何您輸入之 CustomerID 所訂購的產品記錄。

### <a name="to-test-the-application"></a>若要測試應用程式

1. 按 F5 開始偵錯作業。

     Form1 隨即出現。

2. 在 [**輸入訂單**] 方塊中`10249`，輸入，然後按一下 [**訂單詳細資料**]。

     訊息方塊會列出訂單 10249 中所含的產品。

     按一下 **[確定]** 關閉訊息方塊。

3. 在 [**輸入 CustomerID** ] 方塊中`ALFKI`，輸入，然後按一下 [**訂單歷程記錄**]。

     出現的訊息方塊會列出客戶 ALFKI 的訂單記錄。

     按一下 **[確定]** 關閉訊息方塊。

4. 在 [**輸入訂單**] 方塊中`123`，輸入，然後按一下 [**訂單詳細資料**]。

     出現的訊息方塊會顯示 "No results."

     按一下 **[確定]** 關閉訊息方塊。

5. 在 [**調試**] 功能表上，按一下 [**停止調試**]。

     偵錯工作階段 (Session) 隨即關閉。

6. 如果您已完成實驗，您可以**按一下 [檔案**] 功能表上的 [**關閉專案**]，並在出現提示時儲存專案。

## <a name="next-steps"></a>後續步驟

您可以進行一些變更，以強化這個專案。 例如，您可以在清單方塊中列出可用的預存程序，讓使用者選取所要執行的程序。 您也可以將報表輸出送至文字檔。

## <a name="see-also"></a>另請參閱

- [依逐步解說學習](learning-by-walkthroughs.md)
- [預存程序](stored-procedures.md)
