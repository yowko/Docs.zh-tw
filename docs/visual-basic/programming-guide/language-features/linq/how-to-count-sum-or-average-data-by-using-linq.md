---
title: "如何︰ 統計、 加總或平均資料使用 LINQ (Visual Basic) |Microsoft 文件"
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
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
caps.latest.revision: 9
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
ms.openlocfilehash: c5789d9e4bee1388d5ad0368f88fad5c1b6e95cc
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>如何：使用 LINQ 統計、加總或平均資料 (Visual Basic)
語言整合查詢 (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。  
  
 下列範例示範如何建立新的應用程式執行的 SQL Server 資料庫的查詢。 範例計數、 加總，並計算結果平均使用`Aggregate`和`Group By`子句。 如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[By 子句群組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
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
  
3.  當您新增資料表至 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件，為您的專案。</xref:System.Data.Linq.DataContext> 此物件包含的程式碼，您必須擁有存取這些資料表，以及存取個別物件和集合的每個資料表。 <xref:System.Data.Linq.DataContext>物件針對您的專案名為基礎的.dbml 檔案名稱。</xref:System.Data.Linq.DataContext> 針對此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。</xref:System.Data.Linq.DataContext>  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼和查詢中的資料表。</xref:System.Data.Linq.DataContext>  
  
     加入下列程式碼以`Load`事件查詢公開為屬性的資料表您<xref:System.Data.Linq.DataContext>和計數、 加總和結果的平均值。</xref:System.Data.Linq.DataContext> 此範例會使用`Aggregate`子句來查詢單一的結果，而`Group By`子句來顯示平均值分組結果。  
  
     [!code-vb[VbLINQToSQLHowTos #&13;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  按 F5 執行您的專案，並檢視結果。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)   
 [DataContext 方法 （O/R 設計工具）](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Group By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)

