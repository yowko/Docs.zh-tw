---
title: "實體活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 實體活動
這個範例示範如何與 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] 搭配使用 ADO.NET Entity Framework，以簡化資料存取。  
  
 ADO.NET Entity Framework 可讓開發人員使用網域特有之物件、屬性和關聯性形式的資料，例如客戶、訂單、訂單詳細資料以及這些實體之間的關聯性。ADO.NET Entity Framework 藉由提供某個層級的抽象概念來進行這項處理，這個概念會針對概念應用程式模型進行程式設計，而不是直接針對關聯式儲存結構描述進行程式設計。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] ADO.NET Entity Framework，請參閱 [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549)。  
  
## 範例詳細資料  
 這個範例會使用 `Northwind` 資料庫，而且包含了用來建立及移除 `Northwind` 資料庫的指令碼 \(Setup.cmd 和 Cleanup.cmd\)。此範例中的專案包含了根據 `Northwind` 資料庫的實體資料模型。您可以開啟專案中包含的 `Northwind.edmx` 檔案來尋找此模型。這個模型會定義可以使用 ADO.NET Entity Framework 存取之物件的形狀。  
  
 下列活動包含在此範例中：  
  
-   `EntitySQLQuery`：`EntitySQLQuery` 活動可讓您從根據 Entity SQL 查詢字串的資料庫中擷取物件。Entity SQL 是一種與存放區無關的語言而且與 SQL 非常類似，它可讓您指定以概念模型為基礎的查詢以及屬於模型或網域之一部分的實體。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]如需 Entity SQL 語言的詳細資訊，請參閱 [Entity SQL 語言](http://go.microsoft.com/fwlink/?LinkId=165646) \(英文\)。  
  
-   `EntityLinqQuery`：這個活動可讓您從根據 LINQ 查詢或述詞的資料庫中擷取物件。  
  
-   `EntityAdd`：`EntityAdd` 活動可讓您將實體或實體集合加入至資料庫。  
  
-   `EntityDelete`：`EntityDelete` 活動可讓您從資料庫中刪除實體或實體集合。  
  
-   `ObjectContextScope`：之前提到的活動只能在包含的 `ObjectContextScope` 活動執行個體內使用。`ObjectContextScope` 活動會設定與資料庫之間的連接。此活動需要連接字串 \(使用組態檔設定來傳入或擷取\)。`ObjectContextScope` 活動可讓您輕鬆地針對實體執行一組相關作業。因為這個範圍會維護作用中的連接，所以它是「無持續性」範圍。此外，當 `ObjectContextScope` 活動結束時，使用該範圍內的實體活動所擷取之物件的任何變更都會自動保存回資料庫，而且不需要任何明確或後續的動作來將物件儲存回資料庫。  
  
## 使用實體活動  
 下列程式碼片段會示範如何使用這個範例所呈現的實體活動。  
  
### EntitySql  
 底下的程式碼片段會示範如何查詢位於倫敦 \(London\) 的所有客戶 \(依據名稱排序\)，以及如何逐一查看客戶清單。  
  
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
  
### EntityLinqQuery  
 底下的程式碼片段會示範如何查詢位於倫敦 \(London\) 的所有客戶，以及如何逐一查看產生的客戶清單。  
  
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
  
### EntityAdd  
 底下的程式碼片段會示範如何將 OrderDetail 記錄加入至現有的訂單。  
  
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
  
### EntityDelete  
 底下的程式碼片段會示範如何刪除訂單中的現有 OrderDetail 記錄 \(如果存在的話\)。  
  
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
  
## 若要使用這個範例  
 您必須先在本機 SQL Server Express 執行個體中建立 `Northwind` 資料庫，然後才能執行這個範例。  
  
#### 若要設定 Northwind 資料庫  
  
1.  開啟命令提示字元。  
  
2.  在新的命令提示字元視窗中，巡覽至 EntityActivities\\CS 資料夾。  
  
3.  輸入 `setup.cmd` 然後按 ENTER。  
  
#### 若要執行範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 EntityActivities.sln 方案檔。  
  
2.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
3.  若要執行此方案，請按下 CTRL\+F5。  
  
 在執行此範例之後，您可能會想要移除 `Northwind` 資料庫。  
  
#### 若要解除安裝 Northwind 資料庫  
  
1.  開啟命令提示字元。  
  
2.  在新的命令提示字元視窗中，巡覽至 EntityActivities\\CS 資料夾。  
  
3.  輸入 `cleanup.cmd` 然後按 ENTER。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`  
  
## 請參閱