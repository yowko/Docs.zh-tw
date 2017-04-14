---
title: "Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, improving efficiency"
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency
TPL 資料流程式庫提供 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=fullName> 類別，以便從一或多個來源接收並緩衝資料然後傳送這些緩衝區的資料做為一個集合。  當您從一或多個來源收集資料然後將多個資料項目處理為一個批次時，這個批次處理機制很有用。  例如，假設有一個應用程式，使用資料流程將記錄插入至資料庫。  若能將多個項目同時插入，而非循序地個別插入，此作業會更有效率。  本文件說明如何使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別來改善這類資料庫作業的效率。  也說明如何使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 類別擷取結果，以及當程式從資料庫讀取時發生的任何例外狀況。  
  
> [!TIP]
>  TPL 資料流程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並沒有和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 配置在一起。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[**管理 NuGet 封裝**\]，並且線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
## 必要條件  
  
1.  在開始這個逐步解說之前，請閱讀 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) 文件的聯結區塊部分。  
  
2.  請確定您的電腦上有可用的 Northwind 資料庫的複本， Northwind.sdf。  這個檔案通常位於資料夾 %Program Files%\\Microsoft SQL Server Compact Edition\\v3.5\\Samples\\。  
  
    > [!IMPORTANT]
    >  在 Windows 中某些版本，如果 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 在非系統管理員模式下執行，就無法連接至資料庫。  若要連接至資料庫，請啟動 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 命令提示字元並調整至 \[**以系統管理員身分執行**\] 模式。  
  
 此逐步解說包含下列章節：  
  
-   [建立主控台應用程式](#creating)  
  
-   [定義 Employee 類別](#employeeClass)  
  
-   [定義 Employee 資料庫作業](#operations)  
  
-   [將 Employee 資料加至資料庫，而不使用緩衝區](#nonBuffering)  
  
-   [使用緩衝區將 Employee 資料儲存至資料庫](#buffering)  
  
-   [使用緩衝區聯結讀取資料庫的 Employee 資料](#bufferedJoin)  
  
-   [完整的範例](#complete)  
  
<a name="creating"></a>   
## 建立主控台應用程式  
  
<a name="consoleApp"></a>   
1.  在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中，建立 Visual C\# 或 Visual Basic **主控台應用程式** 專案。  在這個文件中，此專案的名稱為 `DataflowBatchDatabase`。  
  
2.  在您的專案中，加入 System.Data.SqlServerCe.dll 的參考和 System.Threading.Tasks.Dataflow.dll 的參考。  
  
3.  確定 Form1.cs \( [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中的 Form1.vb\) 包含下列 `using` \(在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中為`Imports` \) 陳述式。  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  加入下列資料成員至 `Program` 類別中：  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## 定義 Employee 類別  
 加入 `Employee` 類別至 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` 類別包含三個屬性： `EmployeeID`、`LastName` 和 `FirstName`。  這些屬性會對應至 Northwind 資料庫中，`Employees` 表格的 `Employee ID`、`Last Name` 和 `First Name` 欄位。  對於這個範例， `Employee` 類別也會定義 `Random` 方法，此方法建立的 `Employee` 物件，其屬性擁有隨機的值。  
  
<a name="operations"></a>   
## 定義 Employee 資料庫作業  
 加入 `InsertEmployees`、`GetEmployeeCount` 和 `GetEmployeeID` 方法至 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` 方法會將新員工記錄至資料庫。  `GetEmployeeCount` 方法會擷取 `Employees` 資料表中的項目數目。  `GetEmployeeID` 方法會擷取具有指定名稱的第一個員工的識別項。  每個方法會使用連接字串至 Northwind 資料庫，並使用 `System.Data.SqlServerCe` 命名空間中的功能與資料庫溝通。  
  
<a name="nonBuffering"></a>   
## 將 Employee 資料加至資料庫，而不使用緩衝區  
 加入 `AddEmployees` 和 `PostRandomEmployees` 方法至 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` 方法會使用資料流，加入隨機員工的資料至資料庫。  它會建立 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，此物件呼叫 `InsertEmployees` 方法將員工輸入到資料庫。  `AddEmployees` 方法接著會呼叫 `PostRandomEmployees` 方法，張貼多個 `Employee` 物件至 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。  `AddEmployees` 方法接著會等待所有插入作業完成。  
  
<a name="buffering"></a>   
## 使用緩衝區將 Employee 資料儲存至資料庫  
 將 `AddEmployeesBatched` 方法加入至 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 這個方法類似於 `AddEmployees`，不過，它也會使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別來緩衝多個 `Employee` 物件，然後再將這些物件傳送至 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。  由於 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別會將多個項目做為一個集合，因此 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件已被修改，以針對 `Employee` 物件的陣列進行操作。  如同在 `AddEmployees` 方法中， `AddEmployeesBatched` 會呼叫 `PostRandomEmployees` 方法以張貼多個 `Employee` 物件；不過， `AddEmployeesBatched` 會將這些物件張貼至 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件。  `AddEmployeesBatched`  方法接著也會等待所有插入作業完成。  
  
<a name="bufferedJoin"></a>   
## 使用緩衝區聯結讀取資料庫的 Employee 資料  
 將 `GetRandomEmployees` 方法加入至 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 這個方法會將有關隨機員工的資訊寫入主控台。  它會建立多個隨機 `Employee` 物件並呼叫 `GetEmployeeID` 方法來擷取每個物件的唯一識別項。  因為如果沒有具有指定的名稱相符的員工， `GetEmployeeID` 方法會擲回例外狀況，所以 `GetRandomEmployees` 方法使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 類別，對於 `GetEmployeeID` 物件的成功呼叫，儲存 `Employee` 物件；對於失敗的呼叫則儲存 <xref:System.Exception?displayProperty=fullName> 物件。  這個範例中的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件針對 <xref:System.Tuple%602> 物件進行處理（後者持有 `Employee` 物件清單及 <xref:System.Exception> 物件清單）。  在接收的 `Employee` 和 <xref:System.Exception> 物件的總和計數等於批次大小時， <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 物件會傳播這項資料。  
  
<a name="complete"></a>   
## 完整的範例  
 下列範例顯示完整程式碼。  `Main` 方法會比較執行批次資料庫與非批次資料庫兩者插入所需的時間。  它也示範使用緩衝區聯結，讀取資料庫的 Employees 資料與報告錯誤。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)