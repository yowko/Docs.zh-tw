---
title: "如何：使用 LINQ 修改資料庫中的資料 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69e2fc7a6860ad2ff43742d37cd35671ebe35acf
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>如何：使用 LINQ 修改資料庫中的資料 (Visual Basic)
Language Integrated Query (LINQ) 查詢，讓您輕鬆存取資料庫的資訊，並修改資料庫中的值。  
  
 下列範例顯示如何建立新的應用程式擷取和更新資訊的 SQL Server 資料庫中。  
  
 本主題中的範例使用 Northwind 範例資料庫。 如果您在開發電腦上沒有 Northwind 範例資料庫，您可以下載從[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088)網站。 如需指示，請參閱[下載範例資料庫](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
### <a name="to-create-a-connection-to-a-database"></a>若要建立資料庫的連接  
  
1.  在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**檢視** 功能表，然後選取**伺服器總管**/**資料庫總管**。  
  
2.  以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下**加入連接**。  
  
3.  指定有效的連接至 Northwind 範例資料庫。  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>若要加入在專案中的使用 LINQ to SQL 檔案  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。 選取 Visual Basic **Windows Forms 應用程式**專案類型。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。 選取**LINQ to SQL 類別**項目範本。  
  
3.  將檔案命名為 `northwind.dbml`。 按一下 [加入] 。 物件關聯式設計工具 （O/R 設計工具） 已開啟進行`northwind.dbml`檔案。  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>若要將資料表加入至查詢及修改設計工具  
  
1.  在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。 展開**資料表**資料夾。  
  
     如果您關閉 O/R 設計工具，您可以重新開啟它按兩下`northwind.dbml`您先前加入的檔案。  
  
2.  按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。  
  
     在設計工具會建立新的客戶物件，為您的專案。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>加入程式碼以修改資料庫，並顯示結果  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>到您的專案，Form1 的預設值的 Windows Form 控制項。  
  
2.  當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件加入專案。 此物件包含可用來存取 「 客戶 」 資料表的程式碼。 它也包含定義區域的客戶物件和資料表的客戶集合的程式碼。 <xref:System.Data.Linq.DataContext>物件針對名為您的專案是根據.dbml 檔案的名稱。 針對此專案，<xref:System.Data.Linq.DataContext>物件命名為`northwindDataContext`。  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>物件在您的程式碼和查詢，並修改 O/R 設計工具所指定的客戶集合。 您對客戶集合的變更才會反映資料庫中您藉由呼叫提交<xref:System.Data.Linq.DataContext.SubmitChanges%2A>方法<xref:System.Data.Linq.DataContext>物件。  
  
     按兩下 Windows Form，Form1，加入程式碼以<xref:System.Windows.Forms.Form.Load>Customers 資料表，查詢的事件會公開的屬性為您<xref:System.Data.Linq.DataContext>。 加入下列程式碼：  
  
    ```vb  
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
  
3.  從**工具箱**，將三個<xref:System.Windows.Forms.Button>控制項拖曳至表單。 選取第一個`Button`控制項。 在**屬性**視窗中，將`Name`的`Button`控制權傳輸至`AddButton`和`Text`至`Add`。 選取第二個按鈕，並設定`Name`屬性`UpdateButton`和`Text`屬性`Update`。 選取第三個按鈕，並設定`Name`屬性`DeleteButton`和`Text`屬性`Delete`。  
  
4.  按兩下**新增** 按鈕，將程式碼加入其`Click`事件。 加入下列程式碼：  
  
    ```vb  
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
  
5.  按兩下**更新** 按鈕，將程式碼加入其`Click`事件。 加入下列程式碼：  
  
    ```vb  
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
  
6.  按兩下**刪除** 按鈕，將程式碼加入其`Click`事件。 加入下列程式碼：  
  
    ```vb  
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
  
7.  請按 F5 執行您的專案。 按一下**新增**新增新的記錄。 按一下**更新**修改新的記錄。 按一下**刪除**刪除新的記錄。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [DataContext 方法 （O/R 設計工具）](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
