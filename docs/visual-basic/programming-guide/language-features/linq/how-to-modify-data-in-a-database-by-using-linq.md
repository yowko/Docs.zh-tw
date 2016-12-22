---
title: "How to: Modify Data in a Database by Using LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "inserting rows [LINQ to SQL]"
  - "deleting rows [LINQ to SQL]"
  - "updating rows [LINQ to SQL]"
  - "inserting data [Visual Basic]"
  - "deleting data"
  - "data [Visual Basic], updating"
  - "updating data [LINQ]"
  - "queries [LINQ in Visual Basic], data changes in database"
  - "queries [LINQ in Visual Basic], how-to topics"
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Modify Data in a Database by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Language\-Integrated Query \(LINQ\) 查詢可讓您輕鬆地存取資料庫資訊及修改資料庫中的值。  
  
 下列範例顯示如何建立新的應用程式，用來擷取並更新 SQL Server 資料庫中的資訊。  
  
 本主題中的範例使用 Northwind 範例資料庫。  如果您的開發電腦上沒有 Northwind 範例資料庫，可以從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088) \(英文\) 網站下載。  如需相關說明，請參閱[下載範例資料庫](../Topic/Downloading%20Sample%20Databases.md)。  
  
### 若要建立連接至資料庫  
  
1.  在 Visual Studio 中，按一下 \[**檢視**\] 功能表，然後選取 \[**伺服器總管**\]\/\[**資料庫總管**\]，以開啟 \[**伺服器總管**\]\/\[**資料庫總管**\]。  
  
2.  以滑鼠右鍵按一下 \[**伺服器總管**\]\/\[**資料庫總管**\] 中的 \[**資料連接**\]，然後按一下 \[**加入連接**\]。  
  
3.  指定至 Northwind 範例資料庫的有效連接。  
  
### 若要加入含有 LINQ to SQL 檔案的專案  
  
1.  在 Visual Studio 的 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  選取 Visual Basic \[**Windows Form 應用程式**\] 為專案類型。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  選取 \[**LINQ to SQL 類別**\] 項目範本。  
  
3.  將檔案命名為 `northwind.dbml`。  按一下 \[**加入**\]。  `northwind.dbml` 檔案會開啟物件關聯式設計工具 \(O\/R 設計工具\)。  
  
### 若要加入資料表以對設計工具進行查詢及修改  
  
1.  在 \[**伺服器總管**\]\/\[**資料庫總管**\] 中，展開 Northwind 資料庫的連接。  展開 \[**資料表**\] 資料夾。  
  
     如果您關閉了 O\/R 設計工具，可以按兩下您稍早加入的 `northwind.dbml` 檔案以重新開啟。  
  
2.  按一下 \[Customers\] 資料表，將它拖曳至設計工具的左窗格。  
  
     設計工具會為您的專案建立新的 Customer 物件。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### 若要加入程式碼以修改資料庫並顯示結果  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.DataGridView> 控制項拖曳至專案的預設 Windows Form 上 \(Form1\)。  
  
2.  當您將資料表加入至 O\/R 設計工具時，設計工具會將 <xref:System.Data.Linq.DataContext> 物件加入至您的專案。  這個物件包含您可以用來存取 Customers 資料表的程式碼。  也包含用來定義資料表之區域 Customer 物件及 Customers 集合的程式碼。  專案的 <xref:System.Data.Linq.DataContext> 物件是根據 .dbml 檔案的名稱命名的。  在這個專案中，<xref:System.Data.Linq.DataContext> 物件命名為 `northwindDataContext`。  
  
     您可以在程式碼中建立 <xref:System.Data.Linq.DataContext> 物件的執行個體 \(Instance\)，並查詢及修改 O\/R 設計工具指定的 Customers 集合。  您對 Customers 集合所做的變更，在您呼叫 <xref:System.Data.Linq.DataContext> 物件的 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 方法送出變更之前，都不會反映在資料庫中。  
  
     按兩下 Windows Form 的 Form1，將程式碼加入至 <xref:System.Windows.Forms.Form.Load> 事件以查詢公開為 <xref:System.Data.Linq.DataContext> 之屬性的 Customers 資料表。  加入以下程式碼：  
  
    ```vb#  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  從 \[**工具箱**\] 將三個 <xref:System.Windows.Forms.Button> 控制項拖曳到表單上。  選取第一個 `Button` 控制項。  在 \[**屬性**\] 視窗中，將 `Button` 控制項的 `Name` 設定為 `AddButton`，並將 `Text` 設定為 `Add`。  選取第二個按鈕並將 `Name` 屬性設定為 `UpdateButton`，以及將 `Text` 屬性設定為 `Update`。  選取第三個按鈕並將 `Name` 屬性設定為 `DeleteButton` 以及將 `Text` 屬性設定為 `Delete`。  
  
4.  按兩下 \[**Add**\] 按鈕將程式碼加入至其 `Click` 事件。  加入以下程式碼：  
  
    ```vb#  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  按兩下 \[**Update**\] 按鈕將程式碼加入至其 `Click` 事件。  加入以下程式碼：  
  
    ```vb#  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  按兩下 \[**Delete**\] 按鈕將程式碼加入至其 `Click` 事件。  加入以下程式碼：  
  
    ```vb#  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  請按 F5 執行您的專案。  按一下 \[**Add**\] 以加入新記錄。  按一下 \[**Update**\] 以修改新記錄。  按一下 \[**Delete**\] 以刪除新記錄。  
  
## 請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext 方法 \(O\/R 設計工具\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)