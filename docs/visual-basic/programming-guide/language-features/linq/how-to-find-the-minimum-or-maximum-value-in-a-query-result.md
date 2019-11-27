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
ms.openlocfilehash: bddb90baa0b01fd9d724583b472af9f9fa7569e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344971"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>如何：使用 LINQ 尋找查詢結果中的最小或最大值 (Visual Basic)
語言整合式查詢（LINQ）可讓您輕鬆地存取資料庫資訊並執行查詢。  
  
 下列範例示範如何建立新的應用程式，以對 SQL Server 資料庫執行查詢。 此範例會使用 `Aggregate` 和 `Group By` 子句來決定結果的最小和最大值。 如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[Group by 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
 本主題中的範例會使用 Northwind 範例資料庫。 如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。 如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>建立資料庫的連接  
  
1. 在 Visual Studio 中，按一下 [**視圖**]**功能表上的**[**伺服器總管**/資料庫總管]，開啟**伺服器總管**/**資料庫總管**。  
  
2. 以滑鼠右鍵按一下**伺服器總管**/**資料庫總管**中的 [**資料連線**]，然後按一下 [**新增連接**]。  
  
3. 請指定與 Northwind 範例資料庫的有效連接。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>若要加入包含 LINQ to SQL 檔案的專案  
  
1. 在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。 選取 [Visual Basic **Windows Forms 應用程式**] 做為 [專案類型]。  
  
2. 在 [專案] 功能表中，按一下 [加入新項目]。 選取 [ **LINQ to SQL 類別**] 專案範本。  
  
3. 將檔案命名為 `northwind.dbml`。 按一下 [加入]。 [物件關聯式設計工具（O/R 設計工具）] 會針對 northwind .dbml 檔案開啟。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>若要將資料表加入至 O/R 設計工具以進行查詢  
  
1. 在**伺服器總管**/**資料庫總管**中，展開 Northwind 資料庫的連接。 展開 [**資料表]** 資料夾。  
  
     如果您已經關閉 O/R 設計工具，可以按兩下先前加入的 northwind 檔案來重新開啟它。  
  
2. 按一下 [Customers] 資料表，並將它拖曳至設計工具的左窗格。 按一下 [Orders] 資料表，並將它拖曳至設計工具的左窗格。  
  
     設計工具會為您的專案建立新的 `Customer` 和 `Order` 物件。 請注意，設計工具會自動偵測資料表之間的關聯性，並建立相關物件的子屬性。 例如，IntelliSense 會顯示 `Customer` 物件具有與該客戶相關之所有訂單的 `Orders` 屬性。  
  
3. 儲存您的變更並關閉設計工具。  
  
4. 儲存您的專案。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>若要加入程式碼以查詢資料庫並顯示結果  
  
1. 從 [**工具箱**] 中，將 [<xref:System.Windows.Forms.DataGridView>] 控制項拖曳至您的專案 [Form1] 的預設 Windows Form。  
  
2. 按兩下 [Form1]，將程式碼加入表單的 `Load` 事件。  
  
3. 當您將資料表加入至 O/R 設計工具時，設計工具會為您的專案加入 <xref:System.Data.Linq.DataContext> 物件。 除了每個資料表的個別物件和集合之外，此物件還包含存取這些資料表所需的程式碼。 專案的 <xref:System.Data.Linq.DataContext> 物件是根據 .dbml 檔案的名稱來命名。 針對此專案，<xref:System.Data.Linq.DataContext> 物件的名稱為 `northwindDataContext`。  
  
     您可以在程式碼中建立 <xref:System.Data.Linq.DataContext> 的實例，並查詢 O/R 設計工具所指定的資料表。  
  
     將下列程式碼新增至 `Load` 事件。 這段程式碼會查詢公開為數據內容屬性的資料表，並決定結果的最小值和最大值。 此範例會使用他的 `Aggregate` 子句來查詢單一結果，而 `Group By` 子句會顯示群組結果的平均值。  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. 按 F5 執行您的專案並查看結果。  
  
## <a name="see-also"></a>請參閱

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
