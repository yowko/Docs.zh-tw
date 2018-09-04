---
title: 如何：將 LINQ 查詢結果當做特定類型傳回 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 720660153cb357c11168ab45ebf8343559faf82a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514281"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>如何：將 LINQ 查詢結果當做特定類型傳回 (Visual Basic)
Language Integrated Query (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。 根據預設，LINQ 查詢會傳回非匿名型別物件的清單。 您也可以指定查詢傳回特定型別的清單，使用`Select`子句。  
  
 下列範例示範如何建立新的應用程式會執行對 SQL Server 資料庫的查詢，並將結果投射成特定的具名類型。 如需詳細資訊，請參閱 <<c0> [ 匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)並[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
 本主題中的範例使用 Northwind 範例資料庫。 如果您的開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。 如需相關指示，請參閱 <<c0> [ 下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>若要建立資料庫的連接  
  
1.  在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫檔案總管**上**檢視**功能表。  
  
2.  以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下**加入連接**。  
  
3.  請指定有效的連接至 Northwind 範例資料庫。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>若要將專案加入包含 LINQ to SQL 檔案  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。 選取 Visual Basic **Windows Forms 應用程式**作為專案類型。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。 選取  **LINQ to SQL 類別**項目範本。  
  
3.  將檔案命名為 `northwind.dbml`。 按一下 [加入] 。 Northwind.dbml 檔案會開啟 物件關聯式設計工具 （O/R 設計工具）。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>若要將資料表加入至查詢至 O/R 設計工具  
  
1.  在 **伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。 依序展開**資料表**資料夾。  
  
     如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。  
  
2.  按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。  
  
     設計工具建立新`Customer`物件，為您的專案。 您可以投影查詢結果當做`Customer`類型或為您建立的型別。 此範例會在稍後的程序中建立新的類型，並在投射查詢結果為該型別。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>加入程式碼來查詢資料庫，並顯示結果  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到您的專案，Form1 的預設 Windows 表單。  
  
2.  按兩下 Form1 以修改，在 Form1 類別。  
  
3.  在後`End Class`陳述式，在 Form1 類別，新增下列程式碼，以建立`CustomerInfo`保存此範例的查詢結果的型別。  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件加入專案。 此物件包含的程式碼，您必須擁有存取這些資料表，以及存取個別的物件和每個資料表的集合。 <xref:System.Data.Linq.DataContext>物件您專案的名稱為根據的.dbml 檔案的名稱。 此專案而言<xref:System.Data.Linq.DataContext>物件會命名為`northwindDataContext`。  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>資料表指定 O/R 設計工具在您的程式碼和查詢。  
  
     在 `Load`事件，在 Form1 類別，新增下列程式碼來查詢公開為屬性的資料內容的資料表。 `Select`會建立新的查詢子句`CustomerInfo`類型而不是每個項目查詢結果的匿名型別。  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  按 F5 執行您的專案，並檢視結果。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [查詢](../../../../visual-basic/language-reference/queries/index.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
