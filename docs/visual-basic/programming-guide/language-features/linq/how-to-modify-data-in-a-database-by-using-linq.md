---
title: 如何：使用 LINQ 修改資料庫中的資料
ms.date: 07/20/2015
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
ms.openlocfilehash: 9a10efef5ae92dd21888594ae80a3fc07869a8c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344950"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>如何：使用 LINQ 修改資料庫中的資料 (Visual Basic)

語言整合式查詢（LINQ）查詢可讓您輕鬆地存取資料庫資訊並修改資料庫中的值。

下列範例示範如何建立新的應用程式，以抓取和更新 SQL Server 資料庫中的資訊。

本主題中的範例會使用 Northwind 範例資料庫。 如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。 如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。

### <a name="to-create-a-connection-to-a-database"></a>建立資料庫的連接

1. 在 Visual Studio 中，按一下 [ **View** ] 功能表以開啟**伺服器總管**/**資料庫總管**，然後選取 [**伺服器總管** **/資料庫總管]。**

2. 以滑鼠右鍵按一下**伺服器總管**/**資料庫總管**中的 [**資料連線**]，然後按一下 [**新增連接**]。

3. 請指定與 Northwind 範例資料庫的有效連接。

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>若要加入具有 LINQ to SQL 檔案的專案

1. 在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。 選取 [Visual Basic **Windows Forms 應用程式**] 做為 [專案類型]。

2. 在 [專案] 功能表中，按一下 [加入新項目]。 選取 [ **LINQ to SQL 類別**] 專案範本。

3. 將檔案命名為 `northwind.dbml`。 按一下 [加入]。 `northwind.dbml` 檔案的物件關聯式設計工具（O/R 設計工具）隨即開啟。

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>若要將資料表加入至設計工具並進行查詢和修改

1. 在**伺服器總管**/**資料庫總管**中，展開 Northwind 資料庫的連接。 展開 [**資料表]** 資料夾。

     如果您已經關閉 O/R 設計工具，可以按兩下先前加入的 `northwind.dbml` 檔案來重新開啟它。

2. 按一下 [Customers] 資料表，並將它拖曳至設計工具的左窗格。

     設計工具會為您的專案建立新的 Customer 物件。

3. 儲存您的變更並關閉設計工具。

4. 儲存您的專案。

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>若要加入程式碼來修改資料庫並顯示結果

1. 從 [**工具箱**] 中，將 [<xref:System.Windows.Forms.DataGridView>] 控制項拖曳至您的專案 [Form1] 的預設 Windows Form。

2. 當您將資料表加入至 O/R 設計工具時，設計工具會將 <xref:System.Data.Linq.DataContext> 物件新增至您的專案。 此物件包含您可以用來存取 Customers 資料表的程式碼。 它也包含定義本機 Customer 物件和資料表之 Customers 集合的程式碼。 專案的 <xref:System.Data.Linq.DataContext> 物件是根據 .dbml 檔案的名稱來命名。 針對此專案，<xref:System.Data.Linq.DataContext> 物件的名稱為 `northwindDataContext`。

     您可以在程式碼中建立 <xref:System.Data.Linq.DataContext> 物件的實例，並查詢和修改 O/R 設計工具所指定的 Customers 集合。 您對 Customers 集合所做的變更不會反映在資料庫中，直到您藉由呼叫 <xref:System.Data.Linq.DataContext> 物件的 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 方法來提交為止。

     按兩下 Windows Form Form1，將程式碼加入 <xref:System.Windows.Forms.Form.Load> 事件，以查詢公開為 <xref:System.Data.Linq.DataContext>屬性的 Customers 資料表。 加入下列程式碼：

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

3. 從 [**工具箱**] 中，將三個 <xref:System.Windows.Forms.Button> 控制項拖曳至表單上。 選取第一個 `Button` 控制項。 在 **屬性** 視窗中，將 `Button` 控制項的 `Name` 設定為 `AddButton` 以及要 `Add`的 `Text`。 選取第二個按鈕，並將 [`Name`] 屬性設定為 [`UpdateButton`]，將 `Text` 屬性設為 [`Update`]。 選取第三個按鈕，並將 [`Name`] 屬性設定為 [`DeleteButton`]，並將 `Text` 屬性設為 `Delete`。

4. 按兩下 [**新增**] 按鈕，將程式碼新增至其 `Click` 事件。 加入下列程式碼：

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

5. 按兩下 [**更新**] 按鈕，將程式碼新增至其 `Click` 事件。 加入下列程式碼：

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. 按兩下 [**刪除**] 按鈕，將程式碼加入其 `Click` 事件。 加入下列程式碼：

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

7. 請按 F5 執行您的專案。 按一下 **[新增]** 以新增記錄。 按一下 [**更新**] 以修改新的記錄。 按一下 [**刪除**] 以刪除新的記錄。

## <a name="see-also"></a>請參閱

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
