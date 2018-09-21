---
title: 如何：使用 LINQ 呼叫預存程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 50a4dff90dc1ce02869978f1da147e530cefc3e1
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525603"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>如何：使用 LINQ 呼叫預存程序 (Visual Basic)
Language Integrated Query (LINQ) 可讓您更容易存取的資料庫資訊，包括資料庫物件，例如預存程序。  
  
 下列範例示範如何建立 SQL Server 資料庫中呼叫預存程序的應用程式。 此範例示範如何呼叫資料庫中的兩個不同的預存程序。 每個程序會傳回查詢的結果。 一個程序會使用輸入的參數，並在其他程序不接受參數。  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>若要將預存程序加入至 O/R 設計工具  
  
1.  在 **伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。 依序展開**預存程序**資料夾。  
  
     如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。  
  
2.  按一下 **依年份銷售**預存程序，並將它拖曳至設計工具的右窗格。 按一下  **Ten Most Expensive Products**預存程序將它拖曳至設計工具的右窗格。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>加入程式碼以顯示預存程序的結果  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到您的專案，Form1 的預設 Windows 表單。  
  
2.  按兩下 Form1 以將程式碼加入其`Load`事件。  
  
3.  當您加入預存程序至 O/R 設計工具時，設計工具便會加入<xref:System.Data.Linq.DataContext>物件，為您的專案。 此物件包含的程式碼，您必須存取這些程序。 <xref:System.Data.Linq.DataContext>物件的專案命名為根據的.dbml 檔案名稱。 此專案而言<xref:System.Data.Linq.DataContext>物件會命名為`northwindDataContext`。  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>在您的程式碼，並呼叫預存程序方法指定 O/R 設計工具。 繫結至<xref:System.Windows.Forms.DataGridView>物件，您可能要強制立即執行，藉由呼叫查詢<xref:System.Linq.Enumerable.ToList%2A>的預存程序結果的方法。  
  
     將下列程式碼加入`Load`呼叫其中一個做為資料內容的方法公開預存程序的事件。  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  按 F5 執行您的專案，並檢視結果。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [查詢](../../../../visual-basic/language-reference/queries/index.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
