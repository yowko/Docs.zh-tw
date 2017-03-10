---
title: "How to: Query a Database by Using LINQ (Visual Basic) | Microsoft Docs"
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
  - "query samples [LINQ]"
  - "database querying [LINQ]"
  - "queries [LINQ in Visual Basic], database querying"
  - "querying databases [LINQ]"
  - "queries [LINQ in Visual Basic], how-to topics"
  - "query samples [Visual Basic]"
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Query a Database by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Language\-Integrated Query \(LINQ\) 可讓您輕鬆地存取資料庫資訊和執行查詢。  
  
 下列範例顯示如何建立新的應用程式，對 SQL Server 資料庫執行查詢。  
  
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
  
2.  按一下 \[Customers\] 資料表，將它拖曳至設計工具的左窗格。  按一下 \[Orders\] 資料表，將它拖曳至設計工具的左窗格。  
  
     設計工具會為您的專案建立新的 `Customer` 和 `Order` 物件。  請注意，設計工具會自動偵測資料表之間的關聯，並建立關聯物件的子屬性。  例如，IntelliSense 會顯示 `Customer` 物件針對與該客戶相關的所有訂單有一個 `Orders` 屬性。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### 若要加入程式碼以查詢資料庫並顯示結果  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.DataGridView> 控制項拖曳至專案的預設 Windows Form 上 \(Form1\)。  
  
2.  按兩下 Form1，將程式碼加入至表單的 `Load` 事件。  
  
3.  當您將資料表加入至 O\/R 設計工具時，設計工具會為專案加入 <xref:System.Data.Linq.DataContext> 物件。  本物件內含的程式碼，您必須擁有才能存取這些資料表，以及個別物件和每一個資料表的集合。  專案的 <xref:System.Data.Linq.DataContext> 物件是根據 .dbml 檔案的名稱命名的。  在這個專案中，<xref:System.Data.Linq.DataContext> 物件命名為 `northwindDataContext`。  
  
     您可以在程式碼中建立 <xref:System.Data.Linq.DataContext> 的執行個體，並查詢 O\/R 設計工具所指定的資料表。  
  
     將下列程式碼加入至 `Load` 事件以查詢公開 \(Expose\) 為資料內容屬性的表格。  
  
     [!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form2.vb#3)]  
  
4.  按下 F5 執行專案並檢視結果。  
  
5.  以下是您可以嘗試的一些額外查詢：  
  
     [!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form2.vb#4)]  
    [!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form2.vb#5)]  
  
## 請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext 方法 \(O\/R 設計工具\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)