---
title: 如何：使用 LINQ 尋找查詢結果中的最小或最大值
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112358"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>如何：使用 LINQ 尋找查詢結果中的最小或最大值 (Visual Basic)
語言集成查詢 （LINQ） 使訪問資料庫資訊和執行查詢變得容易。  
  
 下面的示例演示如何創建執行針對 SQL Server 資料庫的查詢的新應用程式。 該示例通過使用`Aggregate`和`Group By`子句確定結果的最小值和最大值。 有關詳細資訊，請參閱[聚合子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[按子句分組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
 本主題中的示例使用北風示例資料庫。 如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。 有關說明，請參閱[下載示例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>創建與資料庫的連接  
  
1. 在視覺化工作室中，通過按一下 **"視圖"** 功能表上**的伺服器資源管理器**/**資料庫資源管理器**打開**伺服器資源管理器**/**資料庫資源管理器**。  
  
2. 按右鍵**伺服器資源管理器**/**資料庫資源管理器**中**的資料連線**，然後按一下"**添加連接**"。  
  
3. 指定到北風樣本資料庫的有效連接。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>將包含 LINQ 的專案添加到 SQL 檔  
  
1. 在視覺化工作室中，在 **"檔"** 功能表上，指向 **"新建"，** 然後按一下"**專案**"。 選擇視覺化基本**視窗表單應用程式**作為專案類型。  
  
2. 在 [專案]**** 功能表上，按一下 [加入新項目]****。 選擇**LINQ 到 SQL 類**項範本。  
  
3. 開啟 `northwind.dbml` 檔案。 按一下 **[新增]**。 為北風.dbml 檔打開物件關係設計器（O/R 設計器）。  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>將表添加到 O/R 設計器  
  
1. 在**伺服器資源管理器**/**資料庫資源管理器中**，展開與北風資料庫的連接。 展開 **[資料表]** 資料夾。  
  
     如果已關閉 O/R 設計器，則可以通過按兩下之前添加的 Northwind.dbml 檔重新打開它。  
  
2. 按一下"客戶"表並將其拖動到設計器的左側窗格。 按一下"訂單"表並將其拖動到設計器的左側窗格。  
  
     設計器為專案`Customer`創建新`Order`物件和物件。 請注意，設計器會自動檢測表之間的關係，並為相關物件創建子屬性。 例如，IntelliSense 將顯示`Customer`該物件具有與該客戶`Orders`相關的所有訂單的屬性。  
  
3. 保存更改並關閉設計器。  
  
4. 儲存您的專案。  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>添加代碼以查詢資料庫並顯示結果  
  
1. 從**工具箱**中<xref:System.Windows.Forms.DataGridView>，將控制項拖動到專案的預設 Windows 表單表單 Form1。  
  
2. 按兩下 Form1 可向表單`Load`的事件添加代碼。  
  
3. 將表添加到 O/R 設計器時，設計器會<xref:System.Data.Linq.DataContext>為專案添加物件。 除了每個表的各個物件和集合之外，此物件還包含訪問這些表必須具有的代碼。 專案<xref:System.Data.Linq.DataContext>的物件是根據 .dbml 檔的名稱命名的。 對於此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。  
  
     您可以在代碼中創建 的<xref:System.Data.Linq.DataContext>實例，並查詢 O/R 設計器指定的表。  
  
     將以下代碼添加到事件`Load`。 此代碼查詢作為資料上下文的屬性公開的表，並確定結果的最小值和最大值。 該示例使用`Aggregate`子句查詢單個結果，`Group By`子句顯示分組結果的平均值。  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. 按**F5**運行專案並查看結果。  
  
## <a name="see-also"></a>另請參閱

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [資料上下文方法（O/R 設計器）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
