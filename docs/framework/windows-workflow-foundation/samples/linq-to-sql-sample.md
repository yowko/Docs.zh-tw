---
title: "LINQ to SQL 範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06273f3ac7dd159adac4c058a23c187f44417d94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="6b20c-102">LINQ to SQL 範例</span><span class="sxs-lookup"><span data-stu-id="6b20c-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="6b20c-103">這個範例示範如何建立活動，以使用 SQL Server 資料庫資料表中的 LINQ to SQL 查詢實體。</span><span class="sxs-lookup"><span data-stu-id="6b20c-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6b20c-104">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6b20c-104">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples may already be installed on your machine.</span></span> <span data-ttu-id="6b20c-105">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6b20c-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="6b20c-106">如果此目錄不存在，請按一下頁面最上方的 [下載範例] 連結。</span><span class="sxs-lookup"><span data-stu-id="6b20c-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="6b20c-107">請注意，這個連結會下載及安裝所有 [!INCLUDE[wf1](../../../../includes/wf1-md.md)]、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和 [!INCLUDE[infocard](../../../../includes/infocard-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="6b20c-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="6b20c-108">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6b20c-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="6b20c-109">FindInSqlTable 的活動詳細資料</span><span class="sxs-lookup"><span data-stu-id="6b20c-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="6b20c-110">這個活動可讓使用者使用 LINQ to SQL 查詢資料庫資料表中的實體。</span><span class="sxs-lookup"><span data-stu-id="6b20c-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="6b20c-111">活動使用者也可以提供 Lambda 運算式形式的 LINQ 述詞來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="6b20c-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="6b20c-112">如果未提供述詞，則會傳回整個資料表。</span><span class="sxs-lookup"><span data-stu-id="6b20c-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="6b20c-113">下表詳細說明活動的屬性和傳回值。</span><span class="sxs-lookup"><span data-stu-id="6b20c-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="6b20c-114">屬性或傳回值</span><span class="sxs-lookup"><span data-stu-id="6b20c-114">Property or Return Value</span></span>|<span data-ttu-id="6b20c-115">描述</span><span class="sxs-lookup"><span data-stu-id="6b20c-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="6b20c-116">`Collection` 屬性</span><span class="sxs-lookup"><span data-stu-id="6b20c-116">`Collection` property</span></span>|<span data-ttu-id="6b20c-117">指定來源集合的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6b20c-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="6b20c-118">`Predicate` 屬性</span><span class="sxs-lookup"><span data-stu-id="6b20c-118">`Predicate` property</span></span>|<span data-ttu-id="6b20c-119">必要屬性，指定 Lambda 運算式形式的集合篩選。</span><span class="sxs-lookup"><span data-stu-id="6b20c-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="6b20c-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="6b20c-120">Return Value</span></span>|<span data-ttu-id="6b20c-121">篩選的集合。</span><span class="sxs-lookup"><span data-stu-id="6b20c-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="6b20c-122">使用自訂活動的程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6b20c-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="6b20c-123">下列程式碼範例使用 `FindInSqlTable` 自訂活動，在名為 `Employee` 的 SQL Server 資料表中尋找 `Role` 資料行等於 `SDE` 的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="6b20c-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6b20c-124">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="6b20c-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="6b20c-125">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="6b20c-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="6b20c-126">導覽至包含這個範例的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b20c-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="6b20c-127">執行 Setup.cmd 命令檔。</span><span class="sxs-lookup"><span data-stu-id="6b20c-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6b20c-128">Setup.cmd 指令碼會嘗試在本機電腦 SQL Server Express 安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b20c-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="6b20c-129">如果您想要在其他 SQL Server 執行個體中安裝，請編輯 Setup.cmd。</span><span class="sxs-lookup"><span data-stu-id="6b20c-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="6b20c-130">Setup.cmd 指令碼會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6b20c-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="6b20c-131">建立名為 LinqToSqlSample 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b20c-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="6b20c-132">建立 Roles 資料表。</span><span class="sxs-lookup"><span data-stu-id="6b20c-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="6b20c-133">建立 Employees 資料表。</span><span class="sxs-lookup"><span data-stu-id="6b20c-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="6b20c-134">將 3 個記錄插入至 Roles 資料表。</span><span class="sxs-lookup"><span data-stu-id="6b20c-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="6b20c-135">將 12 個記錄插入至 Employees 資料表。</span><span class="sxs-lookup"><span data-stu-id="6b20c-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="6b20c-136">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 LinqToSQL.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="6b20c-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="6b20c-137">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="6b20c-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="6b20c-138">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="6b20c-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="6b20c-139">若要解除安裝 LinqToSql 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="6b20c-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="6b20c-140">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="6b20c-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="6b20c-141">導覽至包含這個範例的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b20c-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="6b20c-142">執行 Cleanup.cmd 命令檔。</span><span class="sxs-lookup"><span data-stu-id="6b20c-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6b20c-143">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6b20c-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b20c-144">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6b20c-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6b20c-145">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="6b20c-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b20c-146">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6b20c-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="6b20c-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b20c-147">See Also</span></span>  
 [<span data-ttu-id="6b20c-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6b20c-148">LINQ to SQL</span></span>](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="6b20c-149">使用者入門 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="6b20c-149">Getting Started (LINQ to SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150377)
