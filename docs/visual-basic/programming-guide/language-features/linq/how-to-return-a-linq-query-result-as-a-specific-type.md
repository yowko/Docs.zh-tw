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
ms.openlocfilehash: e0b7e402fba4fb51afb60ad0ae7698bd4947b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>如何：將 LINQ 查詢結果當做特定類型傳回 (Visual Basic)
Language Integrated Query (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。 根據預設，LINQ 查詢會傳回做為匿名類型的物件清單。 您也可以指定查詢傳回特定型別的清單，使用`Select`子句。  
  
 下列範例會示範如何建立新的應用程式，會對 SQL Server 資料庫執行查詢，並規劃成特定的具名類型的結果。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)和[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
 本主題中的範例使用 Northwind 範例資料庫。 如果您在開發電腦上沒有 Northwind 範例資料庫，您可以下載從[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088)網站。 如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>若要建立資料庫的連接  
  
1.  在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。  
  
2.  以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下 **加入連接**。  
  
3.  指定有效的連接至 Northwind 範例資料庫。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>包含 LINQ to SQL 檔案加入專案  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。 選取 Visual Basic **Windows Forms 應用程式**專案類型。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。 選取**LINQ to SQL 類別**項目範本。  
  
3.  將檔案命名為 `northwind.dbml`。 按一下 [加入] 。 物件關聯式設計工具 （O/R 設計工具） 會開啟 northwind.dbml 檔案。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>若要將資料表加入至查詢至 O/R 設計工具  
  
1.  在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。 展開**資料表**資料夾。  
  
     如果您關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。  
  
2.  按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。  
  
     在設計工具建立新`Customer`專案物件。 您可以投影查詢結果為`Customer`類型或為您建立的型別。 此範例會在稍後的程序中建立新的類型和專案做為該類型的查詢結果。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>加入程式碼以查詢資料庫，並顯示結果  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>到您的專案，Form1 的預設值的 Windows Form 控制項。  
  
2.  按兩下 Form1 以修改要屬於 Form1 類別。  
  
3.  之後`End Class`Form1 類別的陳述式加入下列程式碼，以建立`CustomerInfo`來容納此範例的查詢結果的類型。  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件加入專案。 此物件包含的程式碼，您必須擁有存取這些資料表，以及存取個別的物件和集合每個資料表。 <xref:System.Data.Linq.DataContext>物件針對名為您的專案是根據.dbml 檔案的名稱。 針對此專案，<xref:System.Data.Linq.DataContext>物件命名為`northwindDataContext`。  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼和查詢中的資料表。  
  
     在`Load`事件要屬於 Form1 類別，加入下列程式碼來查詢公開為屬性的資料內容的資料表。 `Select`會建立新的查詢子句`CustomerInfo`型別，而不是每個項目查詢結果的匿名型別。  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  按 F5 執行您的專案，並檢視結果。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext 方法 （O/R 設計工具）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
