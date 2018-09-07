---
title: 實作商務邏輯 (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: d739e4bba96873740c53c07eccf687b060d82003
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43798860"
---
# <a name="implementing-business-logic-linq-to-sql"></a>實作商務邏輯 (LINQ to SQL)
本主題中的「商務邏輯」一詞，指的是您套用到資料的任何自訂規則或驗證測試，待套用之後，資料才會在資料庫中插入、更新或刪除。 商務邏輯有時也稱為「商務規則」或「定義域邏輯」。 在 N-Tier 應用程式中，這通常會設計為邏輯層，以便與展示層或資料存取層分開修改。 資料存取層可在資料庫中的資料更新、插入或刪除之前或之後叫用 (Invoke) 商務邏輯。  
  
 商務邏輯可以簡單如結構描述驗證，用來確定欄位的型別與資料表資料行相容。 或者也可以包含一組物件，以各種複雜的方式互動。 這些規則可實作為資料庫上的預存程序 (Stored Procedure) 或實作為記憶體中的物件。 不過實作商務邏輯，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]可讓您將商務邏輯分開資料存取程式碼使用部分類別和部分方法。  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>LINQ to SQL 如何叫用商務邏輯  
 當您在設計階段產生實體類別 (手動或者使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]或 SQLMetal) 時，它會定義為部分類別。 這表示，您可以在不同的程式碼檔案中，定義包含自訂商務邏輯之實體類別的另一個部分。 在編譯階段，這兩個部分會合併成單一類別。 但如果您必須使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]或 SQLMetal 重新產生實體類別，您還是可以這麼做，但您的類別部分將不會修改。  
  
 定義實體和 <xref:System.Data.Linq.DataContext> 的部分類別包含部分方法。 您可使用這些方法當做擴充點，在實體或實體屬性進行任何更新、插入或刪除之前和之後套用商務邏輯。 部分方法可視為編譯時期事件。 程式碼產生器會定義方法簽章，當 `DataContext` 被呼叫時，會在 get 和 set 屬性存取子、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> 建構函式，以及某些情況下在幕後呼叫方法。 不過，如果您沒有實作特定部分方法，則對該方法的所有參考以及定義將在編譯時期移除。  
  
 您可以在另外一個程式碼檔案撰寫的實作定義中，執行任何必要的自訂邏輯。 您可以使用部分類別本身當做定義域層，或可以從部分方法的實作定義呼叫到另外的物件。 無論使用哪種方式，商務邏輯都能完全與資料存取程式碼和展示層程式碼分開。  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>詳述擴充點  
 下列範例顯示產生的程式碼的一部分[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]for`DataContext`有兩個資料表的類別：`Customers`和`Orders`。 請注意，這個類別中的每個資料表都定義了 Insert、Update 和 Delete 方法。  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 如果您在部分類別中實作 Insert、Update 和 Delete 方法，則當 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 被呼叫時，<xref:System.Data.Linq.DataContext.SubmitChanges%2A> 執行階段會呼叫這些方法，而不會呼叫自己的預設方法。 這可讓您覆寫建立/讀取/更新/刪除作業的預設行為。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 自訂插入、 更新和刪除實體類別的行為](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)。  
  
 `OnCreated` 方法是在類別建構函式中呼叫的。  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 實體類別有三個方法，會分別在實體建立、載入和驗證 (當呼叫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 時) 時，由 `SubmitChanges` 執行階段呼叫。 實體類別還有適用於每個屬性的兩個部分方法，一是在屬性設定之前呼叫，另一則是在之後呼叫。 下列程式碼範例顯示為 `Customer` 類別產生的一些方法：  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 這些方法會在屬性 set 存取子中呼叫，如下列 `CustomerID` 屬性的範例所示：  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 在您的類別部分中，您可以撰寫方法的實作定義。 在 Visual Studio 中，輸入之後`partial`您會看到 IntelliSense 中的其他部分類別的方法定義。  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer   
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 如需如何使用部分方法將商務邏輯加入到應用程式中，請參閱下列主題：  
  
 [如何：將驗證新增至實體類別](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [逐步解說：自訂實體類別的插入、更新和刪除行為](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [逐步解說： 將驗證新增至實體類別](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a>另請參閱  
 [部分類別和方法](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [部分方法](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) (Visual Studio 中的 LINQ to SQL 工具)  
 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
