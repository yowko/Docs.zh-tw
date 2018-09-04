---
title: 實作商務邏輯 (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: d739e4bba96873740c53c07eccf687b060d82003
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552227"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="6e846-102">實作商務邏輯 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="6e846-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="6e846-103">本主題中的「商務邏輯」一詞，指的是您套用到資料的任何自訂規則或驗證測試，待套用之後，資料才會在資料庫中插入、更新或刪除。</span><span class="sxs-lookup"><span data-stu-id="6e846-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="6e846-104">商務邏輯有時也稱為「商務規則」或「定義域邏輯」。</span><span class="sxs-lookup"><span data-stu-id="6e846-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="6e846-105">在 N-Tier 應用程式中，這通常會設計為邏輯層，以便與展示層或資料存取層分開修改。</span><span class="sxs-lookup"><span data-stu-id="6e846-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="6e846-106">資料存取層可在資料庫中的資料更新、插入或刪除之前或之後叫用 (Invoke) 商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="6e846-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="6e846-107">商務邏輯可以簡單如結構描述驗證，用來確定欄位的型別與資料表資料行相容。</span><span class="sxs-lookup"><span data-stu-id="6e846-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="6e846-108">或者也可以包含一組物件，以各種複雜的方式互動。</span><span class="sxs-lookup"><span data-stu-id="6e846-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="6e846-109">這些規則可實作為資料庫上的預存程序 (Stored Procedure) 或實作為記憶體中的物件。</span><span class="sxs-lookup"><span data-stu-id="6e846-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="6e846-110">不過實作商務邏輯，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]可讓您將商務邏輯分開資料存取程式碼使用部分類別和部分方法。</span><span class="sxs-lookup"><span data-stu-id="6e846-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="6e846-111">LINQ to SQL 如何叫用商務邏輯</span><span class="sxs-lookup"><span data-stu-id="6e846-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="6e846-112">當您在設計階段產生實體類別 (手動或者使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]或 SQLMetal) 時，它會定義為部分類別。</span><span class="sxs-lookup"><span data-stu-id="6e846-112">When you generate an entity class at design time, either manually or by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="6e846-113">這表示，您可以在不同的程式碼檔案中，定義包含自訂商務邏輯之實體類別的另一個部分。</span><span class="sxs-lookup"><span data-stu-id="6e846-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="6e846-114">在編譯階段，這兩個部分會合併成單一類別。</span><span class="sxs-lookup"><span data-stu-id="6e846-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="6e846-115">但如果您必須使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]或 SQLMetal 重新產生實體類別，您還是可以這麼做，但您的類別部分將不會修改。</span><span class="sxs-lookup"><span data-stu-id="6e846-115">But if you have to regenerate your entity classes by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="6e846-116">定義實體和 <xref:System.Data.Linq.DataContext> 的部分類別包含部分方法。</span><span class="sxs-lookup"><span data-stu-id="6e846-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="6e846-117">您可使用這些方法當做擴充點，在實體或實體屬性進行任何更新、插入或刪除之前和之後套用商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="6e846-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="6e846-118">部分方法可視為編譯時期事件。</span><span class="sxs-lookup"><span data-stu-id="6e846-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="6e846-119">程式碼產生器會定義方法簽章，當 `DataContext` 被呼叫時，會在 get 和 set 屬性存取子、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> 建構函式，以及某些情況下在幕後呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="6e846-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="6e846-120">不過，如果您沒有實作特定部分方法，則對該方法的所有參考以及定義將在編譯時期移除。</span><span class="sxs-lookup"><span data-stu-id="6e846-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="6e846-121">您可以在另外一個程式碼檔案撰寫的實作定義中，執行任何必要的自訂邏輯。</span><span class="sxs-lookup"><span data-stu-id="6e846-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="6e846-122">您可以使用部分類別本身當做定義域層，或可以從部分方法的實作定義呼叫到另外的物件。</span><span class="sxs-lookup"><span data-stu-id="6e846-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="6e846-123">無論使用哪種方式，商務邏輯都能完全與資料存取程式碼和展示層程式碼分開。</span><span class="sxs-lookup"><span data-stu-id="6e846-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="6e846-124">詳述擴充點</span><span class="sxs-lookup"><span data-stu-id="6e846-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="6e846-125">下列範例顯示產生的程式碼的一部分[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]for`DataContext`有兩個資料表的類別：`Customers`和`Orders`。</span><span class="sxs-lookup"><span data-stu-id="6e846-125">The following example shows part of the code generated by the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="6e846-126">請注意，這個類別中的每個資料表都定義了 Insert、Update 和 Delete 方法。</span><span class="sxs-lookup"><span data-stu-id="6e846-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="6e846-127">如果您在部分類別中實作 Insert、Update 和 Delete 方法，則當 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 被呼叫時，<xref:System.Data.Linq.DataContext.SubmitChanges%2A> 執行階段會呼叫這些方法，而不會呼叫自己的預設方法。</span><span class="sxs-lookup"><span data-stu-id="6e846-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="6e846-128">這可讓您覆寫建立/讀取/更新/刪除作業的預設行為。</span><span class="sxs-lookup"><span data-stu-id="6e846-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="6e846-129">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 自訂插入、 更新和刪除實體類別的行為](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)。</span><span class="sxs-lookup"><span data-stu-id="6e846-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="6e846-130">`OnCreated` 方法是在類別建構函式中呼叫的。</span><span class="sxs-lookup"><span data-stu-id="6e846-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="6e846-131">實體類別有三個方法，會分別在實體建立、載入和驗證 (當呼叫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 時) 時，由 `SubmitChanges` 執行階段呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e846-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="6e846-132">實體類別還有適用於每個屬性的兩個部分方法，一是在屬性設定之前呼叫，另一則是在之後呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e846-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="6e846-133">下列程式碼範例顯示為 `Customer` 類別產生的一些方法：</span><span class="sxs-lookup"><span data-stu-id="6e846-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="6e846-134">這些方法會在屬性 set 存取子中呼叫，如下列 `CustomerID` 屬性的範例所示：</span><span class="sxs-lookup"><span data-stu-id="6e846-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="6e846-135">在您的類別部分中，您可以撰寫方法的實作定義。</span><span class="sxs-lookup"><span data-stu-id="6e846-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="6e846-136">在 Visual Studio 中，輸入之後`partial`您會看到 IntelliSense 中的其他部分類別的方法定義。</span><span class="sxs-lookup"><span data-stu-id="6e846-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="6e846-137">如需如何使用部分方法將商務邏輯加入到應用程式中，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="6e846-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="6e846-138">如何：將驗證新增至實體類別</span><span class="sxs-lookup"><span data-stu-id="6e846-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="6e846-139">逐步解說：自訂實體類別的插入、更新和刪除行為</span><span class="sxs-lookup"><span data-stu-id="6e846-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [<span data-ttu-id="6e846-140">逐步解說： 將驗證新增至實體類別</span><span class="sxs-lookup"><span data-stu-id="6e846-140">Walkthrough: Adding Validation to Entity Classes</span></span>](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a><span data-ttu-id="6e846-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e846-141">See Also</span></span>  
 [<span data-ttu-id="6e846-142">部分類別和方法</span><span class="sxs-lookup"><span data-stu-id="6e846-142">Partial Classes and Methods</span></span>](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [<span data-ttu-id="6e846-143">部分方法</span><span class="sxs-lookup"><span data-stu-id="6e846-143">Partial Methods</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 <span data-ttu-id="6e846-144">[LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) (Visual Studio 中的 LINQ to SQL 工具)</span><span class="sxs-lookup"><span data-stu-id="6e846-144">[LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)</span></span>  
 [<span data-ttu-id="6e846-145">SqlMetal.exe (程式碼產生工具)</span><span class="sxs-lookup"><span data-stu-id="6e846-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
