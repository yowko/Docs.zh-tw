---
title: "How to: Call a Stored Procedure by Using LINQ (Visual Basic) | Microsoft Docs"
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
  - "queries [LINQ in Visual Basic], stored procedure calls"
  - "stored procedures sample [Visual Basic]"
  - "stored procedures [LINQ to SQL]"
  - "queries [LINQ in Visual Basic], how-to topics"
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Call a Stored Procedure by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Language\-Integrated Query \(LINQ\) 可讓您輕鬆地存取資料庫資訊，包括預存程序 \(Stored Procedure\) 等資料庫物件。  
  
 下列範例顯示如何建立應用程式來呼叫 SQL Server 資料庫中的預存程序。  這個範例顯示如何呼叫資料庫中兩個不同的預存程序。  每個程序都會傳回查詢結果。  一個程序接受輸入參數，另一個程序則不接受參數。  
  
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
  
### 若要將預存程序加入至 O\/R Designer  
  
1.  在 \[**伺服器總管**\]\/\[**資料庫總管**\] 中，展開 Northwind 資料庫的連接。  展開 \[**預存程序**\] 資料夾。  
  
     如果您關閉了 O\/R 設計工具，可以按兩下您稍早加入的 northwind.dbml 檔案以重新開啟。  
  
2.  按一下 \[**Sales by Year**\] 預存程序並將它拖曳至設計工具的右窗格。  按一下 \[**Ten Most Expensive Products**\] 預存程序並將它拖曳至設計工具的右窗格。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### 若要加入程式碼以顯示預存程序的結果  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.DataGridView> 控制項拖曳至專案的預設 Windows Form 上 \(Form1\)。  
  
2.  按兩下 Form1，將程式碼加入至它的 `Load` 事件。  
  
3.  當您將預存工具加入至 O\/R Designer 時，設計工具會為專案加入 <xref:System.Data.Linq.DataContext> 物件。  這個物件包含存取上述程序所需的程式碼。  專案的 <xref:System.Data.Linq.DataContext> 物件是根據 .dbml 檔案的名稱命名的。  在這個專案中，<xref:System.Data.Linq.DataContext> 物件命名為 `northwindDataContext`。  
  
     您可以在程式碼中建立 <xref:System.Data.Linq.DataContext> 的執行個體 \(Instance\)，並呼叫 O\/R Designer 所指定的預存程序方法。  若要繫結至 <xref:System.Windows.Forms.DataGridView> 物件，您可能必須對預存程序的結果呼叫 <xref:System.Linq.Enumerable.ToList%2A> 方法，強制查詢立即執行。  
  
     將下列程式碼加入至 `Load` 事件，以呼叫上述其中一個以您資料內容之方法公開 \(Expose\) 的預存程序。  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  按下 F5 執行專案並檢視結果。  
  
## 請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext 方法 \(O\/R 設計工具\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)