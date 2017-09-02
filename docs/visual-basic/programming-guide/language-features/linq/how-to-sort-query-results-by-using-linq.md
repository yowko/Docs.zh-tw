---
title: "如何︰ 使用 LINQ (Visual Basic) 來排序查詢結果 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6fe1cd6b529e72ad57834ded875b5339c49de69f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a>如何：使用 LINQ 排序查詢結果 (Visual Basic)
語言整合查詢 (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。  
  
 下列範例示範如何建立新的應用程式，以執行針對 SQL Server 資料庫的查詢，並使用以排序結果，您可以多個欄位`Order By`子句。 每個欄位的排序次序可以遞增或遞減順序。 如需詳細資訊，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 本主題中的範例使用 Northwind 範例資料庫。 如果您的開發電腦上沒有 Northwind 範例資料庫，您可以下載從[Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)網站。 如需指示，請參閱[下載範例資料庫](https://msdn.microsoft.com/library/bb399411)。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>若要建立資料庫的連接  
  
1.  在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。  
  
2.  以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**然後按一下 **加入連接**。  
  
3.  指定有效的連接至 Northwind 範例資料庫。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>若要將專案加入包含 LINQ to SQL 檔案  
  
1.  在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。 選取 Visual Basic **Windows Form 應用程式**做為專案類型。  
  
2.  在 [專案] **Walkthrough: Adding Controls to a Worksheet at Run Time in an VSTO Add-in project** 功能表中，按一下 [加入新項目] ****。 選取**LINQ to SQL 類別**項目範本。  
  
3.  將檔案命名`northwind.dbml`。 按一下 [加入] ****。 Northwind.dbml 檔案的開啟物件關聯式設計工具 （O/R 設計工具）。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>若要將資料表加入至查詢至 O/R 設計工具  
  
1.  在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。 展開**資料表**資料夾。  
  
     如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。  
  
2.  按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。 按一下 「 訂單 」 資料表，並將它拖曳至設計工具的左窗格。  
  
     設計工具建立新`Customer`和`Order`物件，為您的專案。 請注意，在設計工具會自動偵測資料表之間的關聯性和建立子物件相關的屬性。 例如，IntelliSense 會顯示，`Customer`物件具有`Orders`該客戶相關的所有訂單的屬性。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>加入程式碼來查詢資料庫，並顯示結果  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到預設的 Windows Form 專案，Form1。</xref:System.Windows.Forms.DataGridView>  
  
2.  按兩下 Form1 加入程式碼以`Load`形式的事件。  
  
3.  當您新增資料表至 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件至您的專案。</xref:System.Data.Linq.DataContext> 此物件包含的程式碼，您必須擁有存取這些資料表，以及存取個別物件和集合的每個資料表。 <xref:System.Data.Linq.DataContext>物件針對您的專案名為基礎的.dbml 檔案名稱。</xref:System.Data.Linq.DataContext> 針對此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。</xref:System.Data.Linq.DataContext>  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼和查詢中的資料表。</xref:System.Data.Linq.DataContext>  
  
     加入下列程式碼以`Load`事件，以查詢公開為屬性的資料內容，並將結果排序的資料表。 查詢的客戶訂單，以遞減順序排序結果。 依公司名稱，以遞增順序 （預設值） 排序具有相同數目的訂單的客戶。  
  
     [!code-vb[VbLINQToSQLHowTos #&10;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-sort-query-results-by-using-linq_1.vb)]  
  
4.  按 F5 執行您的專案，並檢視結果。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)   
 [DataContext 方法 （O/R 設計工具）](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)

