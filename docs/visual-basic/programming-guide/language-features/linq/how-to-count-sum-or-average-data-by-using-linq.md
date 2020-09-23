---
title: 如何：使用 LINQ 統計、加總或平均資料
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 617c6959e2d3add6d36266b0827ef7281b0c77a9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059245"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>如何：使用 LINQ 統計、加總或平均資料 (Visual Basic)

 (LINQ) 的語言整合式查詢，可讓您輕鬆地存取資料庫資訊和執行查詢。  
  
 下列範例示範如何建立新的應用程式，以針對 SQL Server 資料庫執行查詢。 此範例會使用和子句來計數、加總和平均 `Aggregate` 結果 `Group By` 。 如需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md) 和 [group by 子句](../../../language-reference/queries/group-by-clause.md)。  
  
 本主題中的範例會使用 Northwind 範例資料庫。 如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。 如需相關指示，請參閱 [下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>若要建立資料庫的連接  
  
1. 在 Visual Studio 中， **Server Explorer** / 按一下 [View] 功能表上的 [**伺服器總管**資料庫總管來開啟伺服器總管**資料庫總管** / **Database Explorer** 。 **View**  
  
2. 以滑鼠右鍵按一下**伺服器總管**資料庫總管中的 [**資料連線**] / **Database Explorer** ，然後按一下 [**加入連接**]。  
  
3. 請指定與 Northwind 範例資料庫的有效連接。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>若要加入包含 LINQ to SQL 檔案的專案  
  
1. 在 Visual Studio **的 [檔案** ] 功能表上，指向 [ **新增** ]，然後按一下 [ **專案**]。 選取 Visual Basic **Windows Forms 應用程式** 做為專案類型。  
  
2. 在 [專案]**** 功能表上，按一下 [加入新項目]****。 選取 [ **LINQ to SQL 類別** ] 專案範本。  
  
3. 將檔案命名為 `northwind.dbml`。 按一下 [新增]  。 物件關聯式設計工具的 (O/R 設計工具) 會針對 northwind 檔案開啟。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>若要將資料表加入至 O/R 設計工具的查詢  
  
1. 在**伺服器總管** / **資料庫總管**中，展開 Northwind 資料庫的連接。 展開 **[資料表]** 資料夾。  
  
     如果您已關閉 O/R 設計工具，您可以按兩下先前加入的 northwind 檔案來重新開啟它。  
  
2. 按一下 [Customers] 資料表，然後將它拖曳至設計工具的左窗格。 按一下 [Orders] 資料表，然後將它拖曳至設計工具的左窗格。  
  
     設計工具會 `Customer` `Order` 為您的專案建立新的和物件。 請注意，設計工具會自動偵測資料表之間的關聯性，並建立相關物件的子屬性。 例如，IntelliSense 會顯示 `Customer` 物件具有與 `Orders` 該客戶相關之所有訂單的屬性。  
  
3. 儲存您的變更並關閉設計工具。  
  
4. 儲存您的專案。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>加入程式碼以查詢資料庫並顯示結果  
  
1. 從 [ **工具箱**] 中，將 <xref:System.Windows.Forms.DataGridView> 控制項拖曳至專案的預設 Windows 表單（Form1）。  
  
2. 按兩下 [Form1]，將程式碼加入 `Load` 表單的事件中。  
  
3. 當您將資料表加入至 O/R 設計工具時，設計工具會 <xref:System.Data.Linq.DataContext> 為您的專案新增物件。 此物件包含存取這些資料表所需的程式碼，以及存取每個資料表的個別物件和集合。 <xref:System.Data.Linq.DataContext>專案的物件是根據您 .dbml 檔的名稱來命名。 針對此專案， <xref:System.Data.Linq.DataContext> 會將物件命名為 `northwindDataContext` 。  
  
     您可以 <xref:System.Data.Linq.DataContext> 在程式碼中建立的實例，並查詢 O/R 設計工具所指定的資料表。  
  
     將下列程式碼加入至 `Load` 事件，以查詢公開為的屬性、 <xref:System.Data.Linq.DataContext> 計數、總和和平均結果的資料表。 此範例會使用 `Aggregate` 子句來查詢單一結果，以及使用 `Group By` 子句來顯示群組結果的平均值。  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. 按 F5 執行您的專案，並查看結果。  
  
## <a name="see-also"></a>另請參閱

- [LINQ](index.md)
- [查詢](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md)
- [Group By 子句](../../../language-reference/queries/group-by-clause.md)
