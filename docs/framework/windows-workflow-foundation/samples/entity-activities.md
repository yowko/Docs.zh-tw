---
title: 實體活動
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff7e505f6e2040e847b711030d310a70ede65413
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="entity-activities"></a><span data-ttu-id="3a89a-102">實體活動</span><span class="sxs-lookup"><span data-stu-id="3a89a-102">Entity Activities</span></span>
<span data-ttu-id="3a89a-103">這個範例示範如何使用 Windows Workflow Foundation 中的 ADO.NET Entity Framework，以簡化資料存取。</span><span class="sxs-lookup"><span data-stu-id="3a89a-103">This sample shows how to use the ADO.NET Entity Framework with Windows Workflow Foundation to simplify data access.</span></span>  
  
 <span data-ttu-id="3a89a-104">ADO.NET Entity Framework 可讓開發人員使用網域特有之物件、屬性和關聯性形式的資料，例如客戶、訂單、訂單詳細資料以及這些實體之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="3a89a-104">The ADO.NET Entity Framework enables developers to work with data in the form of domain-specific objects, properties and relationships such as Customers, Orders, Order Details and the relationships between these entities.</span></span> <span data-ttu-id="3a89a-105">ADO.NET Entity Framework 處理這項作業的方式，是提供可針對概念應用程式模型來進行程式設計的抽象層級，而不是直接針對關聯式儲存結構描述來進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="3a89a-105">The ADO.NET Entity Framework does this by providing a level of abstraction that enables programming against a conceptual application model instead of programming directly against a relational storage schema.</span></span> <span data-ttu-id="3a89a-106">如需有關 ADO.NET Entity Framework，請參閱[ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549)。</span><span class="sxs-lookup"><span data-stu-id="3a89a-106">For more information about the ADO.NET Entity Framework see [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="3a89a-107">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a89a-107">Sample details</span></span>  
 <span data-ttu-id="3a89a-108">這個範例會使用 `Northwind` 資料庫，而且包含了用來建立及移除 `Northwind` 資料庫的指令碼 (Setup.cmd 和 Cleanup.cmd)。</span><span class="sxs-lookup"><span data-stu-id="3a89a-108">This sample uses the `Northwind` database and includes scripts for creating and removing the `Northwind` database (Setup.cmd and Cleanup.cmd).</span></span> <span data-ttu-id="3a89a-109">此範例中的專案包含了根據 `Northwind` 資料庫的實體資料模型。</span><span class="sxs-lookup"><span data-stu-id="3a89a-109">The projects in this sample include an Entity Data Model based on the `Northwind` database.</span></span> <span data-ttu-id="3a89a-110">您可以開啟專案中包含的 `Northwind.edmx` 檔案來尋找此模型。</span><span class="sxs-lookup"><span data-stu-id="3a89a-110">You can find the model by opening the `Northwind.edmx` file that is included in the project.</span></span> <span data-ttu-id="3a89a-111">這個模型會定義可以使用 ADO.NET Entity Framework 存取之物件的形狀。</span><span class="sxs-lookup"><span data-stu-id="3a89a-111">This is the model that defines the shape of the objects that can be accessed using the ADO.NET Entity Framework.</span></span>  
  
 <span data-ttu-id="3a89a-112">下列活動包含在此範例中：</span><span class="sxs-lookup"><span data-stu-id="3a89a-112">The following activities are included in this sample:</span></span>  
  
-   <span data-ttu-id="3a89a-113">`EntitySQLQuery`：`EntitySQLQuery` 活動可讓您從根據 Entity SQL 查詢字串的資料庫中擷取物件。</span><span class="sxs-lookup"><span data-stu-id="3a89a-113">`EntitySQLQuery`: The `EntitySQLQuery` activity allows you to retrieve objects from the database based on an Entity SQL query string.</span></span> <span data-ttu-id="3a89a-114">Entity SQL 是一種與存放區無關的語言而且與 SQL 非常類似，它可讓您指定以概念模型為基礎的查詢以及屬於模型或網域之一部分的實體。</span><span class="sxs-lookup"><span data-stu-id="3a89a-114">Entity SQL is a store independent language that is similar to SQL and it allows you to specify queries based on the conceptual model and the entities that are a part of the model or domain.</span></span> <span data-ttu-id="3a89a-115">如需有關 Entity SQL 語言的詳細資訊，請參閱[Entity SQL 語言](http://go.microsoft.com/fwlink/?LinkId=165646)。</span><span class="sxs-lookup"><span data-stu-id="3a89a-115">For more information about Entity SQL Language, see [Entity SQL Language](http://go.microsoft.com/fwlink/?LinkId=165646).</span></span>  
  
-   <span data-ttu-id="3a89a-116">`EntityLinqQuery`：這個活動可讓您從根據 LINQ 查詢或述詞的資料庫中擷取物件。</span><span class="sxs-lookup"><span data-stu-id="3a89a-116">`EntityLinqQuery`: This activity allows you to retrieve objects from the database based on a LINQ query or predicate.</span></span>  
  
-   <span data-ttu-id="3a89a-117">`EntityAdd`：`EntityAdd` 活動可讓您將實體或實體集合加入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a89a-117">`EntityAdd`: The `EntityAdd` activity allows you to add an entity or a collection of entities to the database.</span></span>  
  
-   <span data-ttu-id="3a89a-118">`EntityDelete`：`EntityDelete` 活動可讓您從資料庫中刪除實體或實體集合。</span><span class="sxs-lookup"><span data-stu-id="3a89a-118">`EntityDelete`: The `EntityDelete` activity allows you to delete an entity or a collection of entities from the database.</span></span>  
  
-   <span data-ttu-id="3a89a-119">`ObjectContextScope`：之前提到的活動只能在包含的 `ObjectContextScope` 活動執行個體內使用。</span><span class="sxs-lookup"><span data-stu-id="3a89a-119">`ObjectContextScope`: The previously mentioned activities can only be used within a containing `ObjectContextScope` activity instance.</span></span> <span data-ttu-id="3a89a-120">`ObjectContextScope` 活動會設定與資料庫之間的連接。</span><span class="sxs-lookup"><span data-stu-id="3a89a-120">The `ObjectContextScope` activity sets up the connection to the database.</span></span> <span data-ttu-id="3a89a-121">此活動需要連接字串 (使用組態檔設定來傳入或擷取)。</span><span class="sxs-lookup"><span data-stu-id="3a89a-121">It requires a connection string (that is either passed in or retrieved using a configuration file setting).</span></span> <span data-ttu-id="3a89a-122">`ObjectContextScope` 活動可讓您輕鬆地針對實體執行一組相關作業。</span><span class="sxs-lookup"><span data-stu-id="3a89a-122">The `ObjectContextScope` activity makes it easy to perform a group of related operations on entities.</span></span> <span data-ttu-id="3a89a-123">因為這個範圍會維護作用中的連接，所以它是「無持續性」範圍。</span><span class="sxs-lookup"><span data-stu-id="3a89a-123">Because this scope maintains an active connection, it is a No Persist scope.</span></span> <span data-ttu-id="3a89a-124">此外，當 `ObjectContextScope` 活動結束時，使用該範圍內的實體活動所擷取之物件的任何變更都會自動保存回資料庫，而且不需要任何明確或後續的動作來將物件儲存回資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a89a-124">In addition, when the `ObjectContextScope` activity exits, any changes that are made to objects retrieved using Entity Activities within that scope automatically get persisted back to the database, and no explicit or subsequent action is required to save objects back to the database.</span></span>  
  
## <a name="using-the-entity-activities"></a><span data-ttu-id="3a89a-125">使用實體活動</span><span class="sxs-lookup"><span data-stu-id="3a89a-125">Using the entity activities</span></span>  
 <span data-ttu-id="3a89a-126">下列程式碼片段會示範如何使用這個範例所呈現的實體活動。</span><span class="sxs-lookup"><span data-stu-id="3a89a-126">The following code snippets demonstrate how to use the entity activities presented in this sample.</span></span>  
  
### <a name="entitysql"></a><span data-ttu-id="3a89a-127">EntitySql</span><span class="sxs-lookup"><span data-stu-id="3a89a-127">EntitySql</span></span>  
 <span data-ttu-id="3a89a-128">底下的程式碼片段會示範如何查詢位於倫敦 (London) 的所有客戶 (依據名稱排序)，以及如何逐一查看客戶清單。</span><span class="sxs-lookup"><span data-stu-id="3a89a-128">The code snippet below shows how to query all customers in London sorted by name and how to iterate through the list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>();  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>();  
  
// create and return the workflow  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
        {  
            Activities =   
                {               
                    new WriteLine { Text = "Executing query" },                            
                    // query for all customers that are in london   
                    new EntitySqlQuery<Customer>  
                    {  
                        EntitySql =  @"SELECT VALUE Customer   
                                        FROM NorthwindEntities.Customers AS Customer   
                                        WHERE Customer.City = 'London'   
                                        ORDER BY Customer.ContactName",  
                        Result = londonCustomers  
                    },  
  
                    // iterate through the list of customers and display them   
                    new ForEach<Customer>  
                    {                                      
                        Values = londonCustomers,  
                        Body = new ActivityAction<Customer>  
                        {  
                            Argument = iterationVariable,  
                            Handler = new WriteLine   
                            {   
                                  Text = new InArgument<String>(e =>    
                                              iterationVariable.Get(e).ContactName)   
                            }  
                        }  
                    }  
                }  
        }                 
};     
```  
  
### <a name="entitylinqquery"></a><span data-ttu-id="3a89a-129">EntityLinqQuery</span><span class="sxs-lookup"><span data-stu-id="3a89a-129">EntityLinqQuery</span></span>  
 <span data-ttu-id="3a89a-130">底下的程式碼片段會示範如何查詢位於倫敦 (London) 的所有客戶，以及如何逐一查看產生的客戶清單。</span><span class="sxs-lookup"><span data-stu-id="3a89a-130">The code snippet below shows how to query all customers in London and how to iterate through the resulting list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>() { Name = "LondonCustomers" };  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>() { Name = "iterationVariable" };  
  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // return all the customers that match with the provided Linq predicate  
            new EntityLinqQuery<Customer>  
            {   
                Predicate = new LambdaValue<Func<Customer, bool>>(  
                          ctx => new Func<Customer, bool>(c => c.City.Equals("London"))),                              
                Result = londonCustomers  
            },  
  
            // iterate through the list of customers and display in the console  
            new ForEach<Customer>  
            {                                      
                Values = londonCustomers,  
                Body = new ActivityAction<Customer>  
                {  
                    Argument = iterationVariable,  
                    Handler = new WriteLine   
                    {   
                        Text = new InArgument<String>(e =>   
                                      iterationVariable.Get(e).ContactName)   
                    }  
                }  
            }  
        }  
    }  
};  
```  
  
### <a name="entityadd"></a><span data-ttu-id="3a89a-131">EntityAdd</span><span class="sxs-lookup"><span data-stu-id="3a89a-131">EntityAdd</span></span>  
 <span data-ttu-id="3a89a-132">底下的程式碼片段會示範如何將 OrderDetail 記錄加入至現有的訂單。</span><span class="sxs-lookup"><span data-stu-id="3a89a-132">The code snippet below shows how to add an OrderDetail record to an existing Order.</span></span>  
  
```  
Variable<IEnumerable<Order>> orders = new Variable<IEnumerable<Order>>();  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();  
Variable<Order> order = new Variable<Order>();  
Variable<OrderDetail> orderDetail = new Variable<OrderDetail>();              
  
return new ObjectContextScope  
{  
    Variables = { order, orders, orderDetail, orderDetails },  
    ContainerName = "NorthwindEntities",  
    ConnectionString = new InArgument<string>(connStr),                  
    Body = new Sequence  
    {                      
        Activities =   
        {                            
           // get the order where we want to add the detail  
           new EntitySqlQuery<Order>  
           {  
               EntitySql =    
                    @"SELECT VALUE [Order]  
                      FROM NorthwindEntities.Orders as [Order]  
                      WHERE Order.OrderID == 10249",  
               Result = orders  
           },  
  
           // store the order in a variable  
           new Assign<Order>   
           {  
               To = new OutArgument<Order>(order),  
               Value = new InArgument<Order>(c => orders.Get(c).First<Order>())  
           },  
  
           // add the detail to the order  
           new EntityAdd<OrderDetail>  
           {  
               Entity = new InArgument<OrderDetail>(c =>   
                                         new OrderDetail {   
                                                  OrderID=10249, ProductID=11,   
                                                  Quantity=1, UnitPrice = 15,   
                                                  Discount = 0, Order = order.Get(c) })  
           }  
        }  
    }  
};  
```  
  
### <a name="entitydelete"></a><span data-ttu-id="3a89a-133">EntityDelete</span><span class="sxs-lookup"><span data-stu-id="3a89a-133">EntityDelete</span></span>  
 <span data-ttu-id="3a89a-134">底下的程式碼片段會示範如何刪除訂單中的現有 OrderDetail 記錄 (如果存在的話)。</span><span class="sxs-lookup"><span data-stu-id="3a89a-134">The code snippet below shows how to delete an existing OrderDetail record in an Order (if it exists).</span></span>  
  
```  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();              
  
return new ObjectContextScope  
{  
    Variables = { orderDetails },  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // find the entitiy to be deleted (order detail for product 11 in order 10249)  
            new EntitySqlQuery<OrderDetail>  
            {  
                EntitySql = @"SELECT VALUE OrderDetail  
                                FROM NorthwindEntities.OrderDetails as OrderDetail  
                               WHERE OrderDetail.OrderID == 10249   
                                 AND OrderDetail.ProductID == 11",  
                Result = orderDetails  
            },  
  
            // if the order detail is found, delete it, otherwise, display a message  
            new If  
            {  
                Condition = new InArgument<bool>(c=>orderDetails.Get(c).Count() > 0),  
                Then = new Sequence  
                {   
                    Activities =   
                    {                                      
                        new EntityDelete<OrderDetail>  
                        {  
                            Entity = new InArgument<OrderDetail>(c =>   
                                              orderDetails.Get(c).First<OrderDetail>())  
                        },  
                    }  
                },                              
                Else = new WriteLine { Text = "Order Detail for Deleting not found" }                              
            }                                                  
        }  
    }  
};  
```  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="3a89a-135">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="3a89a-135">To use this sample</span></span>  
 <span data-ttu-id="3a89a-136">您必須先在本機 SQL Server Express 執行個體中建立 `Northwind` 資料庫，然後才能執行這個範例。</span><span class="sxs-lookup"><span data-stu-id="3a89a-136">You must create the `Northwind` database in your local SQL server Express instance before running this sample.</span></span>  
  
#### <a name="to-set-up-the-northwind-database"></a><span data-ttu-id="3a89a-137">若要設定 Northwind 資料庫</span><span class="sxs-lookup"><span data-stu-id="3a89a-137">To set up the Northwind database</span></span>  
  
1.  <span data-ttu-id="3a89a-138">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="3a89a-138">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="3a89a-139">在新的命令提示字元視窗中，巡覽至 EntityActivities\CS 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a89a-139">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="3a89a-140">型別`setup.cmd`按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="3a89a-140">Type `setup.cmd` and press ENTER.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="3a89a-141">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="3a89a-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="3a89a-142">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 EntityActivities.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="3a89a-142">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EntityActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="3a89a-143">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="3a89a-143">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="3a89a-144">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="3a89a-144">To run the solution, press CTRL+F5.</span></span>  
  
 <span data-ttu-id="3a89a-145">在執行此範例之後，您可能會想要移除 `Northwind` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a89a-145">After running this sample, you may want to remove the `Northwind` database.</span></span>  
  
#### <a name="to-uninstall-the-northwind-database"></a><span data-ttu-id="3a89a-146">若要解除安裝 Northwind 資料庫</span><span class="sxs-lookup"><span data-stu-id="3a89a-146">To uninstall the Northwind database</span></span>  
  
1.  <span data-ttu-id="3a89a-147">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="3a89a-147">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="3a89a-148">在新的命令提示字元視窗中，巡覽至 EntityActivities\CS 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a89a-148">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="3a89a-149">型別`cleanup.cmd`按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="3a89a-149">Type `cleanup.cmd` and press ENTER.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a89a-150">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="3a89a-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a89a-151">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="3a89a-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3a89a-152">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="3a89a-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a89a-153">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="3a89a-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`