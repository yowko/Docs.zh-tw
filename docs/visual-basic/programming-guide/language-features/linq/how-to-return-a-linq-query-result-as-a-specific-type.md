---
title: 如何：將 LINQ 查詢結果當做特定類型傳回
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: c8ed792bf3ffefd903d60522f621958e44546d32
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404948"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>如何：將 LINQ 查詢結果當做特定類型傳回 (Visual Basic)
語言整合式查詢（LINQ）可讓您輕鬆地存取資料庫資訊並執行查詢。 根據預設，LINQ 查詢會傳回物件的清單做為匿名型別。 您也可以使用子句，指定查詢傳回特定類型的清單 `Select` 。  
  
 下列範例示範如何建立新的應用程式，以對 SQL Server 資料庫執行查詢，並將結果投射為特定的命名類型。 如需詳細資訊，請參閱[匿名型別](../objects-and-classes/anonymous-types.md)和[Select 子句](../../../language-reference/queries/select-clause.md)。  
  
 本主題中的範例會使用 Northwind 範例資料庫。 如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。 如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>建立資料庫的連接  
  
1. 在 Visual Studio 中， **Server Explorer** / **Database Explorer**按一下**Server Explorer** / [ **View** ] 功能表上的 [伺服器總管**資料庫總管**] 來開啟伺服器總管資料庫總管。  
  
2. 以滑鼠右鍵按一下**伺服器總管**資料庫總管中的 [**資料連線**] / **Database Explorer** ，然後按一下 [**新增連接**]。  
  
3. 請指定與 Northwind 範例資料庫的有效連接。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>若要加入包含 LINQ to SQL 檔案的專案  
  
1. **在 Visual Studio 的 [檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。 選取 [Visual Basic **Windows Forms 應用程式**] 做為 [專案類型]。  
  
2. 在 [專案]**** 功能表上，按一下 [加入新項目]****。 選取 [ **LINQ to SQL 類別**] 專案範本。  
  
3. 將檔案命名為 `northwind.dbml`。 按一下 [新增] 。 [物件關聯式設計工具（O/R 設計工具）] 會針對 northwind .dbml 檔案開啟。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>若要將資料表加入至 O/R 設計工具以進行查詢  
  
1. 在**伺服器總管** / **資料庫總管**中，展開 Northwind 資料庫的連接。 展開 **[資料表]** 資料夾。  
  
     如果您已經關閉 O/R 設計工具，可以按兩下先前加入的 northwind 檔案來重新開啟它。  
  
2. 按一下 [Customers] 資料表，並將它拖曳至設計工具的左窗格。  
  
     設計工具會為您的專案建立新的 `Customer` 物件。 您可以將查詢結果投影為 `Customer` 類型，或做為您所建立的類型。 這個範例會在稍後的程式中建立新的型別，並將查詢結果投影為該型別。  
  
3. 儲存您的變更並關閉設計工具。  
  
4. 儲存您的專案。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>若要加入程式碼以查詢資料庫並顯示結果  
  
1. 從 [**工具箱**] 中，將 <xref:System.Windows.Forms.DataGridView> 控制項拖曳至專案的預設 Windows Form （Form1）。  
  
2. 按兩下 [Form1] 以修改 Form1 類別。  
  
3. 在 `End Class` Form1 類別的語句後面，加入下列程式碼來建立類型， `CustomerInfo` 以保存此範例的查詢結果。  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. 當您將資料表加入至 O/R 設計工具時，設計工具會將 <xref:System.Data.Linq.DataContext> 物件加入至您的專案。 這個物件包含存取這些資料表所需的程式碼，以及存取每個資料表的個別物件和集合。 <xref:System.Data.Linq.DataContext>專案的物件會根據 .dbml 檔案的名稱來命名。 針對此專案， <xref:System.Data.Linq.DataContext> 物件的名稱為 `northwindDataContext` 。  
  
     您可以 <xref:System.Data.Linq.DataContext> 在程式碼中建立的實例，並查詢 O/R 設計工具所指定的資料表。  
  
     在 `Load` Form1 類別的事件中，加入下列程式碼來查詢公開為數據內容屬性的資料表。 `Select`查詢的子句會 `CustomerInfo` 針對查詢結果的每個專案，建立新的類型，而不是匿名型別。  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. 按 F5 執行您的專案並查看結果。  
  
## <a name="see-also"></a>另請參閱

- [LINQ](index.md)
- [查詢](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataCoNtext 方法（O/R 設計工具）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
