---
title: 如何：使用 LINQ 查詢資料庫 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: f17e0dc6956c5465f8269562705eb0f754f1585c
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827257"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a>如何：使用 LINQ 查詢資料庫 (Visual Basic)
Language Integrated Query (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。  
  
 下列範例會示範如何建立新的應用程式，會對 SQL Server 資料庫執行查詢。  
  
 本主題中的範例使用 Northwind 範例資料庫。 如果您在開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。 如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a>若要建立資料庫的連接  
  
1.  在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。  
  
2.  以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下 **加入連接**。  
  
3.  指定有效的連接至 Northwind 範例資料庫。  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>包含 LINQ to SQL 檔案加入專案  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。 選取 Visual Basic **Windows Forms 應用程式**專案類型。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。 選取**LINQ to SQL 類別**項目範本。  
  
3.  將檔案命名為 `northwind.dbml`。 按一下 [加入] 。 物件關聯式設計工具 （O/R 設計工具） 會開啟 northwind.dbml 檔案。  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a>若要將資料表加入至查詢至 O/R 設計工具  
  
1.  在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。 展開**資料表**資料夾。  
  
     如果您關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。  
  
2.  按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。 按一下 [Orders] 資料表，並將它拖曳至設計工具的左窗格。  
  
     在設計工具建立新`Customer`和`Order`專案物件。 請注意，設計工具會自動偵測資料表之間的關聯性建立子系相關物件的屬性。 例如，IntelliSense 會顯示`Customer`物件具有`Orders`該客戶所有訂單的屬性相關。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>加入程式碼以查詢資料庫，並顯示結果  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>到您的專案，Form1 的預設值的 Windows Form 控制項。  
  
2.  按兩下 Form1 以將程式碼加入`Load`表單的事件。  
  
3.  當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>專案物件。 此物件包含的程式碼，您必須存取這些資料表，以及個別的物件和集合每個資料表。 <xref:System.Data.Linq.DataContext>物件針對名為您的專案是根據.dbml 檔案的名稱。 針對此專案，<xref:System.Data.Linq.DataContext>物件命名為`northwindDataContext`。  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼和查詢中的資料表。  
  
     將下列程式碼加入`Load`事件來查詢公開為屬性的資料內容的資料表。  
  
     [!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]  
  
4.  按 F5 執行您的專案，並檢視結果。  
  
5.  以下是一些您可以嘗試的其他查詢：  
  
     [!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]  
    [!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext 方法 （O/R 設計工具）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
