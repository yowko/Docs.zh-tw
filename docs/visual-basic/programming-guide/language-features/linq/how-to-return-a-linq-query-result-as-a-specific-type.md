---
title: "How to: Return a LINQ Query Result as a Specific Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [LINQ in Visual Basic], specific type returned"
  - "projection [LINQ in Visual Basic]"
  - "anonymous types [Visual Basic]"
  - "querying databases [LINQ]"
  - "queries [LINQ in Visual Basic], how-to topics"
  - "query samples [Visual Basic]"
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# How to: Return a LINQ Query Result as a Specific Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Language\-Integrated Query \(LINQ\) 可讓您輕鬆地存取資料庫資訊和執行查詢。  根據預設，LINQ 查詢會以匿名型別傳回物件的清單。  您也可以使用 `Select` 子句，指定要讓查詢傳回特定型別的清單。  
  
 下列範例顯示如何建立新的應用程式，而該應用程式會對 SQL Server 資料庫執行查詢，並以特定具名型別投射結果。  如需詳細資訊，請參閱[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)和 [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
 本主題中的範例使用 Northwind 範例資料庫。  如果您的開發電腦上沒有 Northwind 範例資料庫，可以從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088) \(英文\) 網站下載。  如需相關說明，請參閱[下載範例資料庫](../Topic/Downloading%20Sample%20Databases.md)。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要建立連接至資料庫  
  
1.  在 Visual Studio 中，按一下 \[**檢視**\] 功能表上的 \[**伺服器總管**\]\/\[**資料庫總管**\]，以開啟 \[**伺服器總管**\]\/\[**資料庫總管**\]。  
  
2.  以滑鼠右鍵按一下 \[**伺服器總管**\]\/\[**資料庫總管**\] 中的 \[**資料連接**\]，然後按一下 \[**加入連接**\]。  
  
3.  指定至 Northwind 範例資料庫的有效連接。  
  
### 若要加入內含 LINQ to SQL 檔案的專案  
  
1.  在 Visual Studio 的 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  選取 Visual Basic \[**Windows Form 應用程式**\] 為專案類型。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  選取 \[**LINQ to SQL 類別**\] 項目範本。  
  
3.  將檔案命名為 `northwind.dbml`。  按一下 \[**加入**\]。  系統會針對 northwind.dbml 檔案開啟物件關聯式設計工具 \(O\/R 設計工具\)。  
  
### 若要將資料表加入至 O\/R 設計工具的查詢  
  
1.  在 \[**伺服器總管**\]\/\[**資料庫總管**\] 中，展開 Northwind 資料庫的連接。  展開 \[**資料表**\] 資料夾。  
  
     如果您關閉了 O\/R 設計工具，可以按兩下您稍早加入的 northwind.dbml 檔案以重新開啟。  
  
2.  按一下 \[Customers\] 資料表，將它拖曳至設計工具的左窗格。  
  
     設計工具會為您的專案建立新的 `Customer` 物件。  您可以用 `Customer` 型別或您所建立的型別來投射查詢結果。  這個範例會在稍後程序中建立新的型別並以該型別投射查詢結果。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### 若要加入程式碼以查詢資料庫並顯示結果  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.DataGridView> 控制項拖曳至專案的預設 Windows Form 上 \(Form1\)。  
  
2.  按兩下 Form1 以修改 Form1 類別 \(Class\)。  
  
3.  在 Form1 類別的 `End Class` 陳述式之後加入下列程式碼，以為這個範例建立用來存放查詢結果的 `CustomerInfo` 型別。  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  當您將資料表加入至 O\/R 設計工具時，設計工具會將 <xref:System.Data.Linq.DataContext> 物件加入至您的專案。  本物件內含的程式碼，您必須擁有才能存取這些資料表，以及個別物件和每一個資料表的集合。  專案的 <xref:System.Data.Linq.DataContext> 物件是根據 .dbml 檔案的名稱命名的。  在這個專案中，<xref:System.Data.Linq.DataContext> 物件命名為 `northwindDataContext`。  
  
     您可以在程式碼中建立 <xref:System.Data.Linq.DataContext> 的執行個體，並查詢 O\/R 設計工具所指定的資料表。  
  
     在 Form1 類別的 `Load` 事件中加入下列程式碼，查詢以您的資料內容之屬性公開 \(Expose\) 的資料表。  查詢的 `Select` 子句會針對查詢結果中的每個項目建立新的 `CustomerInfo` 型別，而不是匿名型別。  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  按下 F5 執行專案並檢視結果。  
  
## 請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext 方法 \(O\/R 設計工具\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)