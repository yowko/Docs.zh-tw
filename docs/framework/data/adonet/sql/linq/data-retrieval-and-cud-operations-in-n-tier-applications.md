---
title: 多層式架構應用程式中的資料擷取和 CUD 作業 (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 706dbda98d0e1674b76ebc6a25c7a34746720ea2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247369"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>多層式架構應用程式中的資料擷取和 CUD 作業 (LINQ to SQL)
當您將像是 Customers 或 Orders 等實體物件透過網路序列化到用戶端時，這些實體會與其資料內容中斷連結。 資料內容不會再追蹤它們的變更或它們與其他物件的關聯。 如果用戶端只讀取資料，這就不成問題。 此外，要讓用戶端加入資料列到資料庫，也相對來說簡單。 不過，如果您的應用程式要讓用戶端能夠更新或刪除資料，就必須將實體附加到新的資料內容，才能呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>。 此外，如果您使用開放式並行存取 (Optimistic Concurrency) 來檢查原始值，那麼也需要想辦法將原始實體和修改過的實體提供給資料庫。 `Attach` 方法即是提供來讓您將中斷連結的實體放入新的資料內容。  
  
 即使您要序列化 proxy 物件來取代[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]實體, 仍然必須在資料存取層 (DAL) 上建立實體, 並將它附加至新<xref:System.Data.Linq.DataContext?displayProperty=nameWithType>的, 才能將資料提交至資料庫。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]會完全不在乎實體如何序列化。 如需如何使用物件關聯式設計工具和 SQLMetal 工具來產生可使用 Windows Communication Foundation (WCF) 序列化之類別的詳細資訊, 請參閱[如何:讓實體可](how-to-make-entities-serializable.md)序列化。  
  
> [!NOTE]
> 請只在新的或還原序列化的實體上呼叫 `Attach` 方法。 要將實體與其原始資料內容中斷連結的唯一方式就是使其序列化。 如果您嘗試將未中斷連結的實體附加到新的資料內容，而該實體仍擁有先前資料內容的延遲載入器，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 就會擲回例外狀況。 若實體擁有來自兩個不同資料內容的延遲載入器，當您在該實體上執行插入、更新和刪除作業時，可能會導致不想要的結果。 如需延遲載入器的詳細資訊, 請參閱[延後與立即載入](deferred-versus-immediate-loading.md)。  
  
## <a name="retrieving-data"></a>擷取資料  
  
### <a name="client-method-call"></a>用戶端方法呼叫  
 下列範例示範 Windows Form 用戶端對 DAL 的範例方法呼叫。 在這個範例中，DAL 實作為 Windows 服務庫：  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =   
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =   
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,   
    // the client needs to store them and pass them back to the   
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a>中介層實作  
 下列範例顯示中介層 (Middle Tier) 上的介面方法實作。 下列是需要注意的兩個重點：  
  
- <xref:System.Data.Linq.DataContext> 是在方法範圍內宣告。  
  
- 此方法會傳回實際結果的 <xref:System.Collections.IEnumerable> 集合。 序列化程式將會執行查詢，將結果送回用戶端/展示層。 若要在中介層本機上存取查詢結果，您可以在查詢變數上呼叫 `ToList` 或 `ToArray` 來強制執行。 然後就可以將該清單或陣列以 `IEnumerable` 傳回。  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =   
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();   
}  
```  
  
 資料內容的執行個體應具有「工作單元」的存留期 (Lifetime)。 在鬆散結合的環境中，工作單元通常很小，可能是一個開放式異動，其中包含對 `SubmitChanges` 的單一呼叫。 因此，資料內容會在方法範圍內建立和處置 (Dispose)。 如果工作單元包含對商務規則邏輯的呼叫，那麼通常會需要在整個作業期間保留 `DataContext` 執行個體。 無論在哪種情況下，`DataContext` 執行個體都不適合跨任意數目的交易而長期保持作用中。  
  
 這個方法將傳回 Product 物件，而不是與每個 Project 相關聯之 Order_Detail 物件的集合。 請使用 <xref:System.Data.Linq.DataLoadOptions> 物件來變更此預設行為。 如需詳細資訊，請參閱[如何：控制要抓取多少相關資料](how-to-control-how-much-related-data-is-retrieved.md)。  
  
## <a name="inserting-data"></a>插入資料  
 若要插入新物件，展示層會在中介層介面上呼叫相關方法，並傳入要插入的新物件即可。 在某些情況下，為提高效率，用戶端可能只會傳入部分值，再由中介層建構完整物件。  
  
### <a name="middle-tier-implementation"></a>中介層實作  
 在中介層上，新的 <xref:System.Data.Linq.DataContext> 會建立，物件會使用 <xref:System.Data.Linq.DataContext> 方法附加到 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>，當呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，物件即會插入。 例外狀況、回呼 (Callback) 和錯誤狀況的處理方式就如同在任何其他 Web 服務案例中處理一樣。  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a>刪除資料  
 若要刪除資料庫中的現有物件，展示層會在中介層介面上呼叫相關方法，然後針對要刪除的物件，傳入包含其原始值的複本。  
  
 刪除作業包含開放式並行存取檢查，而要刪除的物件必須先附加到新的資料內容。 在這個範例中，`Boolean` 參數會設定為 `false`，表示物件沒有時間戳記 (RowVersion)。 如果資料庫資料表會為每個資料錄產生時間戳記，那麼開放式並行存取檢查會簡單許多，對用戶端來說尤然。 這只要傳入原始或修改過的物件，再將 `Boolean` 參數設定為 `true` 即可。 無論在哪種情況下，在中介層上通常需要攔截 <xref:System.Data.Linq.ChangeConflictException>。 如需如何處理開放式平行存取衝突的詳細資訊, [請參閱開放式平行存取:總覽](optimistic-concurrency-overview.md)。  
  
 刪除在關聯資料表上具有外部索引鍵條件約束的實體時，您必須先刪除其 <xref:System.Data.Linq.EntitySet%601> 集合中的所有物件。  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a>更新資料  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援在下列牽涉到開放式並行存取的案例中更新：  
  
- 以時間戳記或 RowVersion 號碼為基礎的開放式並行存取。  
  
- 以實體屬性子集的原始值為基礎的開放式並行存取。  
  
- 以完整原始和修改過的實體為基礎的開放式並行存取。  
  
 您也可以對實體連同其關聯一起執行更新或刪除，例如 Customer 及其關聯 Order 物件的集合。 當您在用戶端上修改實體物件及子 (`EntitySet`) 集合的圖形，而開放式並行存取需要原始值時，用戶端必須提供每個實體和 <xref:System.Data.Linq.EntitySet%601> 物件的原始值。 如果要讓用戶端能夠在單一方法呼叫中執行一組相關的更新、刪除和插入，您必須提供用戶端方式來指出要對每個實體執行何種作業。 接著在中介層上，您必須為每個實體呼叫適當的 <xref:System.Data.Linq.ITable.Attach%2A> 方法，再呼叫 <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>、<xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A> 或 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (插入不需要 `Attach`)，才能呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>。 請不要擷取資料庫的值來當做更新之前取得原始值的方式。  
  
 如需開放式平行存取的詳細資訊[, 請參閱開放式平行存取:總覽](optimistic-concurrency-overview.md)。 如需解決開放式平行存取變更衝突的詳細資訊[, 請參閱如何:管理變更衝突](how-to-manage-change-conflicts.md)。  
  
 下列範例將示範每個案例：  
  
### <a name="optimistic-concurrency-with-timestamps"></a>使用時間戳記的開放式並行存取  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a>使用原始值子集  
 在這種方式中，用戶端會傳回已序列化的完整物件以及要修改的值。  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a>使用完整實體  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }   
    }  
}  
```  
  
 若要更新集合，請呼叫 <xref:System.Data.Linq.ITable.AttachAll%2A>，而非 `Attach`。  
  
### <a name="expected-entity-members"></a>必要的實體成員  
 如前所述，在呼叫 `Attach` 方法之前，只需要設定實體物件的某些成員。 需要設定的實體成員必須符合下列條件：  
  
- 屬於實體識別的一部分。  
  
- 必須修改。  
  
- 本身是時間戳記或將其 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Attribute) 設為 `Never` 以外的值。  
  
 如果資料表使用時間戳記或版本號碼進行開放式並行存取檢查，則您必須設定這些成員，才能呼叫 <xref:System.Data.Linq.ITable.Attach%2A>。 當 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 在該 Column 屬性 (Attribute) 上設定為 true 時，成員就會專供開放式並行存取檢查使用。 只有在版本號碼或時間戳記值在資料庫上相同時，才會提交任何要求的變更。  
  
 只要成員沒有將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 設定為 `Never`，該成員也會用於開放式並行存取檢查。 如果沒有指定其他值，預設值會是 `Always`。  
  
 如果遺漏任何一個必要成員，在 <xref:System.Data.Linq.ChangeConflictException> 期間會擲回 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> (「資料列找不到，或者已變更」)。  
  
### <a name="state"></a>State  
 實體物件在附加到 <xref:System.Data.Linq.DataContext> 執行個體之後，會視為處於 `PossiblyModified` 狀態。 有三種方式可將附加物件強制視為 `Modified`。  
  
1. 以未修改的形式附加，再執行修改欄位。  
  
2. 使用接受目前和原始物件執行個體的 <xref:System.Data.Linq.Table%601.Attach%2A> 多載附加。 這會將新舊值一起提供給變更 Tracker，這樣它就會自動得知哪些欄位已變更。  
  
3. 使用接受第二個布林值參數 (設為 true) 的 <xref:System.Data.Linq.Table%601.Attach%2A> 多載附加。 這會指示變更 Tracker 將物件視為已修改，而無須提供任何原始值。 在此方式中，物件必須有版本/時間戳記欄位。  
  
 如需詳細資訊, 請參閱[物件狀態和變更追蹤](object-states-and-change-tracking.md)。  
  
 如果實體物件已出現在 ID 快取，而其識別與要附加的物件相同，就會擲回 <xref:System.Data.Linq.DuplicateKeyException>。  
  
 當您使用一組 `IEnumerable` 物件附加時，若有已經存在的索引鍵出現時，會擲回 <xref:System.Data.Linq.DuplicateKeyException>。 其餘的物件將不會附加。  
  
## <a name="see-also"></a>另請參閱

- [使用 LINQ to SQL 的多層式架構和遠端應用程式](n-tier-and-remote-applications-with-linq-to-sql.md)
- [背景資訊](background-information.md)
